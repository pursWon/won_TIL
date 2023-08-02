UserDefaults의 응용
=================

사용자 정의 타입 저장하고 가져오기

</br>

구조체 같은 사용자 정의 타입은 UserDefaults에 바로 저장할 수 없다.

</br>

구조체를 Data 형으로 변경하여 UserDefaults에 저장해야 한다.

</br>

객체를 Data 형과 같이 Byte 형태로 변경하는 작업을 아카이빙이라고 한다.

</br>

반대로 메모리, 디스크에 저장된 Data 형태의 바이트를 구조체와 같은 객체로 바꾸는 것을

</br>

언아카이빙이라고 한다. 구조체를 UserDefaults에서 읽기 위해서는

</br>

언카이빙 과정이 필요하다.

</br>

먼저 아카이빙 과정부터 보자.

</br>

![image](https://github.com/pursWon/won_TIL/assets/99719661/4010826f-c73c-4531-86ce-9b85ffd2b8a9)
 
</br>
 
위의 구조체의 객체가 있고 이들을

</br>

![image](https://github.com/pursWon/won_TIL/assets/99719661/322947ee-81fb-4d4a-8d4a-c40f545c72be)

</br>

JSONEncoder를 이용하여 객체를 아카이빙한다.

</br>

![image](https://github.com/pursWon/won_TIL/assets/99719661/39086c0e-71b0-4897-8ed5-da0b567e2bc0)

</br>

구조체 타입의 객체들을 encode하여 

</br>

UserDefaults에 Data 타입으로 저장한다.

</br>

이렇게 저장된 구조체 데이터를 다시 가져오려면, 반대로 decode를 해주면 된다.

 ![image](https://github.com/pursWon/won_TIL/assets/99719661/2dcb067e-b185-43ad-bbba-5ed62ae77eb9)

</br>

값이 잘 출력되는 것을 확인할 수 있다.

 
</br>
 

 

UserDefaults를 저장하고 꺼내는 방법에 대해서 알았지만,

 

 </br>

 

해당 데이터들이 저장되는 공간은 어디일까?

 

</br> 

 

UserDefaults의 내용은 plist 형식의 파일로 저장되며 OS에 따라 저장되는

 
</br>
 

 

위치가 달라진다. iOS의 경우 탐색이 불가능하므로 정확히 어떤 경로에 저장되는지는 모른다.

 

 </br>

 

시뮬레이터의 경우 /Library/Developer/CoreSimulator에서 시뮬레이터 plist를 확인하면 된다!

 </br>
 
![image](https://github.com/pursWon/won_TIL/assets/99719661/1358ead1-27fd-44d6-8299-1627ebddfb0b)

 </br>

 위의 코드를 이용하여 정확한 경로도 찾을 수 있다.

  </br>

 

 

UserDefaults는 메모리 상에서 모든 데이터를 관리할 수 있고, 저장할 수 있다는 

 
 </br>
 

 

장점이 존재하지만, 대규모 데이터를 저장하기에는 알맞지 않다.

 

  </br>

 

그 이유는 앱을 실행할 때마다 UserDefaults가 대규모 데이터를 메모리에 

 

  </br>

 

올리기 때문에 앱 성능이 나빠질 수도 있기 때문이다.






