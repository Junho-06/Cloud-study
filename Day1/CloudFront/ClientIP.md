> **Client -> CloudFront -> EC2(Backend)로 request가 들어올 때 EC2에서 Client의 IP를 알 수 있는 방법은 어떤 것이 있는지 조사하세요.**  

X-Forwarded-For 헤더를 사용해서 알아낼수 있습니다.  

CloudFront는 클라이언트의 IP 주소를 X-Forwarded-For 헤더로 EC2 인스턴스에 전달하게 됩니다.  

따라서 EC2의 웹 서버나 애플리케이션에서 이 헤더를 확인하여 클라이언트의 실제 IP 주소를 추출할 수 있습니다.  

또는 CloudFront 로그를 분석하여 알아낼 수 있습니다.  

CloudFront는 액세스 로그를 생성하도록 구성할 수 있습니다.  
이 로그를 분석하여 클라이언트의 IP주소를 확인할 수 있습니다.  

또는 CloudFront에서 Custom Header를 전달하여 Client IP를 알아낼 수도 있습니다.