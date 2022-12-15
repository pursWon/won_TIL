dequeueReusableCell에 대하여
=============

<img width="600" alt="스크린샷 2022-12-16 오전 12 41 19" src="https://user-images.githubusercontent.com/99719661/207918854-e4682a32-2657-4c8d-b06c-c6b02285235e.png">

위의 Developer 문서에 따른 dequeueReusableCell의 정의를 보면..

“**식별자로 찾은 재사용 가능한 셀 개체를 대기열에서 뺍니다.”**

이와 같은 문장이 의미하는 바는 

→ Table View 위로 스크롤되어 화면에서 사라지는 Cell은 Queue(큐)로 들어가서 사라지게 되고 Queue(큐)의 front에 있는 Cell이 화면 하단에서 올라와 화면에서 보여지는 Cell로 사용되게 된다. 이 메서드를 사용하는 이유는 메모리의 양을 줄이기 위함이다.  

이미 메모리가 할당된 Cell을 재사용함으로써 추가적인 메모리 손실이 없기 때문이다.    

identifier는 셀의 이름을 정한 후 지정해서 사용하게끔 할려고 identifier를 사용한다. indexPath는 셀 내에서의 위치를 파악하기 위해 사용한다.








