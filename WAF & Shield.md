## Shield

* Protection for AWS resources against DDoS attacks
* DDoS attacks are generally distributed across many IPs
* Two versions: standard and advanced
  * Standard are free with Route53 and/or CloudFront
* Protection against Layer 3 and layer 4 DDoS attacks
* Shield Advanced - $3,000 per/month
  * EC2, ELB, CloudFront, Global Acceleration, and R53
  * Access to 24/7 365 DDoS Response Team & Financial Insurance against increase in costs because of DDoS attacks.

## WAF

* Layer 7 (HTTP/HTTPS) firewall
* Protects against complex layer 7 attacks
  * SQL Injections, Cross-Site Scripting, Geo Blocks, Rate Awareness
* Web Access Control List (WEBACL) integrated with ALB, API Gateway, and CloudFront
* Rules are added to a WEBACL and evaluated when traffic arrives
