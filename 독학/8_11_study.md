8월 11일 공부
===

배열에서 빠진 숫자만 더하는 함수 만들어보기
---

```swift
let numbers: [Int] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

var different: [Int] = []

var answer: Int = 0

func Calculate(array: Int...) {
    for c in numbers {
        if array.contains(c) == false  { // numbers 배열을 순회하는 c가 
        // 배열 array에서 포함되지 않을 때(true면 포함이 될 때)
        different.append(c) // c를 different 배열에 추가한다.
        }
    }
    print(different) // [0, 8, 9]
    
    for d in 0..<different.count { // different 배열에서 d가 마지막 순번까지 돌면서
    answer += different[d] // 0에 different 배열의 d번째 숫자를 반복해서 더해준다.
    
    }
    
    print(answer) // 17
    
    }
        

Calculate(array: 1, 2, 3, 4, 5, 6, 7)
```
