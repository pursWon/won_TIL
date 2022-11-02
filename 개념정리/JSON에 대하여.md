JSON에 대하여
===

Java Script Object Notation의 약자이다.   

JSON 언어를 쉽게 정의를 내리자면, 간결하고 쉽게 데이터를 정의 내리는 방법 중의 하나.   

JSON 언어의 종류는 2가지.

(1) Json 객체

Key: Value로 이루어진 데이터들의 집합

중괄호로 시작해서 중괄호로 끝나고 Key - Value가 쌍을 이루어 들어가게 되는 것이다.   

예시 : 

```swift 
{

"name": "Hong WonGi"

}

```

Key - Value 값을 더 추가해주고 싶으면, ,(comma)를 이용하면 된다.   

```swift 

{

"name": "Hong WonGi"
"age": "28"

}

```

JSON 객체는 Swift의 Dictionary의 성격을 가지고 있으므로 

Swift에서는 이 JSON 객체를 다룰 때에는 

Dictionary 계열의 자료형을 사용한다. 따라서, 배열과 달리 Index가 

상관이 없으므로 Value에 맞는 Key 값만 잘 맞으면 되므로 JSON 객체의 순서는 상관이 없다. 

다만, JSON 객체에서의 Key - Value는 정해진 타입이 존재한다. 

Key 값은 오직 문자열 값만이 들어갈 수 있고, Value 값은 문자열, 숫자, 논리값, 배열, JSON 객체, NULL이 들어갈 수 있다. 

JSON 객체가 Value 값에 들어갈 때 :   

```swift 
{

"name": "Hong Wongi"

"age" : {
"20대 후반"
}

}
```

JSON 객체의 배열

```swift 

[

{
"name": "Hong"
"age": "28"
}

{
"name": "Lee"
"age": "29"
}
]
```
