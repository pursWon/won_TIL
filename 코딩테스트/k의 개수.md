k의 개수
===============

1부터 13까지의 수에서, 1은 1, 10, 11, 12, 13 이렇게 총 6번 등장합니다.   
정수 i, j, k가 매개변수로 주어질 때, i부터 j까지 k가 몇 번 등장하는지 return 하도록 solution 함수를 완성해주세요.   

```swift 

import Foundation

func solution(_ i:Int, _ j:Int, _ k: Int) -> Int {
    var numbers: [Int] = []
    var count: Int = 0
    
    for a in i...j {
        numbers.append(a)
    }
    
    
    for number in numbers {
        let b = String(number).map{ String($0) }.map{ Int($0) ?? 0 }
        
        for n in b {
            if n == k {
                count += 1
            }
        }
    }
    
    return count
}

solution(1, 13, 1) // 6
solution(5, 50, 5) // 5
solution(3, 10, 2) // 0

```

더 짧고 효율적인 풀이

```swift 

import Foundation

func solution(_ i:Int, _ j:Int, _ k:Int) -> Int {
    var answer = 0
    
    for n in i...j {
        answer += String(n).map{ String($0) }.filter{ $0 == String(k) }.count
    }
    
    return answer
}

```
