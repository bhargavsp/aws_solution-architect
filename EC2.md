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

## What are Elastic IP's 
1. stop and start of the instances in AWS changes the public IP, if need an fixed IP then the elastic IP does that work, even on the start stop instance doesnt change the public ip of that instance
2. With an Elastic IP address, you can mask the failure of an instance or software by rapidly remapping the address to another instance in your account.
3. we have only 5 elastic IP in one AWS account
4. Try to avoid the Elastic IP's as
5. They often reflect poor architectural decisions
6. Instead, use a random public IP and register a DNS name to it
7. Or, as we'll see later, use a Load Balancer and don't use a public IP 

## EC2 Placement Groups
 1. It is the placement of our Ec2 instance where tjhey are placed in the AWS physical Hardware
 2. we can create our placment of the EC2 instance, so that AWS will place them accordingly, as we cant access the pyhsical hardware of the AWS directly
 3. There are 3 types of the placment groups
 4. Cluster—clusters instances into a low-latency group in a single Availability Zone <br/>![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/1231be70-fb83-4222-b181-62e28479b5cd)
 5. Spread—spreads instances across underlying hardware (max 7 instances per group per AZ) — critical applications <br/> ![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/7eb889b6-728d-4810-a8ae-43bea0e8b7f4)
 6. Partition—spreads instances across many different partitions (which rely on different sets of racks) in an AZ, partition can upto 7 per AZ. can span upto multiple AZ's no limit and Scales upto 100'S of EC2 instances per group, wecan know whihc partition is on which rack that is possible by using the metadata <br/>

## EC2 hibernate
1. The EC2 instance takes time to boot up and run the EC2 user data scrits to install the application. This is the readon the EC2 hibernate is brought into picture
2. use cases: if we have long running processing, saving ram and if we want less time to start the ec2 instance after stop
3. Here the ram memory will be stored to the EBS volume, and once the EC2 instance is started afer stop, the saved ram in EBS will be loaded to the instance and reboots faster
4. the security mesures for using the Hibernate in EC2 is, the EBS volume should be enough to store the ram and mainly the root EBS volume must be encrypted
5. FOr performing the EC2 hibernation, the EC2 instance root volumne must be an instance store volume 
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/860b5874-5e88-4c80-b2b9-900852993a38)
