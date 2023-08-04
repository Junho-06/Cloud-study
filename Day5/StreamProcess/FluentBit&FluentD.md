> **FluentBit/FluentD를 활용하여 로그 데이터를 Kinesis Stream에 전송해보세요.**

먼저 FluentBit를 설치합니다.  

AWS IAM 역할에 들어가서 FluentBit가 Kinesis Stream에 쓰기 권한을 가지고 있어야하기 때문에 알맞은 역할을 부여합니다.  

FluentBit 설정파일을 작성합니다.  
인풋에는 로그 파일을 설정합니다.  
아웃풋에 kinesis stream을 잘 설정해줍니다.  

FluentBit를 설정파일을 지정하여 실행합니다.