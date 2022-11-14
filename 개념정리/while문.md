while문
=== 

**(1) while문**

```swift

var a: Int = 0

while a < 8 { // a가 8보다 작을 경우에만, 조건을 반복한다. 단, a가 8보다 작지 않게 될 경우, 반복을 종료한다. 

    a += 1 // a에 1을 더해준다.
    print(a) // a를 프린트 해준다.
}
```

while 문에는 거짓된 조건이 성립될 수 있게끔 적어야한다. 무조건 참인 조건이 있을 경우 무한루프에 빠지게 된다.   

결과물 :     
1   
2    
3    
4    
5    
6    
7    
8    

a를 1씩 더해주다가 a가 7일때, 7에 1을 더해주고 8을 프린팅해주고 조건문에 8을 넣었을 때, 조건문에 부합하지 않으므로

while문을 빠져나오게 된다. 

**(2) repeat while문**

```swift
var b: Int = 0

repeat {
   b += 1
   print(b)
} while b < 8
```

repeat while문에선 조건을 통과할 경우에만, 반복문이 실행이 된다. 

위의 repeat while문을 보면 처음 변수 b가 0이므로 8보다 작아야한다는 조건에 부합.

0에서 1을 더해주고 더해준 값을 프린트 해주고 b가 1이 되었을 때, 다시 조건문을 충족시키면

해당 과정을 반복해준다. 

**(3) 과제 중에 썼던 while문 예시**

```swift
 var randomColor: UIColor? = colors.randomElement()
        if let color = currentColor {
            while color == randomColor {
                randomColor = colors.randomElement()
            } else {
            currentColor = randomColor
            contentLabel.textColor = currentColor
            return
        }
        currentColor = randomColor
        contentLabel.textColor = currentColor
    }
```

거짓 조건이 될 경우 while문을 빠져나오게 하는 방법도 존재한다.

currentColor의 값은 계속해서 값이 있으므로, if let 구문에서 else 문으로 빠지지 않고 위의 분기점으로 빠지게 된다.

위의 분기점 안에 있는 while문에서 color가 randomColor와 같을 경우 (while문이 설정한 조건) -> 거짓 조건 : color가 randomColor와 다를 경우   

randomColor에 colors 배열의 멤버 중 하나를 랜덤으로 담아준다.   

그래서 다시금 조건문으로 가서 color와 randomColor를 비교해준다. 만약, 값이 또다시 같다면 다시금   

randomColor에 colors 배열의 멤버 중 하나를 랜덤으로 담아준 후 color와 randomColor를 비교해준다.   

이와 같은 과정을 끝내려면 위에서 얘기한 거짓 조건이 성립되면 while문을 나올 수 있다.   

color에 담긴 UIColor값과 randomColor의 UIColor값이 다를 경우 while문을 종료하고 나와서 

```swift
currentColor = randomColor
        contentLabel.textColor = currentColor
    }
```
해당 코드를 진행한다. 



































