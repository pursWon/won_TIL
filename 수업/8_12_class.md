8월 12일 수업 내용
===

```swift

import UIKit

/*
 함수와 함수 사이에는 한 줄 띈다.
 */

class ViewController: UIViewController {
    
    let colorList: [UIColor] = [.systemPurple, .cyan, .systemGreen, .systemRed, .systemYellow]
    
    // 변수나 상수
    // 네이밍: 변수나 상수에 대한 이름은 명사로 짓는다.
    @IBOutlet weak var contentLabel: UILabel!
    @IBOutlet weak var contentTextField: UITextField!
    
    // 화면에 필요한 초기값 데이터를 대입해줄 때 주로 사용
    override func viewDidLoad() {
        super.viewDidLoad()
        
        view.backgroundColor = .gray
        // backgroundColor : 배경색
        // tintColor : 글자색
    }
    
    // 액션
    // 네이밍: 액션에 대한 이름은 동사로 짓는다.
    @IBAction func sendButton(_ sender: UIButton) {
        print("초록 버튼 눌림")
        
        contentLabel.text = contentLabel.text
    }
    
    @IBAction func initializeButton(_ sender: UIButton) {
        print("빨간 버튼 눌림")
        
        contentTextField.text = ""
    }
    
    @IBAction func changeColorButton(_ sender: UIButton) {
        print("파란 버튼 눌림")
        
        // 버튼을 눌렀을때, colorList배열에서 랜덤으로 하나의 색깔을 가져와서, view의 배경색을 그 색깔로 바꿔주면 된다.
        let randomColor: UIColor? = colorList.randomElement()
        
        if let color = randomColor {
            view.backgroundColor = color
        }
    }
}

