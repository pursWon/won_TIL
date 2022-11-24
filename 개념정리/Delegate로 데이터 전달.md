Delegate로 데이터 전달
=====

### Protocol?

protocol은 특정한 작업이나 기능 부분적인 부분에 적합한 메소드, 프로퍼티 그리고 다른 요구사항의 청사진을 의미합니다.      

그런 다음 프로토콜을 클래스, 구조체, 열거형에서 채택하여 해당 요구사항의 실제 구현을 제공할 수 있다.    

즉 프로토콜에서는 해야할일만 정의하고, 구현은 프로토콜을 채택한 객체에서 이루어진다.   

### Delegate Pattern?

Delegate Pattern은 쉽게 말해서 객체지향 프로그래밍에서 하나의 객체가 모든 일을 처리하는 것이 아니라 처리 해야 하는 일 중 일부를 다른 객체에 넘기는것.    

주로 프레임워크 객체가 위임을 요청하며, 커스텀 컨트롤러 객체가 위임을 받아 특정 이벤트에 대한 기능을 구현.     
 
### Delegate로 데이터 전달을 하는 경우 !

1. 다음 화면 -> 이전 화면으로 (나중에 메모리에 올리는 객체) -> (먼저 메모리에 올라와있는 VC)

2. 이미 메모리에 올라와 있는 상태에서 데이터 전달할 때 사용되는 방식.   

예를 들어,    

(1) A —present—> B, A 뷰컨을 밑에 깔고 B라는 뷰컨을 present한 상황에서 B에서 A로 데이터 전달을 하고 싶을 때 사용합니다!    

(2) A라는 뷰컨위에 TableViewCell, CollectionViewCell같은거를 얹을 때, TVC,CVC를 쥐고 있는 상위 VC한테 데이터 전달을 할 때 사용합니다.    

**주의할점은 XX.delegate = self로 대리자 선언해주는거 잊으면 안된다!**

<예시>   

1. Second VC 먼저 작성 - Protocol 작성    

```swift
import UIKit

//1. 데이터를 넘기는 함수 원형만 적고, 구현부는 FirstVC에서 진행

protocol SampleProtocol {
  func dataSend(data: String)
}


class SecondVC: UIViewController {

  @IBOutlet weak var dataTextField: UITextField!
  
  //2. SampleProtocol형의 delegate 프로퍼티 생성
  var delegate : SampleProtocol?
  
  override func viewDidLoad() {
        super.viewDidLoad()
    }
    
  @IBAction func dataSendBtnClicked(_ sender: Any) {
    //3. 버튼을 눌렀을 때, 선언한 delegate의 dataSend에 textField의 텍스트를 담아주세요!
    if let text = dataTextField.text{
      delegate?.dataSend(data: text)
    }
    
    //4. delegate 처리가 끝난 뒤에, navigation pop처리
    self.navigationController?.popViewController(animated: true)
  }
  
}
```

2. FirstVC에서 protocoel 채택   

```swift

import UIKit

//1. SampleProtocol 채택
class FirstVC: UIViewController, SampleProtocol {
  
  @IBOutlet weak var dataLabel: UILabel!
  
  override func viewDidLoad() {
    super.viewDidLoad()
  }

  //2. protocol의 구현부 작성
  func dataSend(data: String) {
    dataLabel.text = data
  }
  
  @IBAction func nextBtnClicked(_ sender: Any) {
    guard let nextVC = self.storyboard?.instantiateViewController(withIdentifier: "SecondVC") as? SecondVC else {return}
    
    //3. SecondVC에서 선언해둔 delegate가 self. 즉 대신해서 처리할 부분이 FirstVC라는 것을 아래의 구문을 통해 선언
    nextVC.delegate = self
    
    self.navigationController?.pushViewController(nextVC, animated: true)
  }
}








