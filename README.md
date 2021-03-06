# AWSLambda_CloudPing [![Build Status](https://travis-ci.org/chriselsen/AWSLambda_CloudPing.svg?branch=master)](https://travis-ci.org/chriselsen/AWSLambda_CloudPing)
AWS Lambda Function to monitor a website's availability via HTTP/HTTPS. This can be combined with VPC Endpoint for AWS Lambda to monitor the availability of an AWS Managed NAT Gateway.
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
