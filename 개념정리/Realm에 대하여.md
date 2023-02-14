Realm에 대하여
=============

Realm(램)은 모바일에 특화된 NoSQL 데이터 베이스로 Swift, Objective-C, Java, Kotlin 등 

다양한 SDK를 제공한다. 

iOS에서 Realm을 사용할 경우, UserDefaults와 CoreData를 대체해    

Persistent data를 저장하고 관리할 수 있다.    

### <Realm 사용법>

https://github.com/realm/realm-swift

위의 링크를 Xcode에서 파일 → Add Package로 들어가 추가해준다.

그리고 Dependency Rule을 Branch말고 Up to Next Major Version으로 설정해준다.

추가해준 후에, Model을 설정을 다음과 같이 설정한다. 

```swift 

import Foundation
import RealmSwift

class Dog: Object {
    @Persisted(primaryKey: true) var _id: ObjectId // primary Key로 지정 
    @Persisted var name: String // 이름 
    @Persisted var breed: String // 종
    @Persisted var age: Int // 나이 
    
    convenience init(name: String, breed: String, age: Int) {
        self.init() 
        self.name = name
        self.breed = breed
        self.age = age
    } // class이므로 객체들을 초기화해야함
}

```

Realm에 저장할 데이터 객체를 정의할 때는 일반적인 모델을 정의하는 것처럼class를 만들고 필요한 

property를 정의하면 된다.

이때 Realm에서 사용할 수 있는 형태로 만들어 주려면 class가 `Object`를 상속해야 하고, 

Property를 정의할 때 앞에 `@Persisted`를 붙이기만 하면 된다. 

나는 Model 객체를 강아지로 정하고 property를 이름, 종, 나이로 정했다.

```swift

Realm에 저장할 데이터 객체를 정의할 때는 일반적인 모델을 정의하는 것처럼class를 만들고 필요한 

property를 정의하면 된다.

이때 Realm에서 사용할 수 있는 형태로 만들어 주려면 class가 `Object`를 상속해야 하고, 

Property를 정의할 때 앞에 `@Persisted`를 붙이기만 하면 된다. 

나는 Model 객체를 강아지로 정하고 property를 이름, 종, 나이로 정했다.

```

local default Realm 객체를 생성

```swift

print("Realm Location", localRealm.configuration.fileURL ?? "위치를 찾을 수 없습니다.")
// 파일 경로를 프린트해주고, 생성하지 못하였을 경우를 대비해서 nil coalesing operator를 사용

```

파일 경로를 프린트한다.     

<img width="575" alt="스크린샷 2023-02-13 오후 8 15 14" src="https://user-images.githubusercontent.com/99719661/218769148-88ce6425-18b4-4b8c-bb17-1f3f69205c01.png">

파일 경로를 프린트 한 후 /Users ~ Documents/ 까지 프린트 해준다. 

그리고 이동 → 폴더로 이동으로 복사 붙여넣기를 한 후 이동한다. 

그러고 나서, 이동한 후 해당 폴더에서 파일을 우측 클릭한 후 파일 열기에서 Realm Studio로 파일을 열어준다. 

Realm Studio의 내가 만든 저장 공간이 잘 생성되었는지 확인한다.

```swift

func getDogList() {
        savedList = []
				// 함수내에서 빈 배열로 지정
        let dog = localRealm.objects(Dog.self)
        // 모든 객체 얻기
        print(dog)
        
        for dangdang in dog {
            savedList.append("\(dangdang.name), \(dangdang.age), \(dangdang.breed)")
						// 배열에 해당 객체들을 추가해준다.
        }
        
        myLabel.text = savedList.joined()
				// 배열에 저장된 내용들을 myLabe에 보여준다. 
    }
    
```

```swift

@IBAction func saveButton(_ sender: UIButton) {
        let name = nameTextField.text ?? "비어 있음"
        let breed = breedTextField.text ?? "비어 있음"
        let age = Int(ageTextField.text!) ?? 0
				// textField를 통해 생성해낸 3가지 내용들을 각각의 상수에 담아준다
        
        let dog = Dog(name: name, breed: breed, age: age)
			
        try! localRealm.write {
            localRealm.add(dog)
        }
        // 내가 만든 Realm에 dog 객체를 추가

        getDogList()
				// 위에서 만든 함수를 실행 
    }

```

<img width="1440" alt="스크린샷 2023-02-13 오후 7 54 14" src="https://user-images.githubusercontent.com/99719661/218769554-cd3efbc1-f639-4b57-a99f-a73b5a69b0be.png">

Realm에도 저장한 정보가 잘 들어갔는지 확인할 수 있었다. 

```swift

let dog = localRealm.objects(Dog.self)
// 모든 객체 얻기

print(dog)

```

<img width="348" alt="스크린샷 2023-02-13 오후 7 56 26" src="https://user-images.githubusercontent.com/99719661/218769718-a56fdd35-a5d0-4894-a08f-ef68611a1fd0.png">

모든 객체가 들어간 dog를 프린트하여 본 결과, id 번호 0번, 1번 순서대로 내용이 잘 저장된 것을 확인하였다.   

**내용 업데이트하는 방법**

```swift

if let update = localRealm.objects(Dog.self).filter(NSPredicate(format: "name = %@", nameTextField.text ?? "")).first {
            try! localRealm.write {
                update.name = "브로야"
            }
        }
        
```

저장된 내용중에 nameTextField에 입력한 내용(이름)이 첫번째로 저장된 객체의 name과 같으면   

해당 이름을 “브로야”로 업데이트 한다.    

내용을 업데이트 하고 싶을 때는 NSPredicate를 사용한다.   




