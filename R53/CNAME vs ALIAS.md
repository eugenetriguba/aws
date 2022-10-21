# CNAME vs ALIAS

- A maps a NAME to an IP address
    - such as www.google.com to 1.3.3.7
- CNAME maps a NAME to another NAME
    - www.google.com
- CNAME is invalid for naked/apex (google.com)
- Many AWS services use a DNS Name (ELBs)
- With just CNAME - google.com => ELB would be invalid.

This is a problem where ALIAS records fix.

- ALIAS records map a NAME to an AWS resource
- Can be used for botht he naked/apex and normal records.
- For non apex/naked - functions like CNAME
- For AWS resources, AWS tries to encourage you to use it. There is no charge for ALIAS requests pointed at AWS resources.
- For AWS Services - default to picking ALIAS
- Should be the same "Type" as what the record is pointing at.
- API Gateway, Cloudfront, Elastic Beanstalk, ELB, Global Accelerator, S3.

- ALIAS is outside of the usual DNS standard. It is implemented by AWS.
