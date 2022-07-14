7.13 공부 내용
===
코딩 문제 
=== 

학생의 이름, 나이를 입력받아 출력해주세요. (이름과 나이를 각각 readLine() 으로 받으시면 됩니다)
---



```swift
import Foundation

print("이름 : ", terminator: " ")
let myName = readLine()!
print("나이 : ", terminator: " ")
let myAge = readLine()!

print("\(myName)" + " 학생의 나이는" + " \(myAge)입니다")

// 과제 : 4번을 응용하여 아래와 같이 학생의 학년을 출력해주세요.
print("이름 : ", terminator: " ")
var myName2 = readLine()!
print("나이 : ", terminator: " ")
let myAge2 = Int(readLine()!)!

if myAge2 == 17 {
    print("\(myName2)은 고등학교 1학년이군요")
} else if myAge2 == 18 {
    print("\(myName2)은 고등학교 2학년이군요")
} else if myAge2 == 19 {
    print("(\(myName2)은 고등학교 3학년이군요")
} else {
    print("너는 고딩이 아니군요")
}
```

readLine()을 이용하여 문자열에서 문자와 숫자를 분리
---
```swift
import Foundation

let helloNum = readLine()! // readLine()에 !를 넣어서 String으로 변환
let filterStr = helloNum.filter{$0.isNumber} // filter{$0.isNumber}를 이용하여 숫자만 꺼내기
print(filterStr) // 꺼낸 숫자만 filterStr에 담고 프린트
let filterInt = helloNum.filter{$0.isLetter} // filter{$0.isLetter}를 이용하여 문자만 꺼내기
print(filterInt) // 꺼낸 문자만 filterInt에 담고 프린트
```








