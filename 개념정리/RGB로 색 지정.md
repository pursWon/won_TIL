RGB로 색 지정 
=====

지정색에는 없는 버건디색을 가져오고 싶어서 RGB를 이용하였다. 

<img width="228" alt="스크린샷 2022-12-01 오후 3 42 02" src="https://user-images.githubusercontent.com/99719661/204986308-97b5fdf8-09d9-4b45-bc38-91ff52d7ed90.png">

RGB에 적혀있는 값을 가져오면 되는데 이 때, 각각의 값을 **255.0**으로 나눠줘야 한다. 그리고 alpha는 **1.0**으로 지정.

```swift

let color = UIColor(red: 117/255.0, green: 18/255.0, blue: 54/255.0, alpha: 1.0)

```

```swift 

bar.backgroundView.style = .flat(color: color)

```
TabBar의 배경색으로 지정을 한다.           

<img width="335" alt="스크린샷 2022-12-01 오후 3 46 13" src="https://user-images.githubusercontent.com/99719661/204986890-0bc59de6-49ad-4673-aaf9-3369ef353ced.png">

보다시피 TabBar의 색이 버건디 색으로 잘 입혀졌다.       


















