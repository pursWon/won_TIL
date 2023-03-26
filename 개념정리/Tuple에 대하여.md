Tuple에 대하여
=============

간단한 구조체라고 생각하면 편하다.

여러가지 **타입**을 **한꺼번에 묶어서** 사용할 수 있다. 

```swift
import Foundation

let tupleOne: (Int, String, Bool) = (1, "안녕", true)
```

tuple에는 named type을 담을 수 있고 함수나 tuple같은 compound type도 담을 수 있다. 

- tuple을 담기

```swift
import Foundation

let tupleOne: (Int, String, Bool) = (1, "안녕", true)

let tupleTwo = (2, tupleOne)
```

- 함수를 담기

```swift
func a() -> Int { return 10 }

func b(number: Int) -> Int {
    let another = number + 20
    
    return another
}

let tupleThree = (a(), b(number: 30))
print(tupleThree) // (10, 50)
```

tuple안에 있는 값 호출하기 

```swift
let tupleThree = (a(), b(number: 30))
print(tupleThree) // (10, 50)

tupleThree.0 // 10
tupleThree.1 // 50 
```

tuple안에 있는 index를 통해 값을 가져올 수 있다. 

tuple안의 멤버들에 이름을 줄 수 있다. 

```swift
let tupleFour = (name: "철수", 함수: b(number: 100), tuple: (true, "or", false), number: 33)

print(tupleFour.name)
print(tupleFour.함수)
print(tupleFour.tuple)
print(tupleFour.number)
```

이름을 지정함으로써 index가 아닌 이름으로 멤버를 호출할 수 있다. 

tuple로 배열도 만들 수 있다. 

```swift
let tupleFive: [(Int, String)] = [(1, "One"), (2, "Two"), (3, "Three")]

```

tuple 배열의 타입에 이름을 지정해줄 수 있다.

```swift
let tupleFive: [(number: Int, word: String)] = [(1, "One"), (2, "Two"), (3, "Three")]

for item in tupleFive {
    print(item.number)
}
```

이름을 지정해줌에 따라 for 문등을 사용할 때 이름을 통해 멤버를 호출할 수 있다. 

```swift
let tupleFive: [(Int, String)] = [(1, "One"), (2, "Two"), (3, "Three")]

for item in tupleFive {
    print(item.1)
}
```

이름을 제거할 경우에는 index를 통해서 멤버에 접근이 가능하다. 

특정한 이름이 아니어라도 tuple 개수와 맞게 선언해주면 이렇게도 사용이 가능하다.

```swift
let tupleSix = (15, "집", false)

let (number, home, bool) = tupleSix
print(bool) // false
```

```swift
let tupleSix = (15, "집", false)

let (_, home, _) = tupleSix
print(home) // 집
```

특정 데이터만 받고 싶을 때에는 이와같이 작성할 수 있다. 

tuple의 또 다른 특징은 함수를 리턴할 때 한 가지 타입만 리턴하는 것이 아닌 여러 타입을 동시에 리턴시킬 수 있다는 점이다.

```swift
func jj() -> (String, Int, Bool) {
    return ("비비", 30, true)
}

print(jj()) // ("비비", 30, true)
```

```swift
func jj() -> (String, Int, Bool) {
    return ("비비", 30, true)
}

let j = jj()

print(j.0) // "비비"
print(j.1) // 30
print(j.2) // true
```

함수에서 tuple을 리턴시킴에 따라 index를 통해서 멤버를 호출할 수도 있다. 

tuple은 typealias와 같이 쓰면 깔끔하게 쓸 수 있다.

```swift
typealias People = (name: String, age: Int, gender: String)

let 민수: People = ("최민수", 40, "man")

let 민수들: [People] = [("홍민수", 32, "man"), ("여민수", 21, "woman"), ("고민수", 28, "man")]
```
