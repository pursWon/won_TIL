함수의 기본 
===
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
