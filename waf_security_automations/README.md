# Overview
AWS WAF Security Automations에 대해


# AWS WAF
AWS WAF is a web application firewall that helps protect web applications from common web exploits that can affect application availability, compromise security, or consume excessive resources. AWS WAF enables customers to define customizable web security rules, giving them control over which traffic to allow or block to web applications and API's deployed on Amazon CloudFront, an Application Load Balancer, or API Gateway.


# AWS WAF Security Automations
Configuring WAF rules can be challenging and burdensome to large and small organizations alike, especially for those who do not have dedicated security teams. To simplify this process, AWS offers the AWS WAF Security Automations solution, which automatically deploys a single web access control list (web ACL) with a set of AWS WAF rules designed to filter common web-based attacks. __During initial configuration of the solution’s AWS CloudFormation template__<sup id="a1">[1](#s1)</sup> , users specify which protective features to include, as depicted in the image below. After the solution is deployed, AWS WAF will begin inspecting web requests to their existing CloudFront distributions or Application Load Balancer, and block them as applicable.

간단히 말해서 AWS에서 제공하는 서비스 조합(S3, Lambda, WAF 등)으로 공격자로 판별되는 IP를 block 대상 리스트에 업데이트함

><b id="s1">1.</b> WAF Security Automations은 CloudFormation을 사용하여 프로비저닝함

![alt text](aws_waf_security_automations.png)

### 1. 비보안 전문가용 용어 정리
* HTTP Flood : DDoS 공격
* Scanners and Probes : 웹서버의 취약점을 찾는 행위
  * header 값을 찾는 등의 행위
* Bad Bot : 불법 crawler, 구글과 같은 crawler는 robots.txt를 참조하여 허용하지 않는 컨텐츠에는 접근하지 않음

### 2. 보안 항목별 적용 방법
* Whitelist : 수동으로 IP 입력하여 차단
* Blacklist : 수동으로 IP 입력하여 차단
* SQL Injection : 아래와 같은 조건을 선택하여 조건에 맞는 request 차단
  * Body contains SQL injection threat after decoding as HTML tags.
  * Query string contains SQL injection threat after decoding as HTML tags.
  * ...
* XSS : 아래와 같은 조건을 선택하여 조건에 맞는 request 차단
  * URI contains a cross-site scripting threat after decoding as HTML tags.
  * Body contains a cross-site scripting threat after decoding as HTML tags.
  * ...
* HTTP Flood : request를 분석하여 특정 조건(threshold, ignore sufixes 등)에 맞으면 차단 IP 리스트 업데이트
* Scanners and Probes : request를 분석하여 특정 조건(threshold, http error code 등)에 맞으면 차단 IP 리스트 업데이트
* IP Reputation Lists : 잘 알려진 공격자 IP를 CloudWatch를 통해 업데이트
* Bad Bot : Honeypot를 이용해 공격자 IP 판별


# Reference
* AWS WAF Security Automations : https://docs.aws.amazon.com/ko_kr/solutions/latest/aws-waf-security-automations/welcome.html
* Honeypot : https://en.wikipedia.org/wiki/Honeypot_(computing)