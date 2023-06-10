DispatchQueue에 대하여
=======================


![스크린샷 2023-06-09 오후 3 03 16](https://github.com/pursWon/AboutRamen/assets/99719661/e46fb288-e365-4b3a-9c33-b6852bd6f6c0)

DispatchQueue의 사전적 정의를 보자면,    
 
Main Thread 혹은 Background Thread에서 concurrent 혹은 serial 하게 실행되는 작업을 관리하는 객체이다.   

## DispatchQueue의 종류
 
**Main - Serial**
**Main - Concurrent**
**Background - Serial**
**Background - Serial**

![스크린샷 2023-06-09 오후 3 13 43](https://github.com/pursWon/AboutRamen/assets/99719661/318cd85c-2277-4f65-af19-3423fa22625f)

DispatchQueue의 개념 설명에 대해서 보자면
 
FIFO 구조이고, 주어진 코드 블록안에 있는 

작업들을 어플리케이션에게 제출한다.

작업을 concurrent 혹은 serial 하게 실행한다

시스템에 의해 관리되고 있는 thread가 모여있는 pool에서

DispatchQueue에 의해 작업이 실행한다.

당신의 앱의 Main Thread를 (대표하는 DispatchQueue를) 제외하고,  

시스템은 어떤 thread가 무슨 작업을 하는지 보장할 수 없다.    

당신이 동기적으로 작업을 스케쥴 했을 때,   

당신의 코드는 아이템의 실행이 끌날 때까지 기다릴 것이다.   

당신이 비동기적으로 작업을 스케쥴 했을 때,   

당신의 코드는 아이템이 실행되는 동안 연속적으로 실행된다.   

⚠️ Main queue에서 동기적으로 작업을 시도할 경우에 deadlock에 걸릴 수 있다.   

여기서, **Deadlock**이란 무엇인가?

![dead lock](https://github.com/pursWon/AboutRamen/assets/99719661/69cfcd3c-5304-4b6e-bdf4-6113e442ed60)

위의 사진은 차가 양보없이 서로 직진만 하겠다고 하다가     
 
꼬여서 모두 이도저도 못하고 있는 상태를 보여주고 있다.   
 
마치 Deadlock처럼 말이다.   
 
Deadlock의 정의를 살펴보자면,   
 
시스템 자원에 대한 요구가 뒤엉킨 상태이다.   
 
즉, 둘 이상의 Process가 다른 Process가 점유하고 있는 자원을 서로 기다릴 때 무한 대기에   
 
빠지는 상황을 일컫는다.   
 
발생되는 상황을 예시로 하나 들자면.  

Deadlock의 발생조건은 총 4가지가 있다.       

## DispatchQueue의 사용 방법
 
**1. Sync + Serial**
 
메인 Thread의 작업 흐름이 Queue에 넘긴 task가 끝날 때까지 멈춰있고(sync), 넘겨진 task는 queue에 먼저 담겨있던
 
작업들과 같은 Thread에 보내지기 때문에 해당 작업들이 모두 끝나야 실행(Serial Queue)

```swift 

import Foundation

DispatchQueue.global().sync {
    
    for i in 1...3 {
        print(i)
    }
    print("==================")
}

for j in 10...14 {
    print(j)
}

```

![스크린샷 2023-06-09 오후 4 21 28](https://github.com/pursWon/AboutRamen/assets/99719661/15a6aeab-22ba-4b6f-90c5-35a898d1e6f0)

순차적으로 처리하기 때문에
 
결과는 위와 동일하다.

**2. Async + Serial**   

Main Thread의 작업 흐름이 queue에 넘기자마자 반환되고(async),   
 
넘겨진 task는 queue에 먼저 담겨있던 작업들과 
 
같은 thread에 보내지므로 해당 작업들이 모두 끝나야 실행.    

```swift 

DispatchQueue.global().async {
    
    for i in 1...3 {
        print(i)
    }
    
    print("==================")
}

for j in 10...14 {
    print(j)
}

```

![스크린샷 2023-06-09 오후 4 35 40](https://github.com/pursWon/AboutRamen/assets/99719661/138b4675-e150-4285-95c3-d38eed600ce0)

결과는 매번 실행때마다 다르다.   
 
왜냐면 async는 완료 여부에 상관없이 다음 코드를 실행하기 때문이다.   
 
**3. Sync + Concurrent**

Main Thread의 작업 흐름이 queue에 넘긴 task가 끝날때까지 멈춰있고(sync),   
 
넘겨진 task는 queue에 먼저 담겨있던 작업들과 다른 thread에     
 
보내질 수 있으므로 해당 작업들이 모두 끝나지 않아도 실행       

```swift 

let customQueue = DispatchQueue(label: "cus")

customQueue.sync {
    
    for i in 1...5 {
        print("\(i)🐶")
    }
    
    print("==================")
}

customQueue.sync {
    
    for i in 30...33 {
        print("\(i)😍")
    }
    
    print("==================")
}

for i in 100...105 {
    
    print("\(i)👻")
}

```

작업이 끝날 때까지 대기하면서, Queue에 등록되는 작업들은 여러 스레드에 분산되어 처리된다.    

![스크린샷 2023-06-09 오후 5 12 30](https://github.com/pursWon/AboutRamen/assets/99719661/def6e74a-3ee9-4b04-83f8-6e3efb47c57e)

결과물은 다음과 같이 나온다.


4. **Async + Concurrent**      
 
Main Thread의 작업 흐름이 task를 queue에 넘기자마자 반환되고(async), 넘겨진 task는 queue에      
 
먼저 담겨있던 작업들과 다른 thread에 보내질 수 있으므로 해당 작업들이      
  
모두 끝나지 않아도 실행        

```swift 

let customQueue = DispatchQueue(label: "cus")

customQueue.async {
    
    for i in 1...5 {
        print("\(i)🐶")
    }
    
    print("==================")
}
customQueue.async {
    
    for i in 30...33 {
        print("\(i)😍")
    }
    
    print("==================")
}

for i in 100...105 {
    
    print("\(i)👻")
}

```

![스크린샷 2023-06-09 오후 5 11 16](https://github.com/pursWon/AboutRamen/assets/99719661/7a45d80b-4b2e-4b6a-9ed6-1a8548c73b1a)

결과는 위와 같다.    







