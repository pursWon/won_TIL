7.22 공부 기록 
===

#### Switch 문에 대하여
---

switch문은 각 패턴으로 결과를 비교하여 그 결과를 도출해내는 조건문이다.
각 case에는 실행 가능한 문장 하나가 꼭 포함이 되어야 한다. 
모든 case들에 해당되는 모든 경우의 수를 처리했을 때, default 값을 생략할 수 있다. 

## 1. switch 기본문
---
```swift
let english: Character = "d"
switch english {
case "a": // case안에 들어갈 값을 적은 후에 : 를 붙일 것
    print("a가 나오네요")
case "b":
    print("b가 나오네요")
case "c":
    print("c가 나오네요")
default:
    print("abc외에 다른 게 나오네요")
}
```

## 2. switch의 Interval Matching 
---
```swift
let number = 21

switch number {

case 0..<10:
print("10미만")

case 11..<20:
print("11이상 20미만")
    
case 21..<30:
print("21이상 30미만")

default:
print("그외의 숫자 범위")
    
}
```


## 3. switch의 fallthrough 문

fallthrough 문은 매칭된 블록을 실행하고 종료하지 않고 이어지는 블록을 실행하고 종료한다.
코드를 중복시키지 않는데 자주 사용된다. 

---
```swift
let verse: Int = 19

switch verse {
    
case 1..<10:
print("애기시네요")
    
case 10..<20:  // 숫자 범위를 적은 후 : 를 붙일 것
print("잼민이시네요")
fallthrough
    
case 21..<30:
print("대학생 혹은 직딩이시네요")
fallthrough

default:
print("우리 모두 힘냅시다")

// print 결과물 : 잼민이시네요
// 대학생 혹은 직딩이시네요
// 우리 모두 힘냅시다
}
```

## 4. switch문의 where문
---
where 문을 사용하여 case 문에 조건을 추가할 수 있다.
아래의 코드에서는 범위뿐만 아니라 3이나 2로 나누었을 때 나머지가 0이라는 조건을 추가하였다. 

```swift
var corte: Int = 150

switch corte {

case 1...100 where corte % 3 == 0:
print("hoho")
    
case 100..<200 where corte % 2 == 0:
print("haha")
    
default:
print("nothing")
}
```






