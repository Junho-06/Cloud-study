### ALB
ALB는 Layer 7 (Application Layer)의 로드 밸런서입니다.  
HTTP, HTTPS, WebSocket 등과 같은 프로토콜에서 작동합니다.  

클라이언트의 원본 IP주소를 HTTP 요청 헤더의 X-Forwarded-For 헤더에 담아 웹 서버로 전달합니다.  
그러나 이 헤더는 클라이언트가 조작할 수 있는 위험이 있으므로 신뢰성이 떨어집니다.  
또한 X-Forwarded-For 헤더에 담긴 IP는 실제 클라이언트 IP와 프록시를 거친 IP들이 섞여있을 수 있습니다.  

### NLB
NLB는 Layer 4 (Transport Layer)의 로드 밸런서입니다.  
TCP, UDP와 같은 프로토콜에서 작동합니다.  

NLB는 클라이언트의 원본 IP 주소를 변경하지 않고, EC2 인스턴스에 원본 IP 주소 그대로 전달합니다.  

즉, NLB를 통과한 요청은 EC2 인스턴스가 클라이언트로부터 직접 수신한 것과 동일한 IP 주소를 가지게 됩니다  


### 결론
결국 프로토콜이 다르고 동작 방식이 다르기 때문에 네트워크 로드밸런서는 클라이언트의 요청을 그대로 전달해주지만  
ALB는 클라이언트의 요청을 프록시서버인 ALB를 거치며 클라이언트 IP가 변환되는것입니다.