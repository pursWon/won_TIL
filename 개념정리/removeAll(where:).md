removeAll(where:)
===

Removes all the elements that satisfy the given predicate.
-> 주어진 조건을 만족하는 원소를 모두 삭제한다. 

**예시 :**    

```swift
var strings: [String] = ["able", "can", "good", "happy", "luck"]

strings.removeAll(where: { $0 == "able" })
print(strings) // ["can", "good", "happy", "luck"]
```

-> strings의 배열에서 "able"이 해당되는 원소를 지운다. 

```swift
var string: String = "I can do this all day."
let a: [Character] = ["a", "c", "d"]
string.removeAll(where: { a.contains($0) })
print(string) // I n o this ll y.
```

-> string의 문장에서 a가 포함하고 있는 문자들을 지울 수 있다. 

```swift

var numbers: [Int] = [25, 10, 14, 18, 100, 45]
numbers.removeAll { $0 % 5 == 0 }
print(numbers) // [14, 18]

```

-> removeAll에서 소괄호와 where를 제외하고도 이런 식으로 사용이 가능하다.
