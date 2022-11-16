TableView와 Userdefaults
===

## TableView

<img width="661" alt="스크린샷 2022-11-16 오후 11 10 31" src="https://user-images.githubusercontent.com/99719661/202244161-f7d953e0-a2ac-4b74-8594-6890f4ba14b5.png">

위와 같이 tableView를 검색하여 가져올 수 있다. 

<img width="262" alt="스크린샷 2022-11-16 오후 11 12 05" src="https://user-images.githubusercontent.com/99719661/202244362-395b3513-373a-4d68-985e-b06f45dc2aef.png">ㅇ

이런 식으로 테이블뷰를 가져오게 되면, dataSource와 delegate를 따로 설정해 줄 필요가 없다. 이미 연결되어있기 때문이다.    

셀에 체크마크를 넣는 법 ! →   
<img width="251" alt="스크린샷 2022-11-16 오후 11 18 33" src="https://user-images.githubusercontent.com/99719661/202244580-f7f05d92-ab7f-44ee-839f-1685ee8910a4.png">

Accessory에 Checkmark를 설정한다.    

하지만, 이렇게 설정만해주면 셀을 눌렀을 때 체크마크가 그대로 있고 없어지지 않는다.     

https://user-images.githubusercontent.com/99719661/202244775-151242c6-c464-43e9-959a-a88295f70329.mov

```swift

override func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
        if tableView.cellForRow(at: indexPath)?.accessoryType == .checkmark {
            tableView.cellForRow(at: indexPath)?.accessoryType = .none
        } else {
            tableView.cellForRow(at: indexPath)?.accessoryType = .checkmark
        }
        tableView.deselectRow(at: indexPath, animated: true)
    }

```
→ checkmark가 있을 경우에, none 상태가 되고 아닐 경우에(else) checkmark가 된다.    

<Add 버튼을 눌렀을 때, 알람 화면이 뜨게 하기>  

<img width="1440" alt="스크린샷 2022-11-17 오전 12 33 21" src="https://user-images.githubusercontent.com/99719661/202245015-51dc7abc-6659-4233-ba3c-249e94845c10.png">

UIAlertController로 알람 화면을 그려준다. → title : “Add New Item Today”, message: “”, preferredStyle: .alert.    

Action으로 알람의 action을 설정해준다.    
```swift
self.itemArray.append(textField.text!) → 배열에 문장을 추가해준다. 화면에 문장을 추가한다.     

self.tableView.reloadData() → 테이블뷰의 행의 데이터를 가져온다.      

alertTextField.placeholder = “Create new item”.    
```
→ 문장을 입력하지 않았을 때, 이와 같은 문장이 나온다.    

## UserDefaults

userDefaults란?    

: 앱 실행 시에 키, 값을 저장하는 default의 데이터 베이스이다.   

이를 사용하려면, 새로운 객체를 만들어 줘야한다.   

```swift

let defaults = UserDefaults.standard
```

UserDefaults를 설정하고 표준 UserDefaults를 설정해준다.      

itemArray 배열에 항목을 추가해주고 업데이트된 배열을 UserDefaults에 저장해줘야 한다.     

그리고 default 값을 설정해줘야 한다.     

```swift

self.defaults.set(self.itemArray, forKey: "TodoListArray")

```

UserDefaults에서 itemArray 배열을 식별해주려면 key 값이 필요하다.     

그래서 key값을 "TodoListArray"으로 설정해준다.     

그리고 closure 안에 설정해주는것이기 때문에 앞에 self를 무조건 붙여야한다.         

UserDefaults 데이터를 보려면 앱이 실행되는 샌드박스의 파일 경로를 가져와야 하고, 시뮬레이터의 ID를 가져와야 한다.      

```swift

class AppDelegate: UIResponder, UIApplicationDelegate {

    var window: UIWindow?
    
    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
        
        print(NSSearchPathForDirectoriesInDomains(.documentDirectory, .userDomainMask, true).last! as String)
        
        return true
    }
```

→ UserDefaults의 경로를 출력하기 위해서 AppDelegate에 다음과 같이 입력한다.    

경로를 따라서 plist 파일을 찾은 다음 새로운 항목을 추가했을 때, plist에 파일이 추가되지만 화면에는 추가되지 않는 이유는.    

itemArray와 UserDefaults에 TodoListArray 키값을 가진 배열과 동일시 시켜주지 않았기 때문이다.       

따라서, 다음과 같이 코드를 입력해준다.      

```swift

override func viewDidLoad() {
        super.viewDidLoad()
        
        if let items = defaults.array(forKey: "TodoListArray") as? [String] {
            itemArray = items
        }
    }
```

UserDefaults에 배열을 문자로 바꾼다. 다만 값이 nil일 가능성이 있으므로 if let을 사용한다.     

그래서 값이 존재할 경우, itemArray와 items의 값을 같게 해준다.      

이렇게 설정해주면, plist와 화면의 보기상에서도 추가가 되고 앱을 껐다가 다시 켜도 그대로 항목이 남아있다.       

```swift

import Foundation

let defaults = UserDefaults.standard

defaults.set(0.24, forKey: "Volume")
defaults.set(Date(), forKey: "date")
defaults.set([100, 187], forKey: "array")


let volume = defaults.float(forKey: "Volume")
print(volume)

let myDate = defaults.object(forKey: "date")
print(myDate!)

let numberArray = defaults.array(forKey: "array")
```

UserDefault에 다음과 같이 값을 저장하면 이와 같은 값을 볼 수 있는 키가 존재한다.       

UserDefault가 저장할 수 있는 서납장이면 서납장 안에 있는 내용물은 0.24나 Date()가 되는 것이며, 각 서납장마다 열 수 있는 열쇠가 다 다른 것이다.     

이렇게 UserDefault는 어렵지 않은 방법으로 자료를 저장하고 상수를 통해 검색하여 값에 자료에 접근할 수 있지만 조심해야 할 점이 존재한다.       

작은 데이터를 저장하고 사용하는데에 유용하지만 크나는 데이터를 저장하기에는 UserDefault가 데이터 베이스가 아니므로 마땅치 않다는 점을 유의해야 한다.     



