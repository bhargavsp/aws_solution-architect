# Questions and Answers

| Topics | Link to Navigate |
| :---: | :---: |
**`AWS Intro`** | https://github.com/bhargavsp/aws_solution-architect/blob/main/aws%20Q%26A.md#aws-introduction
**`EC2`** | https://github.com/bhargavsp/aws_solution-architect/blob/main/aws%20Q&A.md#ec2
**`IAM`** | https://github.com/bhargavsp/aws_solution-architect/blob/main/aws%20Q&A.md#iam
**`AMI`** | https://github.com/bhargavsp/aws_solution-architect/blob/main/aws%20Q%26A.md#ami
**`ELB & ASG`** | https://github.com/bhargavsp/aws_solution-architect/blob/main/aws%20Q%26A.md#elb--asg
**`RDS, Aurora, Elastic Cache`** | https://github.com/bhargavsp/aws_solution-architect/blob/main/aws%20Q%26A.md#rds-aurora-elastic-cache

## **`Exam Tips`**
| TIP | Understanding |
| :---: | :---: |
The loewst operational overhead | which effectively means what is the quickest and easiest way we can implement this with the least amount of effort and maintenance required 
The lowest overall cost | which means the cheapst and 
The most secure | means the securest
The most Fault Tolerant and Available | Which means the my service available when I need it to be and can it withstand faults elsewhere in network or the architecture
the most cost efficient |  
AWS Budgets | AWS Budgets provides the most stre
ELB | always recommended to allow the web/application tier to the inbound HTTPS Security Group for the loadd balancer
Database | database doesnt need to initiate connections to the upper tiers 
Database | DMS (Database Migratin Service) focus on data migration not to rewrite the SQL queries for the application
Saving plan vs Reserved instance | Both are the commitment for the 1 - 3 yeasrs, but the savings are for the consistent amount of the usage in USD per hour, and the reserved are for the instance configurations, type and the region
spot instance | it is mainly used for the stateless application but not the stateful appliction as we loss the data if the intances are termincated
savings plan | Reserved Instances savings plan covers only Amazon EC2, Elasticsearch, RDS, Redshift
savings plan | Compute Instances Savings Plans covers only Amazon EC2, Fargate, Lambda 
savings plan | SageMaker savings plan is only for sagerMaker instance alone
AWS config | lets us to define the rules and check of newely created volumes are encrypted
S3 storage lens | used tp monitor and identity the S3 buckets usage and activity accross the organization 
S3 | if question says access use frequently pick the `standard` 
S3 | if question says access infrequently pick the `S3-infrequent` storage class
S3 | if question says access rarely pick but need to accesss the data immediately (1 - 2 times a year) with the less amount of the time then pick the `S3-Glacier Instant` storage class 
S3 | if question says access rarely pick but need to accesss the data not immediately (5 - 12 hours) with the less amount of the time then pick the `S3-Glacier flexible retrieval` storage class 
S3 | if question says access rarely pick but need to accesss the data not immediately (12 - 48 hours) with the less amount of the time then pick the `S3-Glacier Deep archive` storage class 
S3 | if question says access there is no pattern pick the `S3-intelligent` storage class tier
Aurora global database | whihc offer async replication
Data Sync | It is a data transfer servie that makes easy to transfer data from on-prem to S3 or EFS
Transit Gateway | communication b/w 2 or more VPCs peacefully
VPC peering | good for communication of only 2 Vpcs
AWS Direct connect | It is good for the hybrid cloud
storage gateway | connects the on-premises data to the cloud data
Tape data | This type of data cannot be stored in the NFS storage, it has a ISCSI format and uses the SAN (storage area networking) protocol
Tape Gateway | Tape Gateway enables you to replace using physical tapes on premises with virtual tapes in AWS without changing existing backup workflows, the data from snwoball transfered to the Amazon S3 Glacier Flexible Retrieval and Amazon S3 Glacier Deep Archive not the s3 standarad
File Gateway | supports NFS/SMB protocols
Volume Gateway | supports ISCSI protocols
iscsi vtl | is for the tape data
AWS snowball | It is used to transfer the data physically in a device (it is mostly usefull if we have the large amount of the data that needs to uploaded to the aws cloud)
Instance scheduler | used to schedule the instances start and stop based on our requirement,it works for the EC2 instances and the RDS database as well 
Amazon Macie | used to discover personally identifiable information (PII)
Amazon GuardDuty | help protect your AWS accounts, workloads, and data from threats.
real life stream | amazon kinesis
durable, low latency database, single digit milliseconds | dynamodb
canary realease deployment for API gateway | Canary release is a technique to reduce the risk of introducing a new software version in production by slowly rolling out the change to a small subset of users before rolling it out to the entire infrastructure and making it available to everybody. 
cloudfront signed URLs | used to give access to particular set of the users for accessing certain content, not giving access to all the users 
If the load is not predictable | always go for the serverless
aws cognito identity pool | uses the 3rd party app for the authentiation from thefederated identities
aws cognito user pools | used to give the access to the web/mobile app for the authentiation
Multi AZ cluster deployment | comes with 2 read replicas for the more reads
multi az instance deployment | comes with just the stand by instance but no read replica
RPO vs RTO
Redis vs Memcached | Memcached is mainly used for caching data, and redis is used for the persistent data(stored data) ex: session data which needs to be used for storing the session of the user 
AWS KMS | EKS supports using the AWS KMS keys to provide the `envelope encryption` of kubernetes secrets in EKS, Envelope encryption adds an extra layer of the addition customer management layer of the encryption for the application secrets or the user data that is stored within the kubernetes cluster 
Hibernation | While the instance is in hibernation, you pay only for the EBS volumes and Elastic IP Addresses attached to it; there are no other hourly charges. It is not possible to enable or disable hibernation for an instance after it has been launched. 

