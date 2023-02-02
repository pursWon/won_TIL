Class와 Struct의 차이에 대해 설명해주세요
==================

첫째, Class는 참조 타입이고, Struct는 값 타입입니다.     

Class 객체를 할당한 변수의 값을 변경시키면 참조된 객체의 값이 변경되고,     

구조체는 값 타입이므로 같은 구조체 객체를 할당하면 매번 새로운 메모리가 할당되어 값을 변경하더라도 다른 구조체 변수에는 영향을 주지 않습니다.      

둘째, Class의 참조 타입 객체는 **Heap**에 할당됩니다.      

Heap은 하나의 명령어로 할당, 해제가 이루어지지 않고 Heap은 참조가 어디서 어떻게 될지 모르기 때문에 Stack보다 관리가 복잡합니다.     

반면에, Struct의 객체는 컴파일 단계에서 언제 생기고 사라지는지 알기 때문에 Stack에 할당하게 됩니다.     

**Stack**은 LIFO(Last In First Out)으로 가장 마지막에 들어간 객체가 가장 먼저 나오게 되는 형태의 자료구조입니다.                               

셋째, 클래스는 상속이 가능하지만, 구조체는 상속이 불가능합니다. 상속은 오직 클래스만 가능하며, 단일 상속만 가능합니다.      

구조체는 연관된 값을 참조하는 것보다 복사하고 독립된 개체로 만들고 싶을 때 사용합니다.       

```swift

import Foundation

struct People {
    let name: String
    var age: Int
}

let man: People = People(name: "김길동", age: 25)
var woman: People = People(name: "김옥순", age: 21)

woman.age = 24

```

사람은 각각 다른 나이와 이름을 가지고 있습니다.     

이런 독립된 특성을 가질 수 있게 만든다면 구조체를 사용하여 구조체의 프로퍼티를 name과 age로 만들어주면 됩니다.     

상수를 사용한다면 인스턴스 내부의 프로퍼티는 변경이 불가능하나 변수를 사용한다면 인스턴스 내부의 프로퍼티를 변경할 수 있습니다.   

```swift

class House {
    var 집: String = "사는 지역명"
}

let kim: House = House()

kim.집 = "대전" 

let lee: House = kim

let jung: House = lee

let hong: House = jung

print(kim.집) // 대전
print(hong.집) // 대전 

```

김, 정, 홍, 이는 모두 대전에 살고 있다가 전주로 이사갔다고 하면 이들이 사는 지역명을 모두 전주로 바꿔야 할 것입니다.     

Home이라는 클래스에 집 이라는 변수 프로퍼티가 있다고 하고, 클래스 Home의 인스턴스들인    

상수 kim, jung, hong, lee는 서로의 값을 참조하고 있다고 하면, kim의 프로퍼티인 집을 “대전”에서 “전주”    

로 바꾸면 이들이 사는 지역명이 모두 변경되게 됩니다.






