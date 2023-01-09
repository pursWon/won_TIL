Protocol에서의 프로퍼티, 메서드 선언 이해하기
==============

프로토콜에서 프로퍼티를 선언한다. 프로토콜에서 프로퍼티를 선언할 때와 프로토콜을 받는 에는 규칙이 존재한다. 

1. **protocol 내의 프로퍼티는 무조건 변수로 선언해야만 한다.** 

```swift
protocol Band {
    var guitar: String { get }
    var piano: String { get }
    var vocal: String { get }
    var drum: String { get }
}
```

2.  **protocol을 채택하여 구현할 때, { get } 을 사용**

**저장 프로퍼티**의 경우 let / var 모두 가능 

**연산 프로퍼티**의 경우 var로만 가능, get만 설정해줘도 되고 get & set 모두 설정해줘도 됨

```swift

protocol Band {
    var guitar: String { get }
    var piano: String { get }
    var vocal: String { get }
    var drum: String { get }
}

struct myBand: Band {
let guitar: String = "A군" // 저장 프로퍼티는 let 가능
    var piano: String { // 연산 프로퍼티는 var만 가능 
        get {
        return "B양"
        } 
    }

var vocal: String = "C군" // 저장 프로퍼티는 var 가능
let drum: String = "D양"
}
```

3. **protocol을 채택하여 구현할 때, { get  set } 을 사용**

**저장 프로퍼티**의 경우 var로만 가능

**연산 프로퍼티**의 경우 var로만 가능, get & set 모두 설정해줘야만 함

```swift
import Foundation

protocol Band {
    var guitar: String { get set }
    var piano: String { get set}
    var vocal: String { get set }
    var drum: String { get set }
}

struct myBand: Band {
var guitar: String = "A군"
    var piano: String {
        get {
        return "B양"
        } set {
        print("???")
        }
    }
    
var vocal: String = "C군"
var drum: String = "D양"
}
```

4. **protocol에 메서드를 선언한 경우**

함수의 헤더부분만 protocol에 선언해주고 바디 부분은 해당 protocol을 채택한 곳에서 직접 구현하면 된다. 

```swift
protocol Band {
    var guitar: String { get set }
    var piano: String { get set}
    var vocal: String { get set }
    var drum: String { get set }
    
    func play() // 함수의 헤더 부분 
}

struct myBand: Band {
var guitar: String = "A군"
    var piano: String {
        get {
        return "B양"
        } set {
        print("???")
        }
    }
    
var vocal: String = "C군"
var drum: String = "D양"
    
    func play() { // 함수의 바디 부분
    print("연주를 시작해보자")
    }
}
```