<details>
  <summary>  1. AWS Introduction </summary>
  
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

### You are preparing to launch an application that will be hosted on a set of EC2 instances. This application needs some software installation and some OS packages need to be updated during the first launch. What is the best way to achieve this when you launch the EC2 instances?
EC2 User Data is used to bootstrap your EC2 instances using a bash script. This script can contain commands such as installing software/packages, download files from the Internet, or anything you want.

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

</details>


<details>
  <summary>  2. EC2 </summary>
  
## **`EC2`**
### what are the EC2 instances purchasing options
1. On-Demand Instances — short workload, predictable pricing, pay by second
2. Reserved (I & 3 years) 
  • Reserved Instances — long workloads  72% discount pricing compared to the on-demand instances
  • Convertible Reserved Instances — long workloads with flexible instances  66% dicount compared to the on-demand instances
3. Savings Plans (l & 3 years) —commitment to an amount of usage, long workload, locked to the specific instance family and AWS region
4. Spot Instances — short workloads, cheap, can lose instances (less reliable)
5. Dedicated Hosts — book an entire physical server, control instance placement, the most expensive option in the AWS
6. Dedicated Instances — no other customers will share your hardware
7. Capacity Reservations — reserve capacity in a specific AZ for any duration 

### You're planning to migrate on-premises applications to AWS. Your company has strict compliance requirements that require your applications to run on dedicated servers. You also need to use your own server-bound software license to reduce costs. Which EC2 Purchasing Option is suitable for you?
Dedicate Hosts: Dedicated Hosts are good for companies with strong compliance needs or for software that have complicated licensing models (BYOL). This is the most expensive EC2 Purchasing Option available.

### what are EC2 instance checks
Amazon EC2 (Elastic Compute Cloud) status checks are automated health checks that run every minute on instances to identify software and hardware issues. These checks are important for ensuring that instances are operating as expected and for identifying issues early

</details>


<details>
  <summary>  3. IAM </summary>
  
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

</details>

<details>
  <summary>  4. AMI </summary>

## **`AMI`**
### You can use an AMI in N.Virginia Region us-east-1 to launch an EC2 instance in any AWS Region.
AMIs are built for a specific AWS Region, they're unique for each AWS Region. You can't launch an EC2 instance using an AMI in another AWS Region, but you can copy the AMI to the target AWS Region and then use it to create your EC2 instances.

## **`EBS`**
### You are running a high-performance database that requires an IOPS of 310,000 for its underlying storage. What do you recommend?
You can run a database on an EC2 instance that uses an Instance Store, but you'll have a problem that the data will be lost if the EC2 instance is stopped (it can be restarted without problems). One solution is that you can set up a replication mechanism on another EC2 instance with an Instance Store to have a standby copy. Another solution is to set up backup mechanisms for your data. It's all up to you how you want to set up your architecture to validate your requirements. In this use case, it's around IOPS, so we have to choose an EC2 Instance Store.

</details>

<details>
  <summary>  5. ELB & ASG </summary>

## **`ELB & ASG`**
### Does the ELB provide the static IP wiht the DNS name 
Only Network Load Balancer provides both static DNS name and static IP. While, Application Load Balancer provides a static DNS name but it does NOT provide a static IP. The reason being that AWS wants your Elastic Load Balancer to be accessible using a static endpoint, even if the underlying infrastructure that AWS manages changes.

### You are using an Application Load Balancer to distribute traffic to your website hosted on EC2 instances. It turns out that your website only sees traffic coming from private IPv4 addresses which are in fact your Application Load Balancer's IP addresses. What should you do to get the IP address of clients connected to your website?
When using an Application Load Balancer to distribute traffic to your EC2 instances, the IP address you'll receive requests from will be the ALB's private IP addresses. To get the client's IP address, ALB adds an additional header called "X-Forwarded-For" contains the client's IP address.

### what are the Registered targets in a Target Groups in ELB
1. The target type of the target group determines how you register targets
2. For example, you can register instance IDs, IP addresses, or an Application Load Balancer
3. Your Network Load Balancer starts routing requests to targets as soon as the registration process completes and the targets pass the initial health checks.

### componenets of the EC2 auto scaling 
EC2 Auto Scaling is made up of three components:
1. a launch template to know what to scale
2. an Auto Scaling Group (ASG) that decides where to launch the EC2 instance
3. optional scaling policies that define when to scale

### For compliance purposes, you would like to expose a fixed static IP address to your end-users so that they can write firewall rules that will be stable and approved by regulators. What type of Elastic Load Balancer would you choose?
Network Load Balancer has one static IP address per AZ and you can attach an Elastic IP address to it. Application Load Balancers and Classic Load Balancers have a static DNS name.

### Your boss asked you to scale your Auto Scaling Group based on the number of requests per minute your application makes to your database. What should you do?
There's no CloudWatch Metric for "requests per minute" for backend-to-database connections. You need to create a CloudWatch Custom Metric, then create a CloudWatch Alarm.

</details>

<details>
  <summary>  5. RDS, Aurora, Elastic Cache </summary>

## **`RDS, Aurora, Elastic Cache`**
### is there possibility to setup the read replicas DB as the disaster recovery DB
Yes, we can setup as MultiAZ

### how we setup RDS from single AZ to Multi AZ
1. It is a zero downtime operation(no need to stop the DB to convert from single az to the multi AZ)

### But the following will happen internally from converting single AZ to Multi AZ
1. A snapshot is taken
2. A new DB is restored from the snapshot in a new AZ
3. Synchronization is established between the two databases<br/>
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/fdc8413f-c39f-4a15-bcba-51f289179d63)

</details>

<details>
  <summary>  5. AWS Budgets </summary>

## **`AWS Budgets`**
### 


</details>
