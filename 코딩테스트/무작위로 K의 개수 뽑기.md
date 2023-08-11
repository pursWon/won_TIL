무작위로 K의 개수 뽑기
================

랜덤으로 서로 다른 k개의 수를 저장한 배열을 만드려고 합니다.    

적절한 방법이 떠오르지 않기 때문에 일정한 범위 내에서 무작위로 수를 뽑은 후,    

지금까지 나온적이 없는 수이면 배열 맨 뒤에 추가하는 방식으로 만들기로 합니다.       

이미 어떤 수가 무작위로 주어질지 알고 있다고 가정하고, 실제 만들어질 길이 `k`의 배열을 예상해봅시다.       

정수 배열 `arr`가 주어집니다. 문제에서의 무작위의 수는 `arr`에 저장된 순서대로 주어질 예정이라고 했을 때,    

완성될 배열을 return 하는 solution 함수를 완성해 주세요.       

단, 완성될 배열의 길이가 `k`보다 작으면 나머지 값을 전부 -1로 채워서 return 합니다.       

</br>

입출력 예시

| arr |	k | result |
|--|--|--|
| [0, 1, 1, 2, 2, 3] |	3	 |[0, 1, 2] |
| [0, 1, 1, 1, 1]	| 4	| [0, 1, -1, -1 |

</br>

## 나의 풀이

```swift

import Foundation

func solution(_ arr:[Int], _ k:Int) -> [Int] {
    var newArr: [Int] = []
    
    for i in arr {
        if !newArr.contains(where: { $0 == i }), newArr.count < k {
            newArr.append(i)
        }
    }
    
    if newArr.count < k {
        while newArr.count < k {
            newArr.append(-1)
        }
    }
    
    return newArr
}

```
