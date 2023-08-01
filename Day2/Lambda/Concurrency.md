### Concurrency
특정 람다에 request가 순간적으로 증가한다면 다른 람다를 실행할 수 없게되는데 이것을 throttling이라고 하고 요청을 받아들이지 않습니다.  

람다는 각 함수별로 reserved concurrency를 설정하여, 한 함수에 설정한 concurrency를 넘어가면 쓰로틀 상태가 됩니다.  

함수별로 적절한 reserved concurrency를 설정하여 비용 절감, 디도스 방지 등을 할 수 있습니다.  

따라서 함수를 생성하고 실행할 때 적절한 각 함수별로reserved concurrency를 설정하여 각 함수가 받아들이는 최대 요청을 제한하여 효율적인 운영이 가능해집니다.

지정하지 않으면 계정별로 남는 Concurrency를 기반으로 동작하게 됩니다.