1. 요청/응답 모델  

가장 일반적으로 사용되는 Invocation Model로 Lambda 함수를 동기적으로 호출 할 때 사용됩니다.  

클라이언트가 Lambda 함수를 호출하면 Lambda 함수가 작업을 수행하고 결과를 반환합니다.  

클라이언트는 Lambda 함수가 처리를 완료할 때 까지 대기 상태에 있습니다.  

2. 이벤트 호출 모델  

이 모델은 비동기적으로 Lambda 함수를 호출할 때 사용됩니다.  

Lambda 함수를 이벤트 소스에 연결하고 이벤트가 발생하면 Lambda 함수가 자동으로 호출됩니다.  

Lambda 함수는 작업을 수행한 후 결과를 반환하지 않으며, 비동기적으로 이벤트를 처리합니다.  

3. 스트림 호출 모델  

스트림 호출 모델은 비동기적 호출의 한 형태로, Event Invocation Model과 비슷합니다.  

이 모델의 경우 Lambda 함수가 Amazon DynamoDB Streams 또는 Amazon Kinesis Data Streams와 같은 스트림에 연결됩니다.  

Lambda함수는 스트림에서 레코드가 실시간으로 도착하는 대로 레코드를 처리합니다.