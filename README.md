# AWSLambda_CloudPing
AWS Lambda Function to monitor a website's availability via HTTP/HTTPS.

**Pre-Requisites:**
* Role for Lambda that allows put-metric access to Amazon CloudWatch

**How-To:**
* Create AWS Lambda function
 * Name: LambdaPing
 * Description: Check availability of websites
 * Runtime: Node.js 4.3
 * Handler: index.handler
 * Timeout : 10 sec
* Configure AWS CloudWatch event rule as trigger
 * Schedule: Fixed rate of 1 minute
 * Function: Lambda Ping
 * Input: Constant (JSON text)
 * JSON: { "domain": "www.example.com", "protocol": "https", "port": "443", "path": "/web/index.html" }

