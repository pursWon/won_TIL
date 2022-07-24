7.24 공부 내용
===

## Dictionary에 대하여 
---

```swift
let dict: [String : String] = ["A" : "Apple", "B" : "Banana", "C" : "Cherry"]
  
for (key, value) in dict {
    print("(\(key) : \(value))")                     // (B : Banana) (C : Cherry) (A : Apple)
}
 
for element in dict {
    print("\(element.key) : \(element.value))")      // (B : Banana) (A : Apple) (C : Cherry)
}
```
Dictionary는 Key, Value로 정해져있는데 정렬되지 않고 결과값은 찍을 때마다 달라진다. 그말인 즉슨, 배열이 아니라 넣은 순서대로 정렬되지 않았기 때문이다. 
따라서 print값은 찍을 때마다 달라질 것이다. Dictionary는 순회하면서 받는 루플 상수 튜플 값(key, value)이며 
