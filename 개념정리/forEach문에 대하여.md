forEach문에 대하여
===========

for문과 동일한 순서로 컨테이너의 각 요소에 대한 주어진 클로저를 호출한다.    

**선언** 

```swift 

func forEach(_ body: (Element) throws -> Void) rethrows

```
      
**매개 변수**

body는 컨테이너의 요소를 매개 변수로 사용하는 클로저이다.   



**예시**

```swift

let numberWords = [One, Two, Three]

numberWords.forEach { word in 

print(word)

}
// One
// Two
// Three
```















