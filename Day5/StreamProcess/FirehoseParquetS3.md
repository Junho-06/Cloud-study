> **Kinesis Firehose를 통해 스트림 데이터를 Parquet 포맷으로 변환하여 S3에 저장해 보세요.**

먼저 Kinesis Firehose를 생성합니다.  

데이터 변환 메뉴에서 convert record format를 apache parquet로 설정합니다.  

목적지를 s3로 선택하고 버킷과 경로를 설정합니다.  

IAM Role을 설정하여 Firhose가 s3에 데이터를 저장하는 역할을 부여합니다.  