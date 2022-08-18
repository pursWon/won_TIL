Array의 메소드
===

**1. 배열 생성하기**

```swift

let array1 = [1, 2, 3]

let array2: [Int] = [1, 2, 3]

```

배열을 선언할 때에 선언할 수 있는 방법은 대표적으로 위의 2가지가 존재한다.   

Swift는 타입에 굉장히 민감한 언어이므로 무언가를 선언할 때에는 반드시 타입을 명시해주도록 하자.    

**2. 배열 개수 확인하기**

```swift

let array: [String] = "abcde"

let isEmpty: Bool = array.isEmpty // false 

```

배열이 비었는지를 확인할 때에는 isEmpty 메소드를 사용하자.   

**3. 배열 요소에 접근하기**

```swift

var array: [Int] = [1, 3, 5]

// 1. Subscript로 접근하기
array[0] // 1
array[2] // 5

// 2. 범위로 접근하기
array[0..2] // [1, 3, 5]

// 3. 속성으로 접근하기 
array.first // Optional(1)
array.last // Optioanl(5)

```

Subscript나 범위로 접근하는 것은 위험성이 있다.    

그건 반환하는 값이 Non - Optional이기 때문이다.   

만약 해당 index에 값이 없으면 그것은 에러로 빠지게 된다.   

따라서, 첫번째, 마지막 요소에 접근할 것이라면 속성으로 접근하는 방법이 낫다.     


















