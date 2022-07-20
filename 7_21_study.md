7.21 공부 기록
===

### func를 이용하여 문자열에서 문자와 숫자를 분리하는 코드를 짜보기 
---

```swift
func hello1(letter1: String) -> String {
let hola1 = letter1
    
let salut = hola1.filter{$0.isNumber}
return salut
}

var result1 = hello1(letter1: "안녕2하세2요는 스2페인말2로 hola")
print(result1)

func hello2(letter2: String) -> String {
let hola2 = letter2
    
let hoi = hola2.filter{$0.isLetter}
return hoi
}

var result2 = hello2(letter2: "안녕2하세2요는 스2페인말2로 hola")
print(result2)
```
