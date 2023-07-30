Userdefaults에 대하여
================

![image](https://github.com/pursWon/won_TIL/assets/99719661/dd78b44b-e3f0-4713-9c95-4beaa4d5ca93)

앱 실행 시 지속적으로 Key - Value 쌍을 저장하는 사용자의

</br>

기본 데이터베이스에 대한 인터페이스이다.

</br>

UserDefaults는 복잡하고 큰 용량의 데이터 보다는 간단한 데이터 저장에 적합하다.

</br>

앱이 삭제되면 UserDefaults 데이터도 함께 삭제되므로

</br>

데이터가 영구히 유지되어야 한다면 UserDefaults는 부적합할 수 있다.

</br>

UserDefaults의 Key - Value 쌍에서 Key는 String 타입이고, 

</br>

Value는 모든 객체를 담을 수 있다.

</br>

UserDefaults의 기본적인 개념에 대해서 알았으니,

</br>

UserDefaults의 사용 방법에 대해서도 알아보자

</br>

## 데이터 저장하기

![image](https://github.com/pursWon/won_TIL/assets/99719661/32589d68-9889-4b2e-8efa-aa5b77e24327)

Set 메서드를 사용해서 값을 저장할 수 있다.

</br>

UserDefaults에 저장한 값을 값을 덮어쓰지 않는 이상 

</br>

변하지 않습니다.

</br>

위의 코드처럼 기존의 값인 4 대신에 44로 변경시켜도

</br>

UserDefaults가 가지고 있는 값은 4 그대로이다.

</br>

데이터 변경을 원한다면 Set 메서드를 통해서 다시 데이터 저장을 해야한다.

## 데이터 삭제하기

UserDefaults의 데이터는 removeObject(forKey:)를 이용하면 간단하게 삭제할 수 있다.

</br>

![image](https://github.com/pursWon/won_TIL/assets/99719661/1a165639-c7ae-4042-b41a-400a653a3675)

11을 세팅한 후 값을 출력하면 저장한 11이 출력되지만,

</br>

removeObject(forKey:)를 이용해 eleven 키의 데이터를 삭제하고

</br>

값을 출력하면 기본값인 0이 출력된다.

## 기본값 설정 

데이터를 불러올 때 값이 없을 수 있다.

</br>

Key의 값을 저장하지 않고 값을 가져오면 기본값이 0으로 읽힌다.

</br>

Inf, Float, Double은 0, Bool은 false이다.

</br>

return 타입이 옵셔널일 때는 기본값이 없는 것으로

</br>

저장하지 않고 값을 읽으면 nil로 읽히게 된다.

</br>

그래서, 매번 값을 안전하게 가져오려면 

</br>

옵셔널 바인딩을 해야 한다는 불편함이 존재한다.

</br>

이를 해결하기 위해선, register(defaultes:)를 이용해 각 키의 기본값을

</br>

설정할 수 있다. 사용 방법은 인자로 [Key : Value] 쌍을 전달하면 된다.

</br>

![image](https://github.com/pursWon/won_TIL/assets/99719661/27d33687-7ab1-4fcf-ae88-9893cb9830c2)

register를 이용해서 

</br>

이런 식으로 기본값을 지정해줄 수 있다.

</br>

다음 글에서는 구조체 같은 사용자 정의 타입을 아카이빙하여 

</br>

저장하는 방법에 대해서 알아보겠다.


 
