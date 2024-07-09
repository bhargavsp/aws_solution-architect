# more additional services in aws

## CloudFormation
1. CloudFormation is a declarative way of outlining your AWS Infrastructure, for any resources (most of them are supported).
2. Then CloudFormation creates those for you, in the right order, with the exact configuration that you specify
3. It is Infrastructure as code, no resources are manually created
4. Each resources within the stack is tagged with an identifier so you can easily see how much a stack costs you
5. You can estimate the costs of your resources using the CloudFormation template
6. Savings strategy: In Dev, you could automation deletion of templates at 5 PM and recreated at 8 AM, safely
7. Automated generation of Diagram for your templates!
8. Declarative programming (no need to figure out ordering and orchestration)
9. You can use "custom resources" for resources that are not supported in cloudFormation
10. CloudFormation + Application Composer gives the great combination of seeing the relations b/w the components

## CloudFormation - Service Role
1. It is an IAM role that allows the cloudFormation to create/update/delete stack resources on your behalf
2. Here the user must have the `iam:PassRole` permissions to create and pass the template
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/7edf10dd-0291-4d4d-80ec-8e79dff4ee5a)

## Amazon Simple Email Service (SES)
This is a bulk email service, used mostly for marketing
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/a653865c-6d50-4e06-b16b-aedeaf5e2cea)

## Amazon Pinpoint

## Pinpoint vs SNS vs SES
1. In SNS & SES you managed each message's audience, content, and delivery scnedule 
2. In Amazon Pinpoint, you create message templates, delivery schedules, highly-targeted segments, and full 
campaigns
3. uses for the run campaigns 

## SSM session Manager in the AWS system manager
1. Allows you to start a secure shell on your EC2 and the on-premises servers
2. No SSH access, bastion hosts, or SSH keys needed
3. No port 22 needed (better security)
4. Supports Linux, macOS, and Windows
5. Send session log data to S3 or CloudWatch Logs
6. ![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/6ac6a11b-b92a-4e98-aba1-ec28ec92a330)
