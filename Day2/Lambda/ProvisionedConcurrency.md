### Provisioned Concurrency
Cold Start 이슈를 해결하기 위한 기능 입니다.  

Provisioned Concurrency는 AWS Lambda 함수를 지속적으로 초기화하며, 런타임 환경을 준비함으로써, 사용자의 요청에 바로 응답할 수 있는 상태로 만들어주는 기능입니다.  

추가 비용이 발생하지만 Cold Start 이슈를 해결하는 좋은 방법입니다.

즉, 설정한 만큼 인스턴스를 준비시켜 Cold Start 없이 즉시 응답할 수 있도록 도와줍니다.