viewDidLoad에 대하여
============

**viewDidLoad**는 ViewController가 메모리에 로드되고 나서 호출이 된다.     

시스템에 의해 자동으로 호출이 되므로 리소스를 초기화하는 용도로 사용이 되고,      

화면이 처음 나타날 때, 한 번만 호출이 되므로 화면을 초기화하는 코드를 이곳에 적으면 된다.    

```swift 

override func viewDidLoad() {
        super.viewDidLoad()
        view.backgroundColor = .blue
        
    }

```

-> 화면이 처음 나타날 때에 view 배경색을 파랑색으로 지정해줬다.
