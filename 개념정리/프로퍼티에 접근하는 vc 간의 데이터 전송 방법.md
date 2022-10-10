프로퍼티에 접근하는 vc 간의 데이터 전송 방법
===

첫번째 뷰 컨트롤러(데이터를 전송하는 뷰 컨트롤러)를 Green ViewController라 하고, 두번째 뷰 컨트롤러(데이터를 받는 뷰 컨트롤러)를 Blue ViewController라 할 것이다.   

### (1) Green VC

```swift
import UIKit

class GreenViewController: UIViewController{

    @IBOutlet weak var sendButton: UIButton!
    
    override func viewDidLoad() {
        super.viewDidLoad()
    }
    
    @IBAction func sendData(_ sender: Any) {
        guard let vc = self.storyboard?.instantiateViewController(identifier: "BlueViewController") as? BlueViewController else {
            return
        }
        
        vc.data = "hello blue"
        self.navigationController?.pushViewController(vc, animated: true)
    }
}
```

이 때에, Green VC에서 Blue VC의 프로퍼티인 data에 직접 접근하여 String 값인 "hello blue"를 건네준다.   

### (2) Blue VC

```swift
import UIKit

class BlueViewController: UIViewController {
    
    @IBOutlet weak var dataLabel: UILabel!
    var data : String = ""

    override func viewDidLoad() {
        super.viewDidLoad()
        
        self.dataLabel.text = data
    }
}
```

Blue VC는 String 값을 받아서 dataLabel에 넣어준다. 값을 넣어줄 때에는 viewDidLoad를 이용한다.   
