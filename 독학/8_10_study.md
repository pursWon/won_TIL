8월 10일 공부 내용
===

함수의 심화 개념 
---

**(1) 파라미터로 전달되는 Value의 값은 복사된 상수 값이다** 

value 타입의 값(let이나 var에 속한 Int나 String 타입들을 의미함)은 복사되서 전달된다.      

이 때, 복사된 값은 상수이다.      

```swift

var hong: String = "원기씨"

func bye(name: String) {
    name = "태현씨"
}

bye(name: hong) // 호출 시 오류 발생 

```
여기서 변수 hong의 value 값인 "원기씨"를 함수 bye의 파라미터 값으로 넘겨주게 되면, 

name의 파라미터 값인 "원기씨"를 복사해서 파라미터로 가지게 된다.   

따라서, 함수 bye를 호출될 때에 값을 "태현씨"로 바꿔도 함수 내부에는 전혀 영향을 주지 못하게 된다. 

파라미터로 전달된 값은 변경하지 못하는 상수이기 때문이다.    

**(2) 파라미터로 전달되는 Reference의 값은 참조된다**

Reference Type의 값을 파라미터로 전달할 경우, 참조로 전달된다.   

파라미터로 참조타입을 전달할 경우에는, 전달되는 값의 주소를 들고 온다.   

```swift

class Human { // 클래스는 레퍼런스 타입
    var name: String
    var age: Int
    
    init(name: String, age: Int) {
        self.name = name
        self.age = age
    }
    
}


func singer(human: Human) { // 레퍼런스 타입을 파라미터에 전달
    human.name = "dean" // 프로퍼티 name에 dean을 설정
}

let b = Human.init(name: "zico", age: 27) // 상수 b에 초기화한 값을 설정.
singer(human: b) // 함수 singer 호출
print(b.name) // name을 zico로 설정했지만 파라미터에 참조 타입을 전달할 경우에는 복사된 상수 값이 아닌 주소값이 전달되므로 값이 변경된다.

```

클래스 Human을 만들어서 Reference Type의 값을 파라미터에 전달할 경우, 값은 복사되지 않고 참조된다.   

따라서 밑에 상수 b를 만들어서 해당 값을 지정해도 함수에서 값을 변경하면 호출할 때에 값은 변경되서 나오게 된다.   

**(3) In-Out 파라미터: Value 타입의 값을 참조로 전달하는 방법**

입출력 파라미터라고 한다.   

value 타입의 값은 파라미터로 전달될 때, 상수로 전달되는데, 이를 참조로 전달되게하는 방법이다.   

```swift

func juice(fruit: inout String) {
fruit = "Orange"
}

var apple: String = "apple"
juice(fruit: &apple)
print(apple) // 결과물 : "Orange"

```

타입 앞에 inout을 적어주고, 호출할 때에 변수 앞에 &를 붙여주면 된다.   

