# IAM (needs a work around on the IAM policy)

### In the IAM Dashboard, the `account alias` must be unique across all Amazon Web Services (AWS) products within a given network partition. A partition is a group of AWS Regions

### we have different types of policies assigning in the IAM: refer to the https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html

## How to create an IAM user in AWS
| Process Step | Reference |
| :---: | :---: |
Navigate to the IAM user console in the AWS and click on the create user | ![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/d59b141b-0bc4-4c52-a173-fd01e3a01b71)


## IAM Policy structure
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/2f4b1f34-f6fe-4327-9fbd-bd040559abe4)


## IAM password policy
1. set minimum characters types
2. Require specific characters - lowecase, uppsercase, numbers, non-alpha
3. Allow all IAM users to change their own passwords ot not
4. password expiraton setup
5. prevent password re-use

## IAM Roles for services
1. These IAM roles are not for the particular user
2. These are created for the services in AWS (EC2) to access the other resources inside the AWS
3. EX: Lamda function, Roles for cloud formation, EC2 instance roles
4. The combination of the IAM role and the service forms the Entity

## IAM Security Tools
1. IAM crendetails Report (account level)
2. IAM access advisor (user-level)

## IAM Guidelines and best practices
1. Don't use the root account except for AWS account setup
2. One physical user = One AWS user
3. Assign users to groups and assign permissions to groups
4. Create a strong password policy
5. Use and enforce the use of Multi Factor Authentication (MFA)
6. Create and use Roles for giving permissions to AWS services
7. Use Access Keys for Programmatic Access (CLI / SDK)
8. Audit permissions of your account using IAM Credentials Report & IAM Access Advisor
9. Never_share IAM users & Access Keys 
