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

## **`IAM`**
1. Root account created by default bu it shouldnt be used so we create IAM for every AWS user and share with them the required access to use only the services they need
2. Groups only contain users, not other groups
3. users no need to belong to a group, a single user can also be in multiple groups
4. users and groups are assigned a JSON document, called an IAM policies
5. In AWS we apply a least privilege principle, dont give more permissions than a user needs


















