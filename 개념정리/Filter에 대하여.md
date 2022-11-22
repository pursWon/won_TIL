Filter에 대하여 
========

**filter(_:)**

Returns an array containing, in order, the elements of the sequence that satisfy the given predicate.

해석 : 주어진 술어를 만족하는 시퀀스의 요소를 순서대로 포함하는 배열을 반환합니다.   

map과 마찬가지로 새로운 컨테이너에 걸러진 값들을 담아 반환하게 된다.   

map과의 차이점을 map은 기존의 요소를 변경한 값을 반환했다면 필터는 기준을 가지고 기준에 맞는 값들을 반환해준다는 것이다.   

기본 형태는 이와 같다.   
```swift

func filter(_ isIncluded: (Self.Element) throws -> Bool) rethrows -> [Self.Element]

```
예시는 다음과 같다. 

```swift 

let array = [0,1,2,3]
let filteredArray = array.filter { $0 % 2 == 0 }
print(filteredArray)   // [0, 2]

```
배열에서 2로 나눴을 때 나머지가 0이되는 조건을 충족했을 때, 프린트 해준다.   


