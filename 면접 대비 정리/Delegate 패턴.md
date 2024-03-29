Delegate 패턴
=====

### Delegate 패턴에 대하여 

**1차 답변** : 이벤트를 알려주는 객체와 해당 이벤트를 처리할 객체가 서로 다를 경우, 주로 Delegate 패턴을 사용하게 됩니다. 한 객체가 모든 일을 처리하는 것이 아닌 

할 일의 일부를 다른 객체에게 넘겨주는 것입니다. 

**2차 답변** : **Delegate 패턴**의 장점은 다음과 같습니다.

첫번째, 프로토콜에 필요한 메서드를 정확히 명시할 수 있습니다. 

두번째, 로직의 흐름을 따라가기 쉽습니다. 

세번째, 프로토콜을 Delegate 패턴과 사용하게 되면 코드의 재사용성이 높아져 코드가 유연해지게 됩니다. 

**Delegate 패턴의 단점**은 다음과 같습니다. 

첫번째, 많은 코드 라인의 수가 필요합니다. 

두번째, 객체가 많을 경우 이벤트를 알려주는 것이 어렵고 비효율적입니다. 

</br>

**Delegate 패턴의 사용 방법**입니다. 

1. 프로토콜을 선언합니다.

2. 프로토콜 내부에 메서드 혹은 변수를 선언합니다.     

3. vc.delegate = self 처럼 프로토콜을 준수합니다. (해당 예시는 vc에서 준수)    

4. vc에서 프로토콜을 준수했으므로 프로토콜내의 메서드를 정의할 수 있습니다.     

5. 정의된 메서드를 사용하고 재사용도 할 수 있습니다.       
