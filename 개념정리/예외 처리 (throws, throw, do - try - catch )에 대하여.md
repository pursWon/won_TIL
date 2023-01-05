예외 처리 (throws, throw, do - try - catch )에 대하여
===========

예외 처리가 필요한 이유? 

→ 옵셔널 타입은 오류가 발생했을 때 오류에 대한 정보를 외부로 전달할 방법이 없다. 

1. **오류의 종류를 정의**

```swift
enum McDonaldOrderError: Error { // 에러 타입 정의
     case invalidSelection
     case LackOfMoney
     case outOfStock
}
```

햄버거 구조체를 설정   

```swift 
struct Hamburger { // 햄버거 구조체 설정
    var name: String
    var price: Int
    var count: Int
}
```

내가 가진 돈과 햄버거의 이름, 가격, 재고

```swift 
let myMoney: Int = 4000 // 내가 가진 돈
let bigMac = Hamburger(name: "BigMac", price: 4600, count: 3) // 빅맥, 4600원, 재고 3개
```

2. **오류가 나는 조건을 throw와 throws로 선언** 

오류가 발생할 수 있다는 조건을 표현 : throws를 “→” 앞에 표시한다(반환 전에 오류가 발생하면, 오류 객체를 반환한다는 의미이다.)

throw와 오류명 집어넣기 

```swift
func OrderMcDonaldMenu(orderedMeun: Hamburger) throws { // 에러를 발생시키는 함수 정의
    if orderedMeun.name != "BigMac" {
        throw McDonaldOrderError.invalidSelection
    }
    if orderedMeun.price > myMoney {
        throw McDonaldOrderError.LackOfMoney
    }
    if orderedMeun.count == 0 {
        throw McDonaldOrderError.outOfStock
    }
}
```

3. **do - try - catch 로 접근** 

마지막 catch에 <오류타입>을 작성하지 않으면 default문으로 됨

```swift
do {
    try OrderMcDonaldMenu(orderedMeun: bigMac)
} catch McDonaldOrderError.invalidSelection {
    print("저희 매장에 주문한 메뉴가 없습니다. 메뉴이름을 다시 확인해주세요.")
} catch McDonaldOrderError.LackOfMoney {
    print("메뉴를 주문하기에 고객님의 잔액이 부족합니다.")
} catch McDonaldOrderError.outOfStock {
    print("현재 재고가 없어 주문이 불가능합니다.")
}

```

가진 돈이 600원이 부족하므로 "메뉴를 주문하기에 고객님의 잔액이 부족합니다."를 프린트해준다. 

전체 코드

```swift
import Foundation

enum McDonaldOrderError: Error { // 에러 타입 정의
     case invalidSelection
     case LackOfMoney
     case outOfStock
}

struct Hamburger { // 햄버거 구조체 설정
    var name: String
    var price: Int
    var count: Int
}

let myMoney: Int = 4000 // 내가 가진 돈
let bigMac = Hamburger(name: "BigMac", price: 4600, count: 3) // 빅맥, 4600원, 재고 3개

func OrderMcDonaldMenu(orderedMeun: Hamburger) throws { // 에러를 발생시키는 함수 정의
    if orderedMeun.name != "BigMac" {
        throw McDonaldOrderError.invalidSelection
    }
    if orderedMeun.price > myMoney {
        throw McDonaldOrderError.LackOfMoney
    }
    if orderedMeun.count == 0 {
        throw McDonaldOrderError.outOfStock
    }
}

do {
    try OrderMcDonaldMenu(orderedMeun: bigMac)
} catch McDonaldOrderError.invalidSelection {
    print("저희 매장에 주문한 메뉴가 없습니다. 메뉴이름을 다시 확인해주세요.")
} catch McDonaldOrderError.LackOfMoney {
    print("메뉴를 주문하기에 고객님의 잔액이 부족합니다.")
} catch McDonaldOrderError.outOfStock {
    print("현재 재고가 없어 주문이 불가능합니다.")
}




