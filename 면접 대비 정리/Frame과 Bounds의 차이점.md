Frame과 Bounds의 차이점
=============

**Frame**은    

상위 뷰의 좌표시스템 안에서 View의 위치와 크기를 나타냅니다.      
 
superView, subView, imageView 순으로 있을 경우 frame에서는 subView의 상위 뷰인 superView의 origin으로부터 떨어진 곳에 subView를 그려주게 되고,      

imageView의 경우, imageView의 상위 뷰인 subView의 origin으로부터 떨어진 곳에 imageView를 그려주게 됩니다.    





















