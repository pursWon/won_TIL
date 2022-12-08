Navigation Bar에 bar item을 코드로 추가하기 
====

viewDidLoad()에 코드 추가
```swift
navigationItem.rightBarButtonItem = UIBarButtonItem(title: "수정", style: .plain, target: self, action:
#selector(saveButton)) // selector안에 함수를 집어넣는다. 
navigationItem.rightBarButtonItem?.tintColor = .red // 버튼의 글자색을 빨강색으로 지정
```

saveButton 함수에 기능 작성 
```swift
@objc func saveButton() {
        let barItem = navigationItem.rightBarButtonItem! // 상수에 담아준다.
        var data = Book.BookData[index!]
        if barItem.title == "수정" {
            barItem.title = "저장"
            titleTextField.isEnabled = true
            descriptionTextField.isEditable = true
            navigationItem.hidesBackButton = true
        } else {
            let title = titleTextField.text?.components(separatedBy: " / ")
            data.coverImage = imageView.image
            data.introduction = descriptionTextField.text
            data.title = title![0]
            data.author = title![1]
            navigationController?.popViewController(animated: true)
        }
    }
```
