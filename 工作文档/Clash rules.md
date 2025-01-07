# rules
https://github.com/renzhaozhao/rules

rule-providers
```yaml
rule-providers:
  my-proxy:
    type: http
    url: 'https://raw.githubusercontent.com/renzhaozhao/rules/release/proxy.yaml' 
    behavior: domain
    path: ./ruleset/proxy.yaml
    interval: 3600
  my-direct:
    type: http
    url: 'https://raw.githubusercontent.com/renzhaozhao/rules/release/direct.yaml' 
    behavior: domain
    path: ./ruleset/direct.yaml
    interval: 3600
  my-reject:
    type: http
    behavior: domain
    url: "https://raw.githubusercontent.com/Loyalsoldier/clash-rules/release/reject.txt"
    path: ./ruleset/reject.yaml
    interval: 86400 
```

rules
```yaml
rules:
  - RULE-SET,my-proxy,🔰国外流量
  - RULE-SET,my-direct,DIRECT
  - RULE-SET,my-reject,REJECT
```

# 参考
https://github.com/Loyalsoldier/clash-rules?tab=readme-ov-file
