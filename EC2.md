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

