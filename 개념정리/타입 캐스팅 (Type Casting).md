타입 캐스팅 (Type Casting)
===

타입 캐스팅은 해당 인스턴스의 타입을 확인하거나, 해당 인스턴스를 하위 클래스, 슈퍼 클래스로 만드는 방법이다.       
타입 캐스팅은 swift에서 is, as 로 구분하며 해당 타입이 프로토콜에 적합한지도 알 수 있다.     

(1) is의 타입 캐스팅 
---

타입을 체크하는 연산자로, 반환값은 Bool 타입이다.    
내가 선언한 변수, 상수가 원하는 타입인지 확인할 때 사용할 수 있다.    

```swift
let char: Character = "B"
char is Character // true 
char is Int // false 
```
동일한 타입인지 확인할 때 쓰지만 type의 서브 클래스일 때도 true를 반환한다.

```swift
class Human {}
class Teacher {}

let teacher: Teacher = .init()
teacher is Teacher // true
teacher is Human // true
```

이렇게 Human 클래스를 Teacher 클래스가 상속받게 되면, teacher 인스턴스는 Human 클래스의 서브 클래스 가 된다.     
이런 경우에는 teacher를 Human으로 타입 체크를 해도 True가 된다.     

(2) as 의 타입 캐스팅
---

서브 클래스의 인스턴스를 슈퍼 클래스의 인스턴스로 참조한다. 업 캐스팅은 항상 성공한다.

```swift
class Human {
    let name: String
    init(name: String) {
        self.name = name
    }
}
class Teacher: Human { }
class Student: Human { }
 
 
let people: [Human] = [
    Teacher.init(name: "김선생"),
    Student.init(name: "박제자"),
    Student.init(name: "유제자")
]
```

people 상수안에 Teacher, Student 2가지의 클래스가 들어갈 수 있었던 이유는 두 클래스가 가지고 있는 공통점은 부모 클래스가 Human이기 때문이다.      
이 둘을 Human이라는 슈퍼클래스로 업캐스팅해서 올릴 수 묶은 것이다.      

```swift
class School {
    let name: String = "Seocho Elementary School"
}

class Teacher: School {
    let student: String = "Won Gi"
}

let child = Teacher.init() as School // 업캐스팅. Teacher의 인스턴스를 만들었지만 School로 업캐스팅해서 child에 저장하겠다.

child.name // 접근이 가능하다.
child.student // 서브 클래스인 Teacher에는 접근을 할 수 없음.
```

Teacher의 인스턴스를 만들었지만 child 상수를 school로 업캐스팅하여 child에 저장한다.

child 타입은 업캐스팅된 School의 타입이다. 그렇다고 School의 인스턴스들만 메모리에 올라가는 것이 아니라 Teacher 인스턴스도 메모리에 올라가게 된다.     
child가 Teacher란 서브 클래스를, School이란 슈퍼 클래스 타입으로 참조되는 업캐스팅을 한 것이므로, child의 접근 범위가 School 멤버로 한정된다.    

(3) as의 다운 캐스팅
---

슈퍼 클래스 인스턴스를 서브 클래스 타입으로 참조한다. 업캐스팅된 인스턴스를 다시 원래 서브 클래스로 참조할 때 사용한다.       
다운 캐스팅은 실패할 확률이 있으므로 as! 혹은 as?를 사용한다.      

위의 코드에서 서브 클래스의 인스턴스인 student에 접근하는 것이 불가능 했으므로 이를 다시 다운 캐스팅을 함으로써 접근할 수 있다.     

```swift
var teacher: Teacher = child as! Teacher // 변수 teacher는 서브 클래스인 Teacher로 다운 캐스팅
teacher.student // teacher 변수는 서브 클래스 Teacher의 인스턴스인 student에 접근이 가능.
```

School로 업캐스팅된 child 상수를 다시 teacher 타입으로 변환해서 넣어준 것이다.     
슈퍼 클래스인 School 클래스 타입의 인스턴스를 서브 클래스인 Teacher 타입의 인스턴스로 참조하는 것이다.    

뒤에 ?, !가 붙는 이유는 다운 캐스팅은 실패할 수 도 있기 때문인데, 예를 들어, 다른 클래스로 잘못 다운 캐스팅하여서        
오류가 생길 수도 있기 때문에 옵셔널의 형태로 다운 캐스팅을 할 수 있다.     
만약, 타입 캐스팅을 실패할 경우 nil을 반환하게 된다.     

```swift
class School {
    let name: String = "Seocho Elementary School"
}

class Teacher: School {
    let student: String = "Won Gi"
}

class Drink: School {
    let juice: String = "Delmonte"
}

let child = Teacher.init() as School // 업캐스팅. Teacher의 인스턴스를 만들었지만 School로 업캐스팅해서 child에 저장하겠다.

let child2 = child as? Teacher



if let teacher = child as? Teacher {
    print("선생님입니다.")
} else if let teacher = child as? Drink {
    print("주스입니다.")
}
```

if let 바인딩 구문을 통해 true, false 를 확인할 수 있다.
