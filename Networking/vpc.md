# VPC

## Elastic Network Interfaces (ENI)
1. It is a logical component in an VPC that represent a virtual network card.
2. They are bound to the specific AZ(cant be used in the other AZ)
3. The ENI can have the following attributes:
4. Primary private IPv4, one or more secondary IPv4
5. One Elastic IP (IPv4) per private IPv4
6. One Public IPv4
7. One or more security groups
8. A MAC address <br/>
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/7cf2b221-3f16-478f-92a7-56cd2c2361d1)
9. You can create ENI independently and attach them on the fly (move them) on EC2 instances for failover
10. usecae: It is basically used to access from application from an other private addresss as well, if there is an failover of the ec2 instance, we can detach the ENI and then attach to the other ec2 instance and access our application so fast
