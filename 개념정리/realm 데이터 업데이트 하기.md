realm 데이터 업데이트 하기
===============

realm에 들어가있는 기존의 데이터를 다른 데이터로 바꿀 수 있다. 

그때는, 아래와 같은 코드를 사용한다.

```swift 

if let update = goodObject.filter(NSPredicate(format: "storeName = %@", store)).first {
// goodObject 배열에 storeName 요소가 store 객체와 같은 goodObject 객체를 담는 배열을 만든다. 그리고 그 배열의 첫번째 멤버가 존재한다면 update에 담아준다. 
                            try! realm.write {
                                update.rating = storeRating
// update문이 존재한다면 update의 rating을 storeRating으로 업데이트 해준다. 
   }
}

```
