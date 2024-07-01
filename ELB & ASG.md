# High Avaliability and Scalability

## Scalability means that an application / system can handle greater loads by adapting. 

## There are two kinds of scalability: 
1. Vertical Scalability - In short vertical scalability means increasing the size of an instance (scale up or down as per need), EX: t2.micro to t2.large, It is common for non distributed systems suxh as databases, RDS, ElastiCache are services that can scale vertically, There is a hardware limit for the vertical scalling  <br/>![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/a110bdf9-6329-4714-9da3-23c1c3a9ea0a)

2. Horizontal Scalability (= elasticity) - In short Horiozntal scaling increases the number of the instances/ systems horizontally (scale out or in), this is most common in the modern web applications <br/>![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/b51d5c2d-280a-4faf-8e0a-24e9fd3933ba)
3. auto scale mean ensure your services run smooth in high load by `auto scaling Group` and `load balancing`

## Scalability is linked but different to High Availability 

## HIgh Avaliability
1. High availability mean ensure your services never go down by replication or multi master
2. The example fo an high avaliability can be passive for the `RDS`(Relational Database) as it offers an multi AZ
3. The goal of the high avaliability is to survive a data center loss 
4. High Availability usually goes hand in hand with horizontal scaling
5. High availability means running your application / system in at least 2 data centers (== Availability Zones)
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/a967fedf-7ca0-42ec-a718-3151b0f24558)

## load balancing
It forwards the traffic to the multiple servers through an `single End point of access` DNS (Elastic Load Balancer) we dont know which EC2 server fulfilled our request
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/db031d73-4a9e-49c7-aff3-1c5d10924a48)

## why do we use the load balancer?
1. Spread load across multiple downstream instances
2. Expose a single point of access (DNS) to your application
3. Seamlessly handle failures of downstream instances
4. Do regular health checks to your instances
5. Provide SSL termination (HTTPS) for your websites
6. Enforce stickiness with cookies
7. High availability across zones
8. Separate public traffic from private traffic

## why use an Elastic Load balancer
1. AWS takes care of maintaince, upgrades, high avaliability and low cost as the aws mainteance everything
2. aslo integrated with the other aws services
3. And also Health checks are made for load balancers regular to check the connected instances are working or not by using hte protocol, port, endpoint to that particular instance

## types of load balancers in AWS
there are 4 typs of load balancers in the AWS
1. Classic Load Balancer (VI - old generation) — 2009 — CLB - HTTR HTTPS,TCR SSI (secure TCP)
2. Application Load Balancer (v2 - new generation) — 20 1 6 — ALB - HTTPS,WebSocket
3. Network Load Balancer (v2 - new generation) — 20 1 7 — NLB - TCR TLS (secure TCP), UDP
4. Gateway Load Balancer — 2020 — Operates at layer 3 (Network layer) — IP Protocol
5. some load balances can be setup as internal (private) or external (public) ELB's

## Load balancer security groups
 ![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/b1194963-2c14-43d6-b46e-696bc5cf2f39)

## Application Load Balancer
1. Load balancing to multiple HTTP applications across machines, multiplpe EC2 instance form a group called the (target groups)
2. Load balancing to multiple applications on the same machine with the help of containers (ex: ecs)
3. Support for HTTP/2 and WebSocket
4. support the redirect of the traffic from HTTP to HTTPS
5. Routing tables to different target groups: 
• Routing based on path in URL (example.com/users & example.com/posts)
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/263b6e7c-96a2-4de3-95f2-cac8e7932098)
• Routing based on hostname in URL (one.example.com & other.example.com) <br/>
• Routing based on Query String, Headers (example.com/users?id= 1 23&order=false) <br/>
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/e79c9c2b-02cb-47b4-8b1a-a3044a55af99)

7. ALB are a great fit for micro services & container-based application (example: Docker & Amazon ECS)
8. Has a port mapping feature to redirect to a dynamic port in ECS


## what are target groups in the load balancing
Taret groups can be created of multiple types
1. EC2 instances (can be managed by an Auto Scaling Group) — HTTP
2. ECS tasks (managed by ECS itself) - HTTP
3. Lambda functions — HTTP request is translated into a JSON event (based by an concept of the serverless in AWS)
4. IP Addresses — must be private IPS
5. ALB can route to multiple target groups
6. Health checks are at the target group level 


