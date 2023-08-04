> **간단한 스크립트를 작성하여 로그 데이터를 1시간 간격으로 백업할 수 있도록 구성해 보세요.**

스크립트 부분은 감이 안잡혀서 도움을 받았습니다.

```python
import boto3
import time
import json

def backup_logs_to_s3(log_data, bucket_name, object_key):
    s3 = boto3.client('s3')
    s3.put_object(Bucket=bucket_name, Key=object_key, Body=json.dumps(log_data))

if __name__ == '__main__':
    # 로그 데이터를 이용하여 로그를 생성하는 가정
    log_data = {
        "timestamp": int(time.time()),
        "message": "This is a log message."
    }

    # AWS S3 버킷 정보 설정
    bucket_name = "your-s3-bucket-name"
    object_key = "logs/backup_log_{timestamp}.json".format(timestamp=log_data["timestamp"])

    # 로그 데이터를 1시간 간격으로 백업
    while True:
        backup_logs_to_s3(log_data, bucket_name, object_key)
        print("Log backed up to S3:", object_key)
        time.sleep(3600)  # 1시간(60초 * 60분) 간격으로 백업
```

위 스크립트를 활용하여 데이터를 1시간 간격으로 백업할 수 있습니다.