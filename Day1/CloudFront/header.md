> **CloudFront에서 backend에서 준 정보에 추가로 http response header에 정보를 추가하는 방법은 어떤 것이 있는지 정리하세요.**  

CloudFront의 Behavior를 설정하면 됩니다.  

CloudFront 배포에서 Behavior를 구성할 때, Cache Based on Selected Request Headers 옵션을 사용하여 특정 요청 헤더 값을 기준으로 캐시를 분리할 수 있게 됩니다.  

이를 활용하면 특정 요청 헤더 값을 기준으로 캐시된 응답에 추가 헤더를 포함시킬 수 있습니다.  

CloudFront 오리진 헤더를 구성하는 방법입니다.  

CloudFront에서 오리진 헤더를 구성하여 요청을 오리진에 전달할 때 추가적인 헤더를 포함시킬 수 있습니다.  

이를 이용하여 백엔드 서버로 전달되는 요청 헤더에 웒는 정보를 추가할 수 있습니다.