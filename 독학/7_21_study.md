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

### for문과 switch문을 이용한 로또 
---
```swift
var lotto1 = Int.random(in: 1...20)
var lotto2 = Int.random(in: 1...20)
var lotto3 = Int.random(in: 1...20)
var lotto4 = Int.random(in: 1...20)

let lucky: [Int] = [lotto1, lotto2, lotto3, lotto4]
print(lucky)

let Y: [Int] = [3, 15, 18, 9]

var count: Int = 0

for p in lucky {
    for o in Y {
     if p == o {
count += 1
     }
     }
}


switch count {
case 0:
print("0개 당첨")
case 1:
print("1개 당첨")
case 2:
print("2개 당첨")
case 3:
print("3개 당첨")
default:
print("완벽한 당첨이로군요")
}
```


