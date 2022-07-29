7.29 공부기록 
===

구조체와 클래스에 대하여 직접 코드를 짜보고 복습 ! 
--- 

Struct (구조체)
---

```swift
import Foundation

struct Person { // 구조체 선언
    var name: String // 프로퍼티들을 선언 
    var age: Int
    let gender: String
}

let 민수: Person = Person(name: "민수", age: 17, gender: "남자") // 민수 상수가 구조체 Person을 받음
var 궤도민수 = 민수 // 민수를 복사하였는데 변수로 정하고 이름을 궤도민수로 함 

궤도민수.name = "궤도민수" // 복사된 개체의 이름을 궤도민수라고 함 
궤도민수.age = 40 // 복사된 개체의 age 값을 점문법을 통해 40이라고 정함

print(민수) // Person(name: "민수", age: 17, gender: "남자")
print(궤도민수) // Person(name: "궤도민수", age: 40, gender: "남자")

// 구조체는 복사가 되므로 복사된 구조체가 name과 age를 변경하여도 기존의 구조체는 영향을 받지 않으므로 변화가 없다.
```

Class (클래스)
---

```swift
class PersonClass { // 클래스 PersonClass를 선언
    var name: String
    var age: Int
    let gender: String

    init(name1: String, age1: Int, gender1: String) { // 이니셜라이저, 초기값을 가져야하므로 init으로 초기화해준다.
        self.name = name1 // name1이 name을 받는다.
        self.age = age1 // age1이 age를 받는다.
        self.gender = gender1 // gender1이 gender를 받는다. 
    }
}

let 영희: PersonClass = PersonClass(name1: "김영희", age1: 20, gender1: "여자") // PersonClass의 객체를 만들어준다.

print(영희.name) // 김영희

let 복제영희 = 영희 // 상수 복제영희가 영희를 참조함.

복제영희.name = "제갈영희" // 복제영희의 name 프로퍼티를 "제갈영희"로 변경
복제영희.age = 16 // 복제영희의 age 프로퍼티를 16으로 변경

print(영희.name) // 제갈영희
print(영희.age) // 16
print("\(영희.age)는 중학교 3학년이다.")

// 복제영희는 영희를 참조하고 있다. 이는 값이 지정되어 있는 메모리 공간의 주소값이 같다는 의미이다. 따라서, 복제영희의 값이 변경되면
// 영희도 영향을 받아서 값이 같은 값으로 변경되게 된다.
```















