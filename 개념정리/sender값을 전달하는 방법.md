버튼 sender의 currentTitle을 전달하는 방법
====

```swift
@IBAction func choiceButton(_ sender: UIButton) { // 버튼의 이벤트 함수

text(myWord: sender.currentTitle)

}

func text(myWord: String) {
if myWord == "True" {
print("true")
} else if == "False" {
print("false")
}

}


```

함수의 매개변수값을 통해 sender의 currentTitle 값을 전달할 수 있다.
