7.25 공부 기록
===

Optional에 대하여 
---
직역하면 선택적인. 그 뜻은 값이 있을수도 있고 없을수도 있다.  

Optional을 사용할 때에는 타입 어노테이션에 ?를 붙여야하며, 초기값을 지정해주지 않으면 기본값은 nil이다. 
```swift
var optionalEX: String? // 이 값은 nil이 나오게 된다.
```

Force Unrapping (강제 언랩핑)
---
```swift
let watch: String? = "time"
print(watch!)
```
!를 붙여줌으로써 강제 언랩핑 해준다.    

이 때, 값이 없다면 런타임 에러가 발생하여 Xcode가 튕길수도 있으므로 그다지 좋은 방법은 아니다.

Optional Binding (옵셔널 바인딩)
---
```swift
var myNumber: Int? = 777
var myNumber2: Int?
if let myLife = myNumber2 {
    print("나의 인생은 행운으로 가득찼구나") // myNumber의 값이 존재하므로 myLife에 값이 할당된다.
} else {
    print("내 인생의 어떤 날은 불운할수도 있겠구나")
}

if let myAge = myNumber2 { // myNumber2에 값이 없으므로 myAge에 할당되지 않고 패스됨
    print(28)
}
```

옵셔널 바인딩이라는 것은 안전하게 값이 있는지를 확인해보고 임시 변수나 상수에 할당을 해주는 기능이다.   

if문을 이용하여 옵셔널에 있는 값을 임시 변수나 상수에 할당해주는 것이다.   

만약에 optional에 값이 있다면 할당하고 nil이면 패스하는 방식을 가진다.   

여러 옵셔널을 바인딩 
---
```swift
var movieName1: String?
var movieName2: String?

movieName1 = "LALA LAND"
movieName2 = "TOP GUN"

if let goodMovie1 = movieName1,
   let goodMovie2 = movieName2 {
    print(goodMovie1, goodMovie2)
}
```
여러개의 옵셔널을 바인딩 할 수 있다. 

Optional Chanining (옵셔널 체이닝)
---
```swift
let array: [String]? = []

var isEmptyArray: Bool = false

if let array = array, array.isEmpty {
  isEmptyArray = true
} else {
  isEmptyArray = false
}

print(isEmptyArray)
```

이렇게 옵셔널 체이닝을 이용하여 코드를 줄일 수 있다. 

```swift
let isEmptyArray = array?.isEmpty == true
```


