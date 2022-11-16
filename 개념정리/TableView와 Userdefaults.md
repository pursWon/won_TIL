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

self.itemArray.append(textField.text!) → 배열에 문장을 추가해준다. 화면에 문장을 추가한다.     

self.tableView.reloadData() → 테이블뷰의 행의 데이터를 가져온다.      

alertTextField.placeholder = “Create new item”.    

→ 문장을 입력하지 않았을 때, 이와 같은 문장이 나온다.    

## UserDefaults












