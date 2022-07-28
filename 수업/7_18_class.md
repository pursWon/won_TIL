7.18 수업 내용 
===

함수에 대하여
---
```swift
/*
 함수란
 - input을 우리가 원하는 결과물의 형태로 변환하는 것
 - input을 사용하여 내가 필요한 작업을 수행해주는 것
 - 코드 묶음

 */

//func 함수명(인자명 : 인자타입) -> 타입 {
//    // 내가 해주고 싶은 작업
//}
//
func hello() {
    print("안녕")
}

hello()

func hello2(name: String, text: String) {
    print("\(name) 안녕! \(text)")
}

hello2(name: "철수", text: "반가워")

func hello3(name: String) -> String {
    return "\(name) 안녕!"
}

let result = hello3(name: "철수")
print(result)

func hello4() -> String { // 리턴 타입
    return "하이" // 던져나오는 결과물
}
/*
hello4 함수를 실행한 결과물을 result2라는 상수에 담아준다.
 for문을 통해 0..<4 범위 동안 반복문을 돌면서,
for 블록 안에 있는 print문을 실행한다. (0..<4이므로 0,1,2,3 총 4번)
 */

let result2 = hello4()

for _ in 0..<4 {
    print(result2)
}
    
print(result2)

// -> 타입이 적혀있는 리턴값이 있는 형태는 함수를 부르면
// 함수 {} 안에 있는 코드들을 실행한 후 return 키워드 위에 있는 값을 던져준다.
// 개발자스럽게 바꾸면, "함수를 실행하면, 리턴타입과 같은 타입의 함수 블록을 실행한 결과를 리턴해준다."
// 리턴된 값을 어떤 변수 혹은 상수에 담아 활용할 수 있다.
//
```
