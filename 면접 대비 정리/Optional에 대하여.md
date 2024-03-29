Optional에 대하여 
===========

옵셔널을 사용하는 경우, Optional(?)나 Forced Unwrapping(!), nil coalescing operator을 사용하게 되고, Optional Chainning(?)을 사용한 경우엔, 값에 대하여 노크를 하는 행위와 같습니다.     

만약에 값이 있다면 해당 값을 반환하고, 값이 없다면 nil을 반환하게 됩니다. 

ex) person?.residence?.address

반면에, !는 문을 부순다는 행위와 같은데 값에 대하여 강제 언랩핑을 해줌으로써 값이 있다면 값을 반환할 수 있지만 값이 없을 경우 값이 존재하지 않는 옵셔널 값에 접근함으로서 런타임 에러가 발생할 것입니다. 

**nil 병합 연산자**는 ??를 사용하여 한 줄로 언랩핑을 할 수 있다. 예를 들어, box라는 상수는 옵셔널 String값이고 해당 값에 선물이 들어있는지 확인하기 위해서 openBox 라는 상수에 box ?? 

“Nothing”을 대입했다하면 값이 있을 경우엔 box를 언랩핑하여 openBox 상수에 담아줄 것이고, 값이 nil이라면 Nothing을 담아줄 것입니다.

**nil 병합 연산자**의 예시 코드 → 

```swift
import Foundation

let box: String? = "Present"

let openBox = box ?? "Nothing"
print(openBox)
```

**옵셔널 바인딩**을 사용하게 되면 안전하게 옵셔널 값을 언랩핑 할 수 있습니다.

**옵셔널 바인딩**을 사용하는 경우, **if let** 그리고 **guard let**이 있습니다.

if let 구문의 특징에 대해서 말씀드리겠습니다.    

첫번째,  조건문의 Optional 값이 nil인지 확인하고 2분기로  분기처리하는 작업할 수 있습니다.    

if let구문안에서만 지역변수로 사용이 가능합니다.     

조건을 가지고 나누어 처리해야 하는 상황에서는 guard문이 아닌 if let을 사용하는 것이 좋습니다.     
 
guard let의 특징에 대해서 말씀드리겠습니다.     

함수에서만 쓰이며, guard 구문의 조건을 만족시키지 못하면, else문으로 빠져서 함수의 실행을 종료시킬 때 사용합니다.      

그리고 전역변수로 사용이 가능합니다.     

마지막으로 return, break, throw 등의 제어문 전환 명령어를 반드시 사용해야 합니다.    

if let과 guard let의 차이점에 대해서 말씀드리겠습니다.    

첫번째, if let은 지역 변수로 if let 구문안에서만 사용이 가능하지만 guard let은 전역 변수로 함수 전체에서 사용이 가능합니다. 추출한 옵셔널 값을 함수에서 사용하고 싶을 때 guard 문을 사용하면 좋습니다.     

두번째, if let은 else문을 생략할 수 있지만 guard let은 else문을 생략할 수 없습니다.      

guard let은 실행시키기 위해 조건을 검사한다는 의미를 가집니다.     

실패할 경우, early exit이 이루어지는만큼 표현이 명확합니다.     

guard문을 사용해서 화면전환을 하는데 이동하고자 하는 화면이 존재하지 않으면 조기 종료를 하고 화면이 존재하면 화면 전환이 이루어집니다.   
