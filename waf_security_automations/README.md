# Overview
AWS WAF Security Automations에 대해


# AWS WAF
AWS WAF is a web application firewall that helps protect web applications from common web exploits that can affect application availability, compromise security, or consume excessive resources. AWS WAF enables customers to define customizable web security rules, giving them control over which traffic to allow or block to web applications and API's deployed on Amazon CloudFront, an Application Load Balancer, or API Gateway.


# AWS WAF Security Automations
Configuring WAF rules can be challenging and burdensome to large and small organizations alike, especially for those who do not have dedicated security teams. To simplify this process, AWS offers the AWS WAF Security Automations solution, which automatically deploys a single web access control list (web ACL) with a set of AWS WAF rules designed to filter common web-based attacks. __During initial configuration of the solution’s AWS CloudFormation template__<sup id="a1">[1](#s1)</sup> , users specify which protective features to include, as depicted in the image below. After the solution is deployed, AWS WAF will begin inspecting web requests to their existing CloudFront distributions or Application Load Balancer, and block them as applicable.

><b id="s1">1.</b> WAF Security Automations은 CloudFormation을 사용하여 프로비저닝함

![alt text](aws_waf_security_automations.png)

# Reference
* https://docs.aws.amazon.com/ko_kr/solutions/latest/aws-waf-security-automations/welcome.html
