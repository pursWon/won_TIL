Retain Cycle에 대하여
=================

순환 참조(Retain Cycle)는 두 인스턴스끼리 강한 참조를 할 때에 발생하게 됩니다.

순환 참조가 발생하게 되면 Reference Count가 0이 되지 못해서 메모리 누수가 발생하게 됩니다.

예를 들면, 각각 다른 두 개의 클래스를 참조하고 있는 인스턴스가 있고,

두 개의 인스턴스끼리 서로 상호참조 하고 있다고 하면, 

두개의 인스턴스를 nil로 설정해도 인스턴스의 프로퍼티끼리의 강한 참조는 유지되므로 

Reference Count가 1이 됨에 따라 메모리 누수가 발생하게 됩니다.

< 예시 코드 >

```swift 

import Foundation

class Person {
    var name: String
    var myCar: Car?
    
    init(name: String) {
        self.name = name
    }
    
    deinit { print("Deinit!") }
      // deinit은 인스턴스가 메모리에서 해제될 때 실행되는 메서드
}

class Car {
    var name: String
    var host: Person?
    
    init(name: String) {
        self.name = name
    }
    
    deinit { print("Deinit!") }
}

var minsu: Person? = Person(name: "민수")
var sonata: Car? = Car(name: "쏘나타")

minsu!.myCar = sonata
sonata!.host = minsu

minsu = nil 
sonata = nil

```
