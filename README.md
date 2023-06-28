# AWSLambda_CloudPing
AWS Lambda Function to monitor a website's availability via HTTP/HTTPS. This can be combined with VPC Endpoint for AWS Lambda to monitor the availability of an AWS Managed NAT Gateway.

It can also be used in combination with [Amazon CloudWatch Alarms](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/AlarmThatSendsEmail.html) and [Amazon Route 53 health checks that monitor CloudWatch alarms](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/health-checks-types.html) to react via Route 53 to internal endpoint failures. 

![Screenshot](https://github.com/chriselsen/AWSLambda_CloudPing/raw/master/AWSLambdaPing.PNG)

**Pre-Requisites:**
* Role for Lambda that allows put-metric access to Amazon CloudWatch

**How-To:**
* Create AWS Lambda function
  * Name: LambdaPing
  * Description: Check availability of websites
  * Runtime: Node.js 4.3
  * Handler: index.handler
  * Timeout : 10 sec
  * Source: In file LambdaPing.nodejs
* Configure AWS CloudWatch event rule as trigger
  * Schedule: Fixed rate of 1 minute
  * Function: Lambda Ping
  * Input: Constant (JSON text)
  * JSON: { "domain": "www.example.com", "protocol": "https", "port": "443", "path": "/web/index.html" }

**Defaul Settings for JSON:**
* domain: example.com
* protocol: https
* port: 443
* path: /
* method: GET
