RGB로 색 지정 
=====

지정색에는 없는 버건디색을 가져오고 싶어서 RGB를 이용하였다. 

<img width="228" alt="스크린샷 2022-12-01 오후 3 42 02" src="https://user-images.githubusercontent.com/99719661/204986308-97b5fdf8-09d9-4b45-bc38-91ff52d7ed90.png">

RGB에 적혀있는 값을 가져오면 되는데 이 때, 각각의 값을 255.0으로 나눠줘야 한다. 그리고 alpha는 1.0으로 지정.

```swift

let color = UIColor(red: 117/255.0, green: 18/255.0, blue: 54/255.0, alpha: 1.0)

```























