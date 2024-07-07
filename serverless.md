# Serverless

## what is serverless
1. Server-less does not mean there are no servers... it means you just don't manage / provision / see them
2. Initially... Serverless FaaS (Function as a Service)
3. Serverless was pioneered by AWS Lambda but now also includes anything that's managed: "databases, messaging, storage, etc." 

## serverless in aws
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/f0ce3e15-1657-4dfa-a29e-91ebc32d4209)

## AWS Lambda
1. Integrated with whole AWS suite of services
2. It is monitored though the AWS cloudwatch
3. Virtual functions — no servers to manage!
4. Its wasy to get the more resources per function(upto 10gb RAM)
5. Limited by time - short executions
6. Run on-demand
7. Scaling is automated!
8. It also has the support for the Lamda container images, the container image itself must implement the Lamda runtime API

## AWS Lambda limits to know - per region
1. Execution: 
* Memory allocation: 128 MB— IOGB (l MB increments) 
* Maximum execution time: 900 seconds (15 minutes) 
* Environment variables (4 KB) 
* Disk capacity in the "function contained' (in /tmp): 512 MB to IOGB 
* Concurrency executions: 1000 (can be increased) 
2. Deployment: 
* Lambda function deployment size (compressed .zip): 50 MB 
* Size of uncompressed deployment (code + dependencies): 250 MB 
* Can use the /tmp directory to load other files at startup 
* Size of environment variables: 4 KB

## Lambda Snapstart
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/d5e26f48-50de-4efe-8aaf-8cfa0da6d25a)

## We can use the cloudFront to minimize the latency for the users, how do we invoke it
We have 2 types of the cloudFront at the edge functions
1. cloudFront Functions: high performance, high scale, used for viewer request and response <br/>![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/bcc67f88-ecca-464d-827c-84d65ea8b3e1)
2. Lambda@Edge: lambda functions return in the nodejs or the python
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/25d6b8cc-da0b-47c5-81ac-8c36ec7ee04c)

## Networking of the lambda
1. By default, your Lambda function is launched outside your own VPC (in an AWS-owned VPC) 
2. Therefore, it cannot access resources in your VPC (RDS, ElastiCache, internal ELB... ) 
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/9f940cfd-c58c-47bf-8cf8-a7fb28249337)

## launching lambda in our own VPC
1. You must define the VPC ID, the Subnets and the Security Groups
2. Lambda will create an ENI (Elastic Network Interface) in your subnets
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/1a1836a8-7b9e-4f1e-b896-38f67a783a0b)

## Lambda RDS Proxy
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/23b4c877-4556-4095-ae88-0e90de01a6de)

## invoking lambda from RDS and Aurora
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/bb73d1b7-a8b3-4e2a-a65e-469b737768fb)

## RDS Event Notifications
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/4d4becc2-3dbe-4e30-8bda-cc83d497371c)

## DynamoDB Accelerator (DAX)
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/6bfdf98f-44f3-4cc2-b405-8d3321d52dbf)

## DynamoDB streams
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/18a055d2-fb18-47c1-8913-61d342fa68a4)

## API Gateway
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/5a2a2e27-e6b2-4260-b17a-0da106f43f61)

## API Gateway — AWS Service Integration Kinesis Data Streams example
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/1a18b2db-11c9-489a-9b0b-e1a80ecc7693)

## AWS Step Functions
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/e2d33967-195b-4861-9076-6675e97730c0)

## Cognito user pools
Access the aws services using the api gateway
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/dfa9b41d-a3bf-427c-ba00-a853a100bb02)

## COgnito Identity pools (Federated identities)
Its direct access to the aws console wuth some temporary credentails and the tokens
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/7da5f32c-2807-4616-95c7-fd324a7f7045)


