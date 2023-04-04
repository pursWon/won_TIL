guard문에 대하여 
=====================================

guard 문은 함수나 메서드, 반목문 등 블록 내부에 선언하게 된다. guard 구문의 기본적인 형태는 다음과 같다.

```swift
guard 조건 else {
// 조건이 false일 경우, 실행
return || throw
}
```

guard 문은 조건이 틀린 경우는 모두 버리고, 개발자가 원하는 조건만 통과시키겠다는 기능으로 사용된다. if문과의 차이점은 if문은 조건이 충족될 경우엔 ~를 해라의 실행 구문이지만,   

guard 문은 조건이 충족될 경우에만 통과시키고 아닐 경우엔 끝낸다는 의미이기 때문이다.     

따라서, guard문의 핵심은 **“조기 종료”(early exit)**이다.     

예시를 하나 들어보자.    

내가 좋아하는 팀인 토트넘이라는 팀이 있는데, 현재는 굉장히 축구를 못하는 팀이다.

어쨌거나, 이 팀이 남은 3경기에서 모두 승리를 해서 승점 9점을 따야 챔피언스리그에 간다고 하자. 

그러면 다음과 같이 작성할 수 있다. 

```swift
class Play {
    var content: Bool?
    var result: String?
}

func tottenHam(game: Play) -> String {
    if let content = game.content {
        if content {
            game.result = "승리"
            if let result = game.result {
            return result
            }
        } else {
            game.result = "패배"
            if let result = game.result {
            return result
            }
        }
    }
    
    return ""
}

let vsNewcastle = Play()
vsNewcastle.content = true

let vsWestham = Play()
vsWestham.content = false

let vsArsenal = Play()
vsArsenal.content = true

let gameResults = [tottenHam(game: vsNewcastle), tottenHam(game: vsWestham), tottenHam(game: vsArsenal)]
var points: Int = 0

gameResults.forEach{
    guard $0 == "승리" else { return }
    
    points += 3
}

if points == 9 {
    print("토트넘이 챔스로 갑니다")
} else {
    print("이딴 경기력으로 무슨 챔스냐 ㅋㅋ 해체해라")
})
}

// 결과 : 이딴 경기력으로 무슨 챔스냐 ㅋㅋ 해체해라
```

guard 문에서 $0의 값(String)이 “승리”가 아닐 경우, 조기 종료하여 배열의 다음 값으로 넘어가게 된다. 

그리고 비기거나 패배하였으므로 3점을 얻지 못하게 된다.         

“승리”일 경우, 승점을 3점을 얻어서 points의 값은 3점을 추가하게 되고 만약 points가 9점일 경우 3승을 모두 채웠으므로 토트넘이 챔스로 가게 된다.   
