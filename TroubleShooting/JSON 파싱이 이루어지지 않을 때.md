 JSON 파싱이 이루어지지 않을 때
 ===================
 
**Unsplash**에 있는 이미지 목록을 불러올 예정이었다.   

데이터 통신을 통하여  이미지 목록을 불러올 것이었기 때문에    

JSON 형태로 주어진 데이터에 맞게끔 Model을 만들고 주어진 방법에   

맞게끔 통신을 해야했다.       

</br>

![image](https://github.com/pursWon/won_TIL/assets/99719661/77ee1c91-da90-4a45-931e-a6e0d1737359)

</br></br>

![image](https://github.com/pursWon/won_TIL/assets/99719661/90417a13-fb5b-47d2-a203-39748d8cf80d)

</br></br>

![image](https://github.com/pursWon/won_TIL/assets/99719661/003bd81c-94dc-46c7-98ce-2e5442a8b101)

</br></br>

홈페이지에서 주어진 설명대로 method는 GET으로 설정하였고, parameter는 따로 만들지 않고 위처럼 URL에 같이 넣어주었다.   

필요한 parameter는 나의 API key이고 옵션값을 가지는 parameter는 page와 per_page이다.    

설명이 적혀진 문서에 있는대로 데이터 통신 준비를 마쳤다고 생각하여 실행을 눌러본 결과, 무언가 잘못 설정을 하였는지 데이터 통신에.  

실패했다고 나오게 되었다. (흑흑).  

아는 분의 헬프로 문제점을 찾게 되었는데... 예상치 못하게도 model에서 문제점을 찾게 되었다.    

일단 다시 설정해야 하는 JSON 형태의 Response를 보면.  

</br>

![image](https://github.com/pursWon/won_TIL/assets/99719661/ff7ae7ac-3a66-452f-a8f9-cb1254dd3bd7)

이와 같이 되어있다. 그런데 내가 설정한 model과는 차이점이 있었던 것이다.   

위의 형태에선 배열에 이름을 따로 지정해준 것이 없고 배열내의 멤버들만 이름이 존재한다.   

하지만, 내가 지정해준 model에선?    

</br></br>

![image](https://github.com/pursWon/won_TIL/assets/99719661/6b76f601-c4c6-4101-afaf-6b7cc6a16892)

</br>

배열의 이름을 지정해준 data라는 상수가 존재한다.    

즉, JSON 데이터 파싱이 이루어지지 않은 이유는 reponse로 들어오는 JSON형식과 다른 형태를 내가 임의로 만들어줬기 때문이다.   

그렇다면, 파싱이 이루어지려면 멤버들의 이름만 지정을 해준 후, 해당 구조체를 배열로 감싼 형태를 decoding을 해주면 된다.     

decoding이 이루어진 model의 최종 형태가 주어진 JSON 데이터 형식과 일치하면 되는 것이다.   



안타깝게도, 과거에 내가 했던 프로젝트와 위와 같은 파싱을 했었다..   

까먹지 않게끔 다시 기록해놓고 꼭 위와 같은 실수를 저지르지 말자..   

</br>

![image](https://github.com/pursWon/won_TIL/assets/99719661/89238cf2-4d64-401b-8803-a07b177a6d9d)

</br></br>

해당 Model도 마찬가지로 안의 멤버만 이름이 지정되어있어야 하고 배열의 이름은 따로 없고 배열로 감싸져야 하는 형태였다. 

![image](https://github.com/pursWon/won_TIL/assets/99719661/fabae13f-d551-4824-a8f5-5cc0fd979d51)

바로 위의 사진과 마찬가지로 배열로 감싸주면 해결되는 문제였기에 Unsplash 이미지를 불러오는 model에서도 배열을 이름을 따로 지정해주지 않고 멤버들의      
이름을 지정해준 후 decoding을 할 때, 배열로 감싸주면 해결될 문제인 것이다.   

</br></br>

![image](https://github.com/pursWon/won_TIL/assets/99719661/821c9615-d3db-43b0-b1d2-196469d8e4c2)

</br>

![image](https://github.com/pursWon/won_TIL/assets/99719661/311915f3-c79f-4d8b-b05a-249042e216c9)

</br>

이렇게 설정하니 데이터 통신이 잘되는 것을 확인하였다. 👍👍✅✔️      












