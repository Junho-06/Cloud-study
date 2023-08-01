### Event Driven Architecture란
Event Driven Architecture란 이벤트의 생상, 갑지, 소비 및 반응 또는 시스템 상태의 중대한 변화를 지원하는 소프트웨어 모델 또는 아키텍처의 패러다임 입니다.  

분산 아키텍처 환경에서 이벤트를 생성하고 발행된 이벤트를 수신자에게 전송하는 구조로 수신자는 그 이벤트를 처리하는 방식으로, 상호 간 결합도를 낮추기 위해 비동기 방식으로 메시지를 전달하는 패턴 입니다.  

각 마이크로서비스는 함께 작동하지만 서로 다른 비즈니스 로직을 적용하고 자체 출력 이벤트를 보낼 수 있으며 주로 Message Broker와 결합하여 구성됩니다.  

* Event?
    * 메시지나 알림을 뜻하는 이벤트가 아닙니다.
    * 이벤트는 프로그램에 의해 감지되고 처리될 수 있는 동작인 사건을 말합니다.

### Event Driven Architecture의 필수 구성 요소
1. Event Generator  

표준화된 형식의 이벤트를 생성하고 생성된 이벤트는 Event Channel로 전송합니다.  

2. Event Channel  

이벤트를 필요로 하는 시스템까지 발송하는 역할을 수행합니다.  

3. Event Processing Engine  

수신한 이벤트를 식별/처리 하는 역할을 수행합니다.  

처리 결과에 따라 새로운 이벤트를 생성할 수 있는데 Consumer 는 이벤트의 송신자에 대한 정보를 알 필요가 없습니다.

### Event Driven Architecture의 동작 방식
1. Message  

이벤트가 생성되면 수신자에게 전달합니다.  

이벤트는 반복되어 전달되지 않으며, 수신자는 송신자의 정보를 알 필요가 없습니다.  

2. Event Source  

Event Processor에게 이벤트를 전달하는 역할입니다.  

Event Source 는 1개 이상일 수 있으며, 1개 이상의 Event Processor 에게 전달합니다.  

3. Event Processor  

수신된 이벤트에 대한 여러 action 을 수행하는 역할입니다.  

4. Event Consumer  

이벤트에 대한 처리를 합니다.  

실질적인 비즈니스 로직을 수행합니다.

### Event Driven Architecture 의 장단점
* 장점
    1. Loosely Coupling  
    분산 시스템간 느슨한 결합도를 제공합니다.

    2. 분산된 시스템간의 의존성 배제  
    약속된 메시지를 통해 통신하기 때문에 다른 시스템의 정보를 알 필요가 없습니다.  

    3. 확장성, 탄력성이 향상됩니다.

* 단점
    1. Broker Dependency  
    시스템 간 의존도가 낮아지고 메시지 브로커에 대한 의존성이 발생합니다.  

    2. Transction 단위 분리  
    장애나 이슈 발생 시 Retry / Rollback 에 대한 고려가 필요합니다.  

    3. 시스템 Flow를 파악하기 어렵습니다.  

    4. 디버깅이 어렵습니다.  