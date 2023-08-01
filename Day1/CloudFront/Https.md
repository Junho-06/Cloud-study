> **Client -> CloudFront -> ALB -> EC2 로된 아키텍쳐가 있고 www.sample.io 라는 도메인으로 https를 사용하기를 원할 때, 인증서 설정을 해야 할 부분은 어디인지와 왜 해당 모듈에 설정을 하고 다른 모듈에는 설정을 하지 않아도 되는지 정리하세요.**

SSL 인증서는 Client -> CloudFront -> ALB 부분에서 적용되어야 합니다.  

CloudFront에 들어온 요청이 ALB를 통해 EC2로 전달되는과정에서 HTTPS 요청을 HTTP로 변환하고 EC2로 넘겨주어야 합니다.  

이유는 Client 와 CloudFront 간의 통신은 HTTPS를 사용하여 암호화 시켜야 하기때문입니다.  

ALB에서는 SSL을 종료시키고 EC2와 HTTP로 통신해야하기에 HTTPS로 요청을 받고 HTTP로 요청을 보내야 합니다.  

EC2에 인증서 설정을 하지 않는 이유는 ALB에서 SSL인증서가 종료되어 ALB -> EC2 의 통신이 HTTP로 이루어지기 때문입니다.