Delegate 패턴 간단한 연습
======

```swift
import UIKit

class ViewController: UIViewController, UITextFieldDelegate { 
// UITextFieldDelegate를 채택함

    @IBOutlet weak var textField: UITextField!
    @IBOutlet weak var label: UILabel!
    
    override func viewDidLoad() {
        super.viewDidLoad()
        textField.delegate = self // textField의 delegate는 self(스스로를 지칭) -> ViewController 클래스
    } // 대리자가 누구인지 알려주는 코드이다.
    
    func textFieldShouldReturn(_ textField: UITextField) -> Bool { 
        label.text = textField.text
        return true
    } // UITextFieldDelegate안에 있는 함수로써 우리가 하고 구현하고 싶은 일을 이 함수에게 맡기면 
    // 된다. 
}
```

기존에 버튼을 눌러서 텍스트필드와 레이블의 텍스트가 같아지게끔 했다면 대리자를 뷰컨트롤러로 설정함으로써 뷰컨트롤러가 해당 역할을 대신해서 할 수 있게     
되었다. 텍스트필드 값을 입력한 뒤에 엔터를 누르면 레이블에도 텍스트 값이 들어가게 된다.     

https://user-images.githubusercontent.com/99719661/207632451-6fe169eb-63bf-4974-bfe2-c52d0f4016b1.mp4

