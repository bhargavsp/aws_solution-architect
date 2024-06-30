# Questions and Answers

| Topics | Link to Navigate |
| :---: | :---: |
**`AWS Intro`** | https://github.com/bhargavsp/aws_solution-architect/blob/443f77c033e383d5286707c6444ffa9644cbf063/aws%20Q%26A.md?plain=1#L7

## **`AWS Introduction`**
### how to choose an AWS region
It depends on mine. but it can be based on some factors that effect
1. compliance: with some restrictions for some government websites, with data governance and legal requirements
2. proximity: for low latency
3. available services: not all services in arent availble in all regions
4. pricing: various from region to region

### AWS AZ (availability zones) 
1. Each region may have min 3 and max 6 AZ's
2. they may have as many data centers 2 or more in a single AZ, aws doesnt say us
3. all the AZ's are isolated from each other so they are isolated from disasters

### AWS Global services
1. IAM 
2. Route 53 (DNS service)
3. CloudFront (content Delivery Network)
4. WAF (Web Application Firewall)

### Some region scoped services
1. Amazon EC2 (Infrastructure as a Service)
2. Elastic Beanstalk (Platform as a Service)
3. Lambda (Function as a Service)
4. Rekognition (Software as a Service)

### different ways to login into the AWS account
1. AWS Management Console (protected by password + MFA)
2. AWS Command Line Interface (CLI): protected by access keys
3. AWS Software Developer Kit (SDK) - for code: protected by access keys

### usage of the Access keys in the AWS
1. There are basically used to login into the AWS, in the form of CLI or by using the SDK
2. Access keys are generated in the AWS console
3. Every user can generate their own access keys, so we should share our access keys with others
4. Access key ID = username, and the secret access key = password

## what can we do with AWS CLI
1. Used to interact with the AWS services using the command-line shell
2. We have direct access to the public API's of the AWS services
3. we can develop the scripts to manage the resources 

## what is the AWS SDK is ?
1. SDK is software Development Kit
2. SDK's are language specific
3. Enables us to access and manage the AWS services programmatically

## can we give the IAM user credentails teh access keys and secret access key in the AWS instance connect/
Never ever give the IAM access keys and the secret aceess keys in the aws intance connect

## **`IAM`**
### what is IAM
1. Root account created by default but it shouldnt be used so we create IAM for every AWS user and share with them the required access to use only the services they need
2. Groups only contain users, not other groups
3. users no need to belong to a group, a single user can also be in multiple groups
4. users and groups are assigned a JSON document, called an IAM policies
5. In AWS we apply a least privilege principle, dont give more permissions than a user needs

### what are the defense mechanisms in the IAM 
There are 2 types
1. IAM password policy
2. MFA (Multi Factor Authentication) (its recommended to use it in AWS)

### what are the MFA devices options in the AWS
1. Virtual MFA devices- Google Authenticator, Authy
2. Universal 2nd factor security key - yubikey by Yubico
3. Hardware key Fob MFA device- Gemalto
4.  Hardware key Fob MFA device by AWS GovCloud (US)- surepassID

















