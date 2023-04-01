didSet과 willSet에 대하여
==========

Swift는 프로퍼티의 옵저버로 didSet과 willSet을 제공한다. 

하나의 프로퍼티에 대해서 다음 옵저버를 정의할 수 있다. 

**willSet** : 값이 저장되기 직전에 호출된다.

**didSet** : 값이 저장된 후에 호출된다. 

```swift
import Foundation

var oldNumber: Int = 0
var newNumber: Int = 0

var myNumber: Int = 30 {
    didSet(oldNumber) {
        print(oldNumber) // 30
    }
    
    willSet(newNumber) {
        print(newNumber) // 40 
    }
}

myNumber = 40
```

이전 프로퍼티의 값은 didSet안의 oldNumber로 제공된다.

새로운 프로퍼티의 값은 willSet안의 newNumber로 제공된다. 

프로퍼티 옵저버의 가장 빈번한 사용은 Model에서 갱신된 값을 View에서 보여줄 때이다. 

```swift
import Foundation

var oldNumber: Int = 0
var newNumber: Int = 0

var myNumber: Int = 30 {
    didSet(oldNumber) {
        print("전 점수 : \(oldNumber), 현재 점수 : \(myNumber)") // 전 점수 : 30, 현재 점수 : 40
    }
    
    willSet(newNumber) {
        print(newNumber)
    }
}

myNumber = 40 // 40
```

전 값과 현재의 값을 구분할 수 있다. 

```swift
import Foundation

class StepCounter {
    var totalSteps: Int = 0 {
        willSet(newTotalSteps) {
            print("About to set totalSteps to \(newTotalSteps)")
        }
        didSet {
            if totalSteps > oldValue  {
                print("Added \(totalSteps - oldValue) steps")
            }
        }
    }
}

let stepCounter = StepCounter()

stepCounter.totalSteps = 130
// About to set totalSteps to 130
// Added 130 steps

stepCounter.totalSteps = 200
// About to set totalSteps to 200
// Added 70 steps
```

totalStep 은 저장 프로퍼티이다. 

위 예시는 totalStep 에 willSet, didSet 옵저버를 추가한다.

totalSteps에 값을 추가하면, 값이 저장되기 직전인 willSet이 먼저 호출되고, 후에 didSet이 호출된다.

기존의 값은 0이고 새로 추가된 값은 130이므로 130 - 0 = 130 

didSet을 호출하면 130이 프린트된다. 

후에 totalSteps을 추가로 200을 집어넣으면, willSet이 호출되어서 200이 totalSteps에 들어간다. 

didSet을 호출하게 되면 기존의 값은 130이고 if문(200 > 130)을 충족하므로 200 - 130 = 70이 

프린트 된다.
