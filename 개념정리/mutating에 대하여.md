mutating에 대하여
===

값 타입인 구조체에서는 인스턴스 메소드 내에서 프로퍼티들을 수정할 수 없게 되어 있다.   
따라서 이러한 프로퍼티들을 구조체 안의 메소드에서 수정을 해주기 위해 mutating이라는 키워드를 사용하게 된다.   

**mutating :** 
특정 메소드 내에서 구조체 또는 열거형의 프로퍼티를 수정해야 하는 경우, 해당 메소드의 동작을 변경하도록 하는 것.  

```swift
import Foundation

struct Calculate {
    
    var myScore: Int // 구조체 Calculate의 프로퍼티 myScore
    
    init(myScore: Int) { // myScore를 초기화한다
        self.myScore = myScore
    }
    
    mutating func change()  { // mutating을 붙이지 않는다면 오류가 생길 것이다. 해당 메소드의 프로퍼티를 수정하려면 mutating을 붙여야한다. 
        myScore = 120 
    }
}

var number: Calculate = Calculate(myScore: 100) // 프로퍼티 myScore의 값을 100으로 정하였다.
number.change() // 구조체내의 메소드인 change 메소드를 사용하였다. 
print(number.myScore) // 120

```
