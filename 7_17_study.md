7.17 공부 내용
===
함수의 기본 
---
```swift
import Swift

//MARK: - 함수의 선언

//MARK: 함수선언의 기본형태
//func: 함수이름(매개변수1이름: 매개변수1타입, 매개변수2이름: 매개변수2타입 ...) -> 반환타입 {
// 함수 구현부
// return 반환값
//}

func sum(a: Int, b: Int) -> Int { // 함수를 선언하려면 func를 써야한다.
    return a + b
}

sum(a: 3, b: 1) // 질문

//MARK: 반환 값이 없는 함수
//func 함수이름(매개변수1이름: 매개변수1타입, 매개변수2이름: 매개변수2타입...) -> Void {
// 함수 구현부
// return
//}

func printMyName(name: String) -> Void { // 반환값이 없는 경우는 Void()를 써주면 된다.
   print(name)
}

func printYourName(name: String) {
    print(name)
}

//MARK:매개변수가 없는 함수
//func 함수이름() -> 반환타입 {
// 함수 구현부
// return 반환값
//}

func maximumIntegerValue() -> Int { // 매개변수와 반환값이 없음. 매개변수가 없다면 괄호를 비워두면 됨.
    return Int.max
}

//MARK: 매개변수와 반환값이 없는 함수
//func 함수이름() -> Void {
// return
//}

func hello() -> Void { print("hello") }

//func 함수이름() {
// 함수 구현부
// return
// }

func bye() { print("bye") }

sum(a: 3, b: 5) // 8

printMyName(name: "yagom") // yagom

printYourName(name: "hana") // hana

maximumIntegerValue() // Int의 최대값

hello() // hello

bye() // bye
```

함수의 응용
---
```swift
import Swift

//MARK: - 매개변수 기본값
 
// 기본값을 갖는 매개변수는 매개변수 목록 중에 뒤쪽에 위치하는 것이 좋다.
// func 함수이름(매개변수1이름 : 매개변수1타입, 매개변수2타입 = 매개변수 기본값 ... ) -> 반환타입 {
// 함수 구현부
// return 반환값
// }

func greeting(friend: String, me: String = "yagom") { // 매개변수의 기본값을 선언해주고 뒤에 타입을 선언 우리가 기본값 외에   다른 값을 넣어주고 싶다면 다른 매개변수를 입력하고 값을 넣어주면 된다.
    print("Hello \(friend)! I'm \(me)")
}

// 매개변수 기본값을 가지는 매개변수는 생략이 가능하다.
greeting(friend: "hana") // Hello hana! I'm yagom
greeting(friend: "john", me: "eric") // Hello John! I'm eric

//MARK: - 전달인자 레이블

//전달인자 레이블은 함수를 호출할 때
//매개변수의 역할을 좀 더 명확하게 하거나
//함수 사용자의 입장에서 표현하고자 할 때 사용한다
//func 함수 이름(전달인자 레이블 매개변수1이름: 매개변수1타입, 전달인자 레이블 매개변수2이름 : 매개변수2타입 ...) -> 반환타입 {
//함수 구현부
//return

// 함수 내부에서 전달인자를 사용할 때에는 매개변수 이름을 사용한다.
func greeting(to friend: String, from me: String) {
    print("Hello \(friend)! I'm \(me)")
}

// 함수를 호출할 때에는 전달인자 레이블을 사용해야 한다.
greeting(to: "hana", from: "yagom") // Hello hana! I'm yagom

//MARK: - 가변 매개변수

// 전달 받을 값의 개수를 알기 어려울 때 사용할 수 있다.
// 가변 매개변수는 함수당 하나만 가질 수 있다.

//func 함수 이름 (매개변수1이름: 매개변수1타입, 전달인자 레이블 매개변수2이름: 매개변수2타입....) -> 반환타입 {
// 함수 구현부
// return
// }

func sayHelloToFriends(me: String, friends: String...) -> String { // 뒤에 ...을 붙이게 되면 가변 매개함수가 된다.
    return "Hello \(friends)! I'm \(me)!"
}
print(sayHelloToFriends(me: "yagom", friends: "hana", "eric", "wing"))
// Hello ["hana", "eric", "wing"]! I'm yagom!

print(sayHelloToFriends(me: "yagom"))
// Hello []! I'm yagom!

/*
 위에 설명한 함수의 다양한 모양은 모두 섞어서 사용이 가능하다
 */

//MARK: - 데이터 타입으로서의 함수

// 스위프트는 함수형 프로그래밍 패러다임을 포함하는 다중 패러다임 언어이다.
// 스위프트의 함수는 일급객체이므로 변수, 상수 등에 저장이 가능하고
// 매개변수를 통해 전달할 수도 있다.

//MARK: 함수의 타입표현
// 반환타입을 생략할 수도 있다.
// (매개변수1타입, 매개변수2타입...) -> 반환타입

var someFunction: (String, String) -> Void = greeting(to:from:) //someFunction 자체가 함수이므로 바로 실행할 수 있게 된다.
someFunction("eric", "yagom") // Hello eric! I'm yagom

someFunction = greeting(friend:me:)
someFunction("eric", "yagom") // Hello eric! I'm yagom

// 타입이 다른 함수는 할당할 수 없다
// someFunction = sayHelloToFriends(me: friends:) -> 틀림 !
// sayHelloToFriends(me: friends:)에서 friends가 가변 매개 함수이므로 다른 타입의 함수에 할당 자체가 되지 않는다.

func runAnother(function: (String, String) -> Void) {
    function("jenny", "mike")
}


// Hello jenny! I'm mike
runAnother(function: greeting(friend:me:))

// Hello jenny! I'm mike
runAnother(function: someFunction)

func moim(boy: String = "wongi", girl: String) {
print("\(boy) is a handsome, and a \(girl) is pretty")
}

moim(girl: "violet")
moim(boy: "david", girl: "cindy")

func moimIn(to boy: String, from girl: String) {
    print("Hello, this is my friends \(boy) and \(girl)")
}

moimIn(to: "Moura", from: "Lily")
moimIn(to: "June", from: "Nana")

var someHaha: (String, String) -> Void = moimIn(to:from:)
someHaha("Andy", "Kai")
someHaha("Dean", "Wendy")

func arbi(function: (String, String) -> Void = moimIn(to:from:)) {
    function("Henry", "Dona")
}

arbi(function: moim(boy:girl:))
arbi() // 밑의 코드와 값이 같다.
arbi(function: moimIn(to:from:))
```




