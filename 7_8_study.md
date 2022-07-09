7.8 수업 내용
==

변수(var)와 상수(let)
----
var 변수명: 타입명 = 값
let 상수명: 타입명 = 값 
import Foundation // Int, String이 담겨있는 다운로드 패키지 


```swift

var hello = "hello!"
var alphabet: Character = "A"
```
Swift의 특징 중 하나는 타입 추론이 가능하다.  

애매할 때는 타입 명시를 해주자.  

명시를 해줄 경우에 컴파일 속도가 조금 빨라진다.

연습할 때는 무조건 타입 명시


기본 데이터 타입 : String, Int, Character, Bool, Float, Double
---

```swift
var hello: String = "Hello, World!"
var comment: String = """
hi
my name is wongi Hong
"""
print(comment)
```

```swift
hello.count // 문자열에 들어있는 문자의 갯수를 알려주는 프로퍼티
hello.isEmpty // 문자열이 비어있는지 체크하는 프로퍼티 
hello.append // 문자열에 뒤에 새로운 문자열을 추가하는 함수 
```

```swift
let upperhello = hello.uppercased() // 문자열을 대문자로 바꾼 후에 문자열을 리턴하는 함수
let lowerhello = hello.lowercased() // 문자열을 소문자로 바꾼 후에 문자열을 리턴하는 함수 
print(hello) // "Hello, World!"
print(upperhello) // "HELLO, WORLD!"
print(lowerhello) // "hello, world!"
```

```swift
hello.removeAll() // 문자열 전체를 지우는 함수
hello.removeFirst() // 첫글자를 지우는 함수 
hello.removeLast() // 마지막 글자를 지우는 함수
print(hello)
```

Character
---

```swift
let alphabet: Character = "c"
print(alphabet)
alphabet.isLetter // 문자가 문자인지 아닌지 체크해주는 프로퍼티
alphabet.isNumber// 문자가 숫자인지 아닌지 체크해주는 프로퍼티
alphabet.isUppercase // 문자가 대문자인지 체크해주는 프로퍼티
alphabet.isWhitespace // 공백이 있는지 체크하기
```
Int
---
```var number: Int = 43
number.negate() // 숫자의 부호를 바꿔주는 함수 -> -43
String(number) // 타입(값) <- 해당 타입으로 값을 반환해준다(형변환)
Float(number) // 타입(값) <- 해당 타입으로 값을 반환해준다(형변환)

let floatValue: Float = 4.7
round(floatValue) // 반올림
ceil(floatValue) // 올림
floor(floatValue) // 내림
```

Bool
---
```swift
var flag: Bool = true
flag.toggle() // 값을 변경하는 함수 -> false 
flag.toggle() // true
flag.toggle() // false
```

컬렉션 타입 : Array
---
```swift
var array: [String] = ["a", "b", "c", "d", "e"]
array[2...4] // 뒤에 있는 인덱스 이하의 원소
array[3..<4] // 뒤에 있는 인덱스 미만의 원소
array.contains("q")
array.append("f")
array.insert("z", at: 1)
```

컬렉션 타입 : Set
---
```swift
var set: Set<Int> = [1, 1, 2, 2, 3, 3, 3] 
print(set) // set는 순서가 없고 중복이 없다 
set.contains(4)
print(Int(a))
```

컬렉션 타입 : Dictionary 
---
```swift
var dict: [String: Int] = [:] 
dict["one"] = 1
dict["two"] = 2
dict["three"] = 3

let t = dict["three"]
dict["one"] = 7
print(dict.keys) // 같은 키에 값을 또 생성하면 덮어쓰기 된다 
```

컨트롤 플로우 : for
---
```swift
for i in 0..<array.count {
print(array[i])
}
```

상수에 할당 접근
```swift
for a in array {
print(a)
}
```

```swift
array.forEach { alpha in 
print(alpha)
}
```

컨트롤 플로우 : while
---
```swift
var num: Int = 0 // 조건을 만족하는 동안 반복 
print("start)
while true { 
print(num)
num += 1

if num == 5 { // 5가 될 경우 
print("5다!") // "5다!"를 프린트하고
break // 반복을 멈춘다.
}

}

print("finish")
```








