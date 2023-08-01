> **한 IP에서 1분 동안 10번 이상 요청 시 차단하는 AWS WAF를 구성을 해보세요.**

WAF의 Rule을 설정하여 위 문제를 해결할 수 있습니다.

```json
{
  "Name": "RequestRateLimitRule",
  "Priority": 1,
  "Action": {
    "Type": "BLOCK"
  },
  "Statement": {
    "RateBasedStatement": {
      "Limit": 10,
      "AggregateKeyType": "IP",
      "ScopeDownStatement": {
        "NotStatement": {
          "Statement": {
            "IPSetReferenceStatement": {
              "Arn": "arn:aws:wafv2:region:account-id:resource/ManagedRuleSetIPSet/IPSetForWhiteList"
            }
          }
        }
      }
    }
  }
}
```

위처럼 설정해서 한 IP에서 1분에 10번이상의 요청이 오면 차단하도록 막을수 있습니다.