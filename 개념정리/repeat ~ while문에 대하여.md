repeat ~ while문에 대하여
=======================

코딩 테스트 문제에서 **repeat ~ while**문을 적용해보았다.    

```swift 

var number: Int = 10

if number != 1 {
            repeat {
                if number % 2 == 0 {
                    number = number / 2
                } else if number % 2 != 0 {
                    number = number - 1
                }
                
            } while number != 1
        }
        
```

쉽게 요약하자면 10(number)이 1이 아니라는 조건하에 짝수일 경우, 2로 나누고, 

홀수일 경우, 1을 빼는 것을 반복하는 함수이다. 

number가 1이 될때까지 반복된다.
