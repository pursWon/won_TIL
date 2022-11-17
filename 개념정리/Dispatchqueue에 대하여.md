Dispatchqueue에 대하여
===

Grand Central Dispatch (GCD) dispatch queues는 task 수행을 위한 강력한 도구입니다. Dispatch Queues를 사용하면 호출자(caller)와 관련하여 비동기/동기식으로 임의의 코드 블록을 수행 할 수 있습니다. Dispatch Queues를 사용하여 별도의 쓰레드에서 수행하는 거의 모든 task를 수행 할 수 있습니다. dispatch queues의 장점은 사용하기 쉽고, 해당 쓰레드 코드보다 해당 task를 실행 할 때 훨씬 효율적이라는 것이다. 이 챕터에서는 dispatch queues를 사용하여 앱에서 일반 task를 실행하는 방법에 대한 정보를 제공한다.

**DispatchQueue**를 쉽게 요약하자면?

앱에서 task를 비동기적으로 동시에 수행할 수 있는 손쉬운 방법이다. task는 앱이 수행해야 하는 작업이다. 예를 들어, 일부 계산을 수행하거나 데이터 구조를 작성 또는 수정하고 파일에서 읽은 일부 데이터를 처리하거나 여러가지 task를 정의할 수 있다. 

**DispatchQueue**의 종류 3가지

1. **Serial** 

Serial queues는 큐에 추가된 순서대로 한번에 하나의 task를 실행한다. 현재 실행중인 task는 dispatch queues에서 관리하는 고유한 스레드에서 실행된다. 필요한 만큼 Serial queues를 작성 할 수 있으며, 각 큐는 다른 모든 큐와 관련하여 동시에 작동한다. Serial Queues을 4개 작성하게 되면 최대 4개의 taskr가 각 큐에서 동시에 실행될 수 있다. 

2. **Concurrent** 

Concurrent queues(일종의 global dispatch queue라고도 알려진)은 동시에 하나 이상의 task를 실행하지만 task는 큐에 추가된 순서대로 게속 시작됩니다. 현재 실행중인 task는 dispatch queue에서 관리하는 고유한 쓰레드에서 실행됩니다. 특정 시점에서 실행되는 정확한 task의 수는 가변적이며 시스템 조건에 따라 다릅니다. iOS 5이상에서는 큐의 타입으로 DISPATCH_QUEUE_CONCURRENT를 지정하여 사용자가 동시에 dispatch queue을 생성 할 수 있습니다. 또한 앱에 사용할 사전에 정의된 global concurrent queues가 4개 있습니다.

3. **Main dispatch queue**

main dispatch queue는 앱의 main 쓰레드에서 task를 실행하는, 전역적으로 사용 가능한 serial queue입니다. 이 큐는 앱의 실행루프와 함께 작동하여 큐에 있는 task의 실행을 실행루프에 연결된 다른 이벤트 소스의 실행과 얽힙니다. 앱의 main쓰레드에서 실행되므로, main queue는 종종 앱의 주요 동기화 지점으로 사용됩니다. main dispatch queue를 만들 필요는 없지만, 앱이 적절하게 배수(drains)되도록 해야합니다.

**Queue**는 선입선출의 구조를 가지고 있다. 

Queue가 Serial Dispatch Queue는 task들을 넣으면 한 task가 끝나야지 다음 task를 한다.

Cocurrent Dispatch Queue에 task들을 넣으면 앞의 task의 완료 여부에 상관없이 동시에 task를 진행하게 된다. 

qos(Quality of service)는 중요도이다. Qos (Quality of Service) class는 DispatchQueue에서 수행할 작업을 분류한다. 작동시킬 Qos를 지정함으로써 중요도를 정하고, 시스템이 우선순위를 정하고 이에 따라 스케쥴링을 정한다. 우선순위가 높은 작업은 우선순위가 낮은 작업보다 더 빨리 수행되고, 리소스가 많으므로 일반적으로 우선순위가 낮은 작업보다 더 많은 에너지가 필요한다.

DispatchQueue는 이렇게 쓸 수 있다.

```swift

DispatchQueue.global(qos: .background).async {


    //code

 
}
```

내가 스스로 큐를 만들어낼 수 있다.   

```swift
let Queue = DispatchQueue(label: "Wongi")
```

여기에 attributes를 주지 않으면 해당 큐는 Serial Queue가 된다.     

```swift

let Queue = DispatchQueue(label: "Wongi", attributes: .cocurrent)

```

명시적으로 지정을 해줘야 concurrent queue가 된다.    

**sync** : 큐에 작업을 추가해주고, 끝날때까지 기다리면 된다.      

**async**: 일단 큐에 작업을 추가해주고, 기다리는 것 없이 다른 작업을 시행하면 된다.      

sync로 만들었으니, global 큐가 끝날 때까지는 다른 작업을 하지 않는다.    

```swift

DispatchQueue.global().sync {



    for i in 1...5 {



        print(i)
    }



    print("==================")
}



for i in 100...105 {



    print(i)
}

```
→ 결과 

1

2

3

4

5

==================

100

101

102

103

104

105

```swift

let zeddQueue = DispatchQueue(label: "zedd")



zeddQueue.sync {



    for i in 1...5 {



        print(i)



    }
    print("==================")



}


for i in 100...105 {



    print(i)
}
```

결과는 위와 같다.

```swift

DispatchQueue.global().async {



    for i in 1...5 {



        print("\(i)🐶")
    }



    print("==================")
}



DispatchQueue.global().async {



    for i in 200...205 {



        print("\(i)😍")
    }



    print("==================")
}

for i in 100...105 {



    print("\(i)👻")
}
```

결과는 매번 실행할 때마다 다르다. 그 이유는 async는 완료 여부와 상관없이 다음 코드를 실행하기 때문이다. cocurrent이므로 🐶가 끝나지 않아도 😍가 실행될 수 있는 것이다.     

Serial에 async를 하면 어떻게 될까?    

```swift

let zeddQueue = DispatchQueue(label: "zedd")

zeddQueue.async {



    for i in 1...5 {

        print("\(i)🐶")
    }

    print("==================")
}



zeddQueue.async {

    for i in 200...205 {

        print("\(i)😍")
    }



    print("==================")
}


for i in 100...105 {

    print("\(i)👻")
}

```

결과는 

100👻

101👻

1🐶

2🐶

3🐶

102👻

4🐶

5🐶

======================

103👻

200😍

104👻

201😍

105👻

202😍

👻은 무작위로 나오지만 (큐 안에 들어가 있지 않으므로) 큐안에 들어가있는 🐶와 😍는 Serial 규칙에 의하여 🐶가 끝나야 😍가 나올 수 있다.    












