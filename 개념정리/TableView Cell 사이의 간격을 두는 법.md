TableView Cell 사이의 간격을 두는 법
===============================

![simulator_screenshot_4D299263-DEB1-452B-849A-A9979228C70A](https://github.com/pursWon/won_TIL/assets/99719661/607d98c5-1da2-4418-9aab-717cae8b94a8)

위의 그림과 같이 cell사이에 간격을 두고 싶다면,   

UITableViewCell 내의 함수인 layoutSubViews를 이용하면 된다.   

contentView의 UIEdgeInsets를 이용하여 값을 지정해주면 된다.   

```swift  

import UIKit

class MyCell: UITableViewCell {
    @IBOutlet weak var numberLabel: UILabel!
    
    override func layoutSubviews() {
        super.layoutSubviews()
        
        contentView.layer.borderWidth = 2
        contentView.layer.borderColor = UIColor.blue.cgColor
        contentView.layer.cornerRadius = 10
        
        contentView.frame = contentView.frame.inset(by: UIEdgeInsets(top: 0, left: 30, bottom: 18, right: 30))
    }
}

```


