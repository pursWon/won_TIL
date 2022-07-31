7월 31일 공부
===

타입 선언
---
스위프트에서 변수의 선언과 초기화는 동시에 할 수 있지만 분리하여 선언을 먼저하고 필요한 때에 초기화를 할 수도 있다.

```swift
var genre1 = "Rock" // 선언과 초기화를 동시에 
var genre2: String 
genre2 = "Hip-Hop"
```

타입 어노테이션 
---
타입 어노테이션이란, 변수나 상수를 선언할 때 그 타입을 명시적으로 선언해줌으로써 어떤 타입의 값이 저장될 것인지를 컴파일러에 직접적으로 알려주는 문법 
변수나 상수명 뒤에 콜론을 붙이고, 이어서 저장될 값의 타입을 작성.

```swift
var number: Int // 명시적인 Int 타입 
var hello: String // 명시적인 String 타입 
var o : Character // 명시적인 Character 타입
var distance : Double // 명시적인 Double 타입
var fact ; Bool // 명시적인 Bool 타입 
```

타입 추론
---
변수나 상수에 타입을 정하지 않고 값만 넣어서 초기화가 가능하다. 변수나 상수를 초기화할 때 입력된 값을 분석하여 변수에 적절한 타입을 컴파일러가 알아서 추론하는 기능이다. 

```swift
let eleven = 11 // 해당 값을 컴파일러가 Int로 추론 
let name = "김남준" // 해당 값을 컴파일러가 String으로 추론 
```

타입 추론으로 얻어지는 타입이 아닌, 직접 타입을 지정해야 할 때 ! 

- 추론되는 타입이 아닌 직접 지정을 해줘야 할 때
- 선언과 초기화를 따로 해줘야 할 때

```swift
let alphabet: Character = "A" // 타입 추론을 사용한다면 String으로 지정되기 때문에 Character로 따로 지정을 해야한다.
let number70: Float = 70 // 타입 추론을 사용한다면 Int로 지정되기 때문에 Float으로 따로 지정을 했다.
let name: String
name = "홍원기" // 선언과 초기화를 따로 해줘야 할 때 타입 어노테이션을 사용한다. 
