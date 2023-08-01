### Shield
Shield는 DDos 공격으로부터 AWS의 애플리케이션을 보호합니다.  

기본적으로 애플리케이션에 활성화 되어있습니다.  

### WAF
WAF는 Shield 보다 상위 레벨에서의 서비스를 제공합니다.  

사용자의 애플리케이션이나 API를 SQL 주입, XSS와 같은 일반적인 위협으로부터 보호하게 됩니다.  

Shield와는 다르게 WAF는 사용하기 위해 별도로 활성화 해줘야 합니다.  

### 차이점
Shield 는 3,4 계층 처럼 네트워크 계층에서 일어나는 공격을 보호합니다.  

WAF는 7계층인 애플리케이션 계층에서 공격을 보호하게 됩니다.  