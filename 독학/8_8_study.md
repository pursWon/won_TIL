8월 8일 공부 내용 
===

함수와 메소드
--- 

func 키워드로 생성하는 모든 것은 "함수"이다.   

반면에, 클래스, 구조체, 열거형 속에 포함되어 있는 함수는 "메소드"라고 한다.   

func 키워드를 붙여서 만드는 함수들은 모두 "클로저"이다.   

다만, 이름을 붙이느냐의 유무에 따라, Named Closure 혹은 Unnamed Closure 라고 한다.    

우리는 주로 이름을 붙이는 클로저를 함수, 이름을 붙이지 않는 클로저를 클로저라고 부른다.   


```swift 
func name(parameters) -> Return Types {   

}   
```

함수 이름을 썼으면 괄호안에 원하는 파라미터를 적으면 되는 형식이다.   

이 형식은 3가지 방식이 존재한다.   


**1. Argument Label과 Parameter Name 선언하기**  

Argument Label: 함수를 선언할 때 쓰는 이름.  

Parameter Name: 함수 내에서 사용하는 파라미터 이름.    

```swift
func sayHello(to name: String) {
print ("Hi, \(name)") 
}

sayHello(name: "Wongi")
```

to가 Argument Label이다.    

name이 Parameter Name이다.    

받은 Parameter를 함수 내부에서 사용할 때 사용된다.    

함수를 호출할 때 Argument Label은 생략이 가능하다.   

```swift
func sayHello(_ name: String) {
print("Hi, \(name)")
}

sayHello("Wongi")
```

와일드카드 패턴을 이용하여 Argument Label을 생략할 수 있다.    

호출할 때도 생략하고 Parameter Name만 적으면 된다.    

Parameter Name은 당연하게도 생략이 불가능하다.    


**2. Argument Label과 Parameter Name을 한꺼번에 선언하기**

```swift 
func sayHello(name: String) {
print("Hi, \(name)")
}

sayHello(name: Wongi)
```

name이 Argument Label과 Parameter Name의 두 가지 역할 모두를 한다.    

호출할 때도, name이 Argument Label의 역할로서 쓰이게 된다.    


**3. 파라미터를 받지 않을 경우**

```swift
func sayHello() {

}
```

파라미터가 없을 경우 빈 괄호를 옆에 붙여준다.   






