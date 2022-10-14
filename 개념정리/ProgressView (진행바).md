ProgressView (진행바)
===

ViewController에서 ProgressView를 객체로 따로 생성해준다.   

```swift
@IBOutlet weak var progressView: UIProgressView!
````

해당 버튼의 액션을 실행하면 (버튼을 누르면) ProgressView의 진행률이 0.0으로 초기화 된다.

```swift
@IBAction func HardnessSelected(_ sender: UIButton) {
        
        timer.invalidate()
        
        let hardNess = sender.currentTitle!
        totalTime = eggTime[hardNess]!
        
        progressView.progress = 0.0 // 해당 코드는 진행바의 진행률을 나타낸다.
        secondPassed = 0
        titleLabel.text = hardNess
        
        timer = Timer.scheduledTimer(timeInterval: 1.0, target: self, selector: #selector(updateTimer), userInfo: nil, repeats: true)
    }
````

ProgressView의 진행률은 백분율이므로 현재 진행된 진행률을 전체 진행률로 나눈 값이다. 

**ProgressView의 진행률 = 현재 진행된 진행률 / 전체 진행률 (백분율)**

```swift
let percentageProgress: Float = Float(secondPassed) / Float(totalTime)
            print(Float(secondPassed) / Float(totalTime))
            progressView.progress = percentageProgress // 나눈 값을 progressView의 값으로 넣어준다.
````

secondPassed = 현재 진행된 진행률(초단위의 시간)   

totalTime = 전체 진행된 진행률(초단위의 시간)  


여기서 잠깐 ! 
secondPassed를 totalTime으로 나눌 때, 왜 각각의 값에 Float을 붙여야 하는가?   

```swift
let a: Int = 22
let b: Int = 4

let c: Float = Float(a / b)
print(c) // 5
````

각각의 값에 Float을 붙이지 않고 나눈 값에만 Float을 붙일 경우, 제대로 된 값이 5.5가 나오지 않고 5가 나오게 된다. 반면에, 각가의 값에 Float를 붙이게 되면,    

```swift
let a: Int = 22
let b: Int = 4

let c: Float = Float(a) / Float(b)
print(c) // 5.5
````
5.5가 나오게 된다. 따라서 진행률도 마찬가지다.     
전체 진행률은 소수점을 가지는 Float  타입의 값을 가질텐데 이를 딱 맞아떨어지게끔 값이 나온다면 프로그레스바도 정상적으로 채워지지 못할 것이다.    
