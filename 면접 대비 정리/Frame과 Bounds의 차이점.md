Frame과 Bounds의 차이점
=============

**Frame**은    
상위 뷰의 좌표시스템 안에서 View의 위치와 크기를 나타냅니다.      
superView, subView, imageView 순으로 있을 경우 frame에서는 subView의 상위 뷰인 superView의 origin으로부터 떨어진 곳에 subView를 그려주게 되고,      
imageView의 경우, imageView의 상위 뷰인 subView의 origin으로부터 떨어진 곳에 imageView를 그려주게 됩니다.    

**Bounds**는    
자신만의 좌표시스템 안에서 View의 위치와 크기를 나타냅니다.      
subView의 origin을 변경했을 경우에.     
subView는 움직이지 않고 오히려 imageView가 움직이게 되는데, 이는 subView가 위치를 바꿈으로써 imageView가 움직이는 것처럼 보이게는 원리를 가지기 때문입니다.      
이는 우리가 폰을 사용할 때에 많이 쓰는 Scroll View와 같은 원리를 가지는데,     
우리가 보는 물체가 움직이는 것처럼 보이지만 사실 ScorllView의 Bounds의 origin이 변경되었기 때문입니다.     

<img width="313" alt="스크린샷 2022-12-23 오후 11 14 27" src="https://user-images.githubusercontent.com/99719661/209351144-5d27662c-81b4-4161-b378-c4554af9b0b0.png">

**Bounds**에서는 기준이 자신의 orgin이 좌표이므로 해당 모양을 회전시켜도 본인의 크기와 좌표를 유지하게 도됩니다. 

<img width="313" alt="스크린샷 2022-12-23 오후 11 14 49" src="https://user-images.githubusercontent.com/99719661/209362680-3cd268d3-768a-4e9e-ab10-f502fca9ee3e.png">

**Frame**에서는 이렇게 뷰가 회전했을 때 Frame은 뷰를 감싸고 있는 사각형이므로 해당 모양에 맞게끔 변하게 됩니다. 













