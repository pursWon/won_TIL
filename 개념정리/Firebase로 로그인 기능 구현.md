Firebase로 로그인 기능 구현
=======================

Firebase의 Authentication로 회원가입과 로그인 기능을 쉽게 구현할 수 있다.   

</br>

![ㅇㅇ](https://github.com/pursWon/won_TIL/assets/99719661/3f6bd01b-7e6d-43e0-b451-b60836d7c032)

</br>

Sign - in method에서 이메일 / 비밀번호를 선택

</br>

![ㅇㅇㅇ](https://github.com/pursWon/won_TIL/assets/99719661/c7e18104-d832-4b40-af73-35f613fb042e)

</br>

![ㅇㅇㅇㅇ](https://github.com/pursWon/won_TIL/assets/99719661/61b1abef-2491-4f8f-93a4-ff8cc057849f)

</br>

새 제공업체 추가 버튼을 누르게 되면 소셜 기능을 추가할 수 있고,   

오른쪽 연필 버튼을 누르면 비밀번호가 없는 로그인 설정도 다시 해줄 수 있다.    

![ㅇㅇㅇㅇㅇ](https://github.com/pursWon/won_TIL/assets/99719661/38922935-9d1c-40f7-92c3-848da5dae508)

Users 탭에서는 Auth 기능을 통해 가입한 사용자들을 확인할 수 있다.       

그리고 사용자 추가버튼을 통하여 로그인할 수 있는 회원을 추가할 수 있다.     

Firebase Console에서의 설정은 끝났으므로 Xcode로 가서 설정해주면 된다.     

</br>

![444](https://github.com/pursWon/won_TIL/assets/99719661/a93dc6dc-d915-4bfb-af1c-e6670a1fda76)

</br>

Xcode 내에서 FirebaseAuth를 import 해준다.    

</br>

![55555](https://github.com/pursWon/won_TIL/assets/99719661/76a1726a-b763-49c8-98dd-7fe2d2df834d)

</br>

사용자 추가 버튼을 눌러서 테스트 유저를 추가했다.   

추가되는 사용자들은 사용자 UID라는 고유한 값을 가지게 된다.   

</br>

<img src="https://github.com/pursWon/won_TIL/assets/99719661/d916ffc5-ac27-44a6-a614-b2a54beb0c37.png" width="200" height="400"/>

</br>

만든 로그인 화면은 위와 같다.    

그리고 화면 내의 코드는 다음과 같다.   

```swift

import UIKit
import FirebaseAuth

class LoginViewController: UIViewController {
    @IBOutlet weak var idTextField: UITextField!
    @IBOutlet weak var passWordTextField: UITextField!
    @IBOutlet weak var loginButton: UIButton!
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
    }
    
    @IBAction func loginButtonAction(_ sender: UIButton) {
        guard let email: String = idTextField.text?.description else { return }
        guard let passWord: String = passWordTextField.text?.description else { return }
        
        Auth.auth().signIn(withEmail: email, password: passWord) { authResult, error in
            if authResult != nil {
                print("로그인 성공")
            } else {
                print("로그인 실패")
                print(error.debugDescription)
            }
        }
    }
}

```

FirebaseAuth 패키지를 추가하고 나면 Auth 클래스를 사용할 수 있다.   

Auth.auth().signIn(withEmail: email, password: passWord)를 구현하기 위해서는 두 개의 파라미터 값을 입력해야 한다.    

첫번째 파라미터인 authResult가 nil이 아닐 경우, 성공.   

nil일 경우에는 실패하고 실패한 이유를 출력하게 된다.    

</br>

**로그인 실행 결과**

![스크린샷 2023-08-18 오전 9 16 18](https://github.com/pursWon/won_TIL/assets/99719661/7b534bc7-fb8a-44f3-9929-942dc72e3f2d)

</br>

이메일과 패스워드를 받는 텍스트 필드에 각각 입력후에 Login 버튼을 누르게 되면 작성한 코드가 실행된다!    

- 로그인 실패했을 때

</br>

![스크린샷 2023-08-18 오전 9 17 00](https://github.com/pursWon/won_TIL/assets/99719661/e6cd34ac-ca80-4c23-80d5-381dac14b133)

</br>

- 로그인 성공했을 때

</br>

![777](https://github.com/pursWon/won_TIL/assets/99719661/ece3fb6f-12ae-4129-a750-80dae8bcd759)


