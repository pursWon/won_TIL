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



















