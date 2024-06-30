# Networking

## Networking has 2 sorts of IP's 
1. IPV4 -  
2. IPV6 - Hexadecimal (used for IOT)

## Private and Public IP
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/0e9e9cdc-5dd9-4a48-8477-0a5643dd66cc)
1. machines connect to WWW using an NAT + internet gateway (a proxy)
2. only a specified number if IP's are used as Private IP's
3. private IP means the machine can only be identified on that particular private network only

## can we connect to the EC2 instance through SSH with the private IP
1. It is not possible because the private IP's only belong to the particular network.
2. example the AWS instance private IP belongs to the AWS network,
3. Only the internal AWS network private IP can connect to the other private IP inside the AWS network.  
