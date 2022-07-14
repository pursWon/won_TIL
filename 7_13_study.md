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









