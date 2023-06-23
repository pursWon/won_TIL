Moya에 대해서 알아보자
================

오늘은 라이브러리 Moya 사용법에 대해서 알아보자.

</br>


일단 늘 하던대로 공식문서를 먼저 보면


</br>


**Moya의 공식 문서 설명글**


</br></br>


![image](https://github.com/pursWon/won_TIL/assets/99719661/9b6d677f-835e-483d-865d-93c01d7a3b27)


</br></br>


데이터 통신을 하기위해 Swift에서 기본적으로 제공되는 기능은 URLSession이다.

</br>


하지만, URLSession은 사용이 복잡하고 코드의 가독성이 좋지 않아서 Foundation Networking을 

</br>



기반으로한 인터페이스를 제공해서 네트워킹 작업을 단순화 해주는 라이브러리인 Alamofire를 

</br>


흔히들 많이 사용한다. 하지만, Alamofire는 유지보수와 유닛 테스트가 힘들다는 단점이 존재한다.

</br>


그래서! 등장한 Moya는 URLSession을 추상화한 Alamofire를 다시 추상화해서 프레임워크로

</br>

Network Layer를 템플릿화해서 재사용성을 높이고

</br>


사용자가 request와 response에만 신경을 쓰도록  해주게 만들었다.

</br></br>


![image](https://github.com/pursWon/won_TIL/assets/99719661/dff5d80c-de9a-4f1f-aaf6-8c8c83be6848)


</br></br>


위의 그림을 보면 네트워크 계층이 복잡하지 않고 깔끔하게 한 줄로 정리된 것을 확인할 수 있다.

</br></br>


## Moya 사용법


</br></br>


(1)

</br>

Moya를 설치한다.

</br>

모든 라이브러리가 그렇듯, 설치를 먼저 해줘야한다.



</br>



CocoaPods를 이용하거나, Swift Package Manager를 사용하면 된다.



</br>



나 같은 경우는, Swift Package Manager를 사용하였다.



</br></br>


![image](https://github.com/pursWon/won_TIL/assets/99719661/44581ec9-6134-42e0-8548-22ad07015a10)


</br></br>


File -> Add Packages 순으로 들어간 후

</br>

https://github.com/Moya/Moya﻿

</br>



위의 사이트를 위 사진의 빨강 네모칸에 입력하면

</br>



위와 같이 Moya 라이브러리가 나오게 되고 Add Package 버튼을 눌러 각자의 프로젝트에 



</br>



추가해주면 된다.



</br></br>



(2)

</br>

Enum을 사용하여 사용할 API 목록을 작성해준다.

</br></br>

![image](https://github.com/pursWon/won_TIL/assets/99719661/ff0964d9-657e-44df-9fb3-03b49ab0d5e5)




</br></br>




난 GitHub에서 유저를 검색하는 API를 사용할 것이므로 searchUser로 지어주었다.


</br>


(3)

</br>

Target Type 작성

</br>


Enum으로 작성한 API 목록을 extension할 예정인데, Target Type 프로토콜을 Confirm하여 

</br>

API 별로 request에 필요한 것들을 지정할 수 있다.



</br>





Target Type의 종류


</br>


- baseURL : Server base의 UR을 지정


</br>


- path : API Path를 지정 


</br>


- method : HTTP Method 지정

</br>



- sampleData : Mock Data for Test


</br>


- task : Parameters for request 지정


</br>


- validationType : 허용할 response를 정의


</br>


- headers : HTTP headers 적용



</br>



내가 Target Tyep들을 적을 때에는 sampleData와 validationType은 




</br>


필요하지 않아서 적지 않았다.

</br></br>

![image](https://github.com/pursWon/won_TIL/assets/99719661/69aee76a-fe2c-4a29-ae5f-6c08a3fab7ba)


</br></br>



(4)


</br>


Response Struct 생성 


</br>




API 데이터 통신을 해서 데이터를 받아왔으면



</br>



항상 그래왔던 것처럼, response를 저장한 구조체를 만들어준다.

</br></br>

![image](https://github.com/pursWon/won_TIL/assets/99719661/f3e1404a-408e-47e2-80e6-bbfdb3a7b178)

</br></br>



Data를 받아올 Model



</br></br>


(5)



</br>

Moya Provider를 이용한 네트워크 요청



</br>



네트워크 요청을 수행할 Moya Provider 인스턴스를 생성



</br>






Moya Provider는 Target Type 프로토콜을 준수하는 Enum을 받고 있다. 

</br></br>

![image](https://github.com/pursWon/won_TIL/assets/99719661/6d5564d3-fbf1-4a5a-8304-ba8754504d7e)

</br></br>


생성한 Provider를 통해서 request를 요청할 수 있다.


</br>




provider의 request의 파리미터로 아까 만든 Target Type을 전달한다.



</br>



Decoding을 실패하거나 데이터 통신을 실패했을 경우엔,

</br>





error의 localizedDescription 문을 통해서 error가 발생했다는 것을 알려주게끔 설정하였다.





</br></br>



(6)


</br>


Data가 잘 들어오는지 확인.

</br></br>

![image](https://github.com/pursWon/won_TIL/assets/99719661/e3223538-96c9-4592-8e60-101c696d6554)

</br></br>

![image](https://github.com/pursWon/won_TIL/assets/99719661/1b9a1aef-c2bd-4e1d-b8c7-654990afb4b4)













Moya를 이용한 API 통신을 하여 Data가 잘 들어오는 것을 확인하였다.



