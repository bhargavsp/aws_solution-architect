# EC2

## Ec2 Capabilities:
1. Renting virtual machines (EC2)
2. Storing data on virtual drives (EBS)
3. Distributing load across machines (ELB)
4. Scaling the services using an auto-scaling group (ASG) 

## EC2 configuration options
1. Operating System (OS): Linux, Windows or Mac OS
2. How much compute power & cores (CPU)
3. How much random-access memory (RAM)
4. How much storage space:
  5. Network-attached (external storages) (EBS & EFS)
  6. hardware (EC2 Instance Store)
7. Network card: speed of the card, Public IP address
8. Firewall rules: security group
9. Bootstrap script (configure at first launch): EC2 User Data 

## Security Groups
1. Security groups can add rules for the specific IP or they can be refered by the other Security Groups
2. ![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/7baab19b-1696-4d8c-838f-9ae25c0c27a8)
3. SG are locked to a specific region and the VPC combinition
4. Its good to maintain one separate SG from teh SSH access
5. ![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/c335d90b-1168-4a34-98b7-6c53a5b22529)

## Ec2 instance types and the usage options
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/68f5e3ad-1649-4dcc-a5c9-82e904b855dc)

Types of the instances groups:
|type of the instance| usage |
|:---:|:---:|
compute optimized | Compute Optimized EC2 instances are great for compute-intensive workloads requiring high-performance processors (e.g., batch processing, media transcoding, high-performance computing, scientific modeling & machine learning, and dedicated gaming servers).
Memory Optimized |  you choose for a critical application that uses an in-memory database
Storage Optimized | Storage Optimized EC2 instances are great for workloads requiring high, sequential read/write access to large data sets on local storage.

## EC2 spot instances 
1. can get upto 90% discount compared to the on-demand
2. Define max spot price and get the instance while current spot price < max 
  • The hourly spot price varies based on offer and capacity 
  • If the current spot price > your max price you can choose to stop or terminate your instance with a 2 minutes grace period. 
3. Other strategy: **Spot Block**
  • 'block" spot instance during a specified time frame (1 to 6 hours) without interruptions 
  • In rare situations, the instance may be reclaimed 
4. Used for batch jobs, data analysis, or workloads that are resilient to failures. 
5. Not great for critical jobs or databases
6. You can only cancel Spot Instance requests that are open, active, or disabled. Cancelling a Spot Request does not terminate instances. You must first cancel a Spot Request, and then terminate the associated Spot Instances

## spot fleets
1. Spot fleets allows us to automatically request spot instances with the lowest price based on the pools we defined
2. Spot Fleet is a set of Spot Instances and optionally On-demand Instances. It allows you to automatically request Spot Instances with the lowest price.

## 
