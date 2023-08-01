### log4shell
log4shell은 Java Log4j의 취약점으로 발생하게 됩니다.  

WAF의 규칙을 구성하여 HTTP 요청에서 Java Log4j를 제거하면 막을수 있습니다.  

Log4Shell 공격은 특정 패턴과 문자열을 사용하여 Java Log4j를 호출합니다.  
이러한 패턴을 감지하여 해당 요청을 차단하는 규칙을 생성해야 합니다.

```json
{
  "Name": "Log4ShellProtectionRule",
  "Priority": 1,
  "Action": {
    "Type": "BLOCK"
  },
  "Statement": {
    "ByteMatchStatement": {
      "FieldToMatch": {
        "SingleHeader": {
          "Name": "User-Agent"
        }
      },
      "TextTransformations": [
        {
          "Type": "NONE"
        }
      ],
      "SearchString": "log4j",
      "PositionalConstraint": "CONTAINS"
    }
  },
  "VisibilityConfig": {
    "SampledRequestsEnabled": true,
    "CloudWatchMetricsEnabled": true,
    "MetricName": "Log4ShellProtectionRule"
  }
}
```
위는 예시의 log4shell 을 막는 규칙입니다.