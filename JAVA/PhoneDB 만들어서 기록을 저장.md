PhoneDB 만들어서 기록을 저장
================================================================

</br>

**class**를 먼저 형성

```java

public class PersonInform {
	public String name;
	public String phoneNum;
	public String companyNum;
	
	public PersonInform(String name, String phoneNum, String companyNum) {
		this.name = name;
		this.phoneNum = phoneNum;
		this.companyNum = companyNum;
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public String getPhoneNum() {
		return phoneNum;
	}

	public void setPhoneNum(String phoneNum) {
		this.phoneNum = phoneNum;
	}

	public String getCompanyNum() {
		return companyNum;
	}

	public void setCompanyNum(String companyNum) {
		this.companyNum = companyNum;
	}
}

```

</br>
</br>

데이터를 관리해주는 class와 함수를 형성

```java

public class PhoneManager {
	Scanner sc = new Scanner(System.in);
	String temp = null;
	List<PersonInform> pList = new ArrayList<PersonInform>();

	public void getList() {
		System.out.println("사람의 정보를 입력해주세요.");
		System.out.println("---------------------------");

		System.out.print("이름 :");
		String name = sc.next();
		System.out.print("전화번호 :");
		String phoneNum = sc.next();
		System.out.print("회사번호 :");
		String companyNum = sc.next();

		System.out.println("입력이 완료되었습니다.");
		System.out.println("---------------------------");

		PersonInform inform = new PersonInform(name, phoneNum, companyNum);
		pList.add(inform);

		try {
			Writer fw = new FileWriter("C:\\Users\\User\\eclipse-workspace\\Goods\\src\\calculate\\PhoneDB.txt");
			BufferedWriter bw = new BufferedWriter(fw);

			for (PersonInform value : pList) {
				PersonInform newInform = new PersonInform(value.name, value.phoneNum, value.companyNum);
				temp = "" + newInform.getName() + ", " + inform.getPhoneNum() + ", " + inform.getCompanyNum() + "";
				bw.write(temp);
				bw.newLine();
			}

			bw.flush();
			bw.close();
		} catch (IOException e) {
			e.printStackTrace();
			System.out.println("다시 입력해주세요.");
		}
	}

	public void removeInform() {
		System.out.println("삭제하고 싶은 사람의 이름을 입력해주세요.");
		System.out.println("---------------------------");

		System.out.print("이름 :");
		String name = sc.next();

		pList.removeIf(n -> (n.name.equals(name)));
		System.out.println(""+name+"이 삭제되었습니다.");

		try {
			Writer fw = new FileWriter("C:\\Users\\User\\eclipse-workspace\\Goods\\src\\calculate\\PhoneDB.txt");
			BufferedWriter bw = new BufferedWriter(fw);

			for (PersonInform value : pList) {
				PersonInform inform = new PersonInform(value.name, value.phoneNum, value.companyNum);
				temp = "" + inform.getName() + ", " + inform.getPhoneNum() + ", " + inform.getCompanyNum() + "";
				bw.write(temp);
				bw.newLine();
			}

			bw.flush();
			bw.close();
		} catch (IOException e) {
			e.printStackTrace();
		}
	}

	public void searchInform() {
		System.out.println("검색하고 싶은 사람의 이름을 입력해주세요.");
		int falseCount = 0;
		String searchName = sc.next();
		
		for (int i = 0; i < pList.size(); i++) {
			String name = pList.get(i).getName();

			if (name.contains(searchName)) {
				System.out.println(""+searchName+"은 리스트안에 있습니다.");
			} else {
				falseCount ++;

				if (falseCount == pList.size()) {
					System.out.println("검색한 내용은 리스트안에 없습니다.");
				}
			}
		}
	}

	public void saveInform() {
		try (BufferedReader reader = new BufferedReader(new FileReader("C:\\Users\\User\\eclipse-workspace\\Goods\\src\\calculate\\PhoneDB.txt"))) {
			String line;

			while ((line = reader.readLine()) != null) {
				String [] arr = line.toString().split(", ");
				PersonInform inform = new PersonInform(arr[0], arr[1], arr[2]);
				pList.add(inform);
			}
		} catch (IOException e) {
			e.printStackTrace();
		}
	}

	public void showInfo() {
		System.out.println("파일내의 모든 정보를 보여드립니다.");
		String str;

		try (BufferedReader reader = new BufferedReader(new FileReader("C:\\Users\\User\\eclipse-workspace\\Goods\\src\\calculate\\PhoneDB.txt"))) {
			while ((str = reader.readLine())!= null) {
				System.out.println(str);
			}
		} catch (IOException e) {
			e.printStackTrace();
		}
	}

	public void allDelete() {
		pList.clear();
		System.out.println("모든 정보를 삭제하였습니다..");
		
		try {
			Writer fw = new FileWriter("C:\\Users\\User\\eclipse-workspace\\Goods\\src\\calculate\\PhoneDB.txt");
			BufferedWriter bw = new BufferedWriter(fw);
			
			bw.write("");	
			bw.flush();
			bw.close();
		} catch (IOException e) {
			e.printStackTrace();
		}
	}
}
```

</br>
</br>

데이터를 보여주고 실행시키는 class를 형성

```java

public class PhoneApp {
	public static void main(String[] args) {
		PhoneManager manager = new PhoneManager();
		boolean status = true;
		Scanner sc = new Scanner(System.in);
		manager.saveInform();

		while (status) {
			System.out.println("프로그램 종료를 원하시면 0번, 폰에 정보를 입력하고 싶으면 1번, 정보를 삭제하고 싶으면 2번, 정보를 검색하고 싶으면 3번, 모든 정보를 보고 싶으면 4번, 모든 정보를 삭제하고 싶으면 5번을 눌러주세요.");
			System.out.println("----------------------------");

			String insert = sc.next();

			switch (insert) {
			case "0":
				System.out.println("프로그램을 종료합니다...");
				return;
			case "1":
				manager.getList();
				break;
			case "2":
				manager.removeInform();
				break;
			case "3":
				manager.searchInform();
				break;
			case "4":
				manager.showInfo();
				break;
			case "5":
				manager.allDelete();
				break;
			default:
				System.out.println("다시 입력해주세요.");
				break;
			}			
		}
		
		sc.close();
	}
}
```

