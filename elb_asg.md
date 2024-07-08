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
4. The health check configuration includes information like the protocol, ping port, ping path, response timeout, and health check interval.

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
4. redirect of the traffic from HTTP to HTTPS (level 7)
5. Routing tables to different target groups: 
• Routing based on path in URL (example.com/users & example.com/posts)
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/263b6e7c-96a2-4de3-95f2-cac8e7932098)
• Routing based on hostname in URL (one.example.com & other.example.com) <br/>
• Routing based on Query String, Headers (example.com/users?id= 1 23&order=false) <br/>
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/e79c9c2b-02cb-47b4-8b1a-a3044a55af99)
7. ALB are a great fit for micro services & container-based application (example: Docker & Amazon ECS)
8. Has a port mapping feature to redirect to a dynamic port in ECS


## target groups in the Application load balancing
Taret groups can be created of multiple types
1. EC2 instances (can be managed by an Auto Scaling Group) — HTTP
2. ECS tasks (managed by ECS itself) - HTTP
3. Lambda functions — HTTP request is translated into a JSON event (based by an concept of the serverless in AWS)
4. IP Addresses — must be private IPS
5. ALB can route to multiple target groups
6. Health checks are at the target group level
7. we can also give the fixed hostname for the APplication load balancer
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/f23e10af-bd33-479f-b97d-1177585c84b2)

## Network load balancer
1. forward TCP & UDP traffic to your instance (layer 4)
2. less latency ~ 100ms (vs ALB ~400ms) means handle millions of requests per second
3. NLB has 1 static IP per AZ and also support assigning Elastic IP (it is helpful for listing specific IP, for example when there is condition of using 1,2,3 IPs to access our application
4. we can use the HTTP in the backend, but still it transfer the traffic in the TCP, UDP in the frontend
5. the NLB supports HTTP health checks as well as TCP and HTTPS
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/718e2103-11c2-44ac-a509-fc96d19e60d1)

## target groups in the Network load balancing
1. they can support the health chekcs support of the tCP, HTTP, HTTPS protocols
2. The target groups in the NLB can be the EC2 isntances combined in a target group or the IP address (the private IP of the serveer or the EC2 isntances in the on-premises must be hard coded) combined in the target group
3. we can also have the application load balancer inside the netwrok the load balancer as the NLB supports the HTTP or HTTPS requests in the backend while communcicating wiht the EC2 instsances
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/33fbd9ef-9675-457b-954c-7b6fb5ed8250)

## gateway load balancer
1. for creating a gateway load balancer and to pass the incoming traffic into the target group of 3rd party network virtual appliances (EC2 instances) in AWS we should configure the `Route Table in the VPC`
2. here at the Target group of 3rd party virtual appliances they analyse the incoming traffic adn drop the reuest if it is malicious
3. It works at the very low level Level 3(Network layer) - IP packets
4. how it works is it works with the 2 functions
5. Transparent Network Gateway - single entry/exit for all traffic
6. load balancer -  distributes the traffic to your virtual appliances
7. uses the GENEVE protocol on port 6081
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/cb6309dd-079f-42ca-8b85-87d9609a7687)

## target groups in the Gateway load balancing
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/6ba5e665-3e39-4c3e-900f-3d0c13a6f646)

## sticky sessions (session Affinity)
1. It is possible to implement stickiness so that the same client is always redirected to the same instance behind a load balancer (this is done because the particukar client doesnt loss the session data while he is working ex: logins)
2. This works for Classic Load Balancer, Application Load Balancer, and Network Load Balancer
3. The "cookie" used for stickiness has an expiration date you control
4. The cookies are not required for hte NLB
5. Use case: make sure the user doesn't lose his session data
6. NOTE: Enabling stickiness may bring imbalance to the load over the backend EC2 instances, incase if we have a sticky user for the single EC2 instance

## types in the sticky session cookies
1. Application-based cookies
   * Custom cookie: 
      * Generated by the target
      * Can include any custom attributes required by the application
      * Cookie name must be specified individually for each target group
      * Don't use AWSALB, AWSALBAPP, or AWSALBTG (reserved for use by the ELB) 
   * Application cookie:
      * Generated by the load balancer 
      * Cookie name is AWSALBAPP
2. Duration-based Cookies 
   * Cookie generated by the load balancer 
   * Cookie name is AWSALB for ALB, AWSELB for CLB
   * They are terminated based on the cookies

## ELB - cross zone Balancing
1. for application load balancer, the cross zone load balancing is is enabled by default (can be disabled at the target group level)and there is not extra charges for inter AZ data change
2. For NLB and GLB, you pay charges for using the inter AZ data if enabled
3. for CLB disabled by default, no charges even if enabled for the inter AZ data change 
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/eca1c15e-715f-439c-bb17-3ecdc86101a2)

## Connection Draining or Deregistration Delay 
1. Connection draining is a process that ensures that existing, in-progress requests are given time to complete when a VM is removed from an instance group or the instance in unhealthy condition or the instance is de-registering or when an endpoint is removed from network endpoint groups (NEGs) that are zonal in scope.
2. Feature naming
   * Connection Draining — for CLB
   * Deregistration Delay — for ALB & NLB 
3. draining connection hold will be between 1 to 3600 seconds (default: 300 seconds)
4. Can be disabled (set value to 0)
5. Set to a low value if your requests are short
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/6f6612c3-487c-4d3a-9cae-4f5e7f4ec036)

## ASG Auto scaling Group in AWS
1. In real-life, the load on your websites and application can change
2. In the cloud, you can create and get rid of servers very quickly
3. The goal of an Auto Scaling Group (ASG) is to: 
   * Scale out (add EC2 instances) to match an increased load
   * Scale in (remove EC2 instances) to match a decreased load
   * Ensure we have a minimum and a maximum number of EC2 instances running
   * Automatically register new instances to a load balancer
   * Re-create an EC2 instance in case a previous one is terminated (ex: if unhealthy)
   * ASG are free (you only pay for the underlying EC2 instances)
   * ASG maintains the desired capacity all the time
4. using the load balancer with te auto scalling group <br/>![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/ac4139a8-4a16-4305-8dd5-45639c5e1152)
5. Auto scaling Group attributes uses launche templates<br/> ![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/5ade7713-bb37-46dc-9842-e61d9db60a66)
6. Auto scaling with the `Cloud watch alarms`
7. based on the cloud watch metrics such as average cpu are computed for the overall ASG instances and scalein or scale out policies are created 

## Auto scaling groups - scaling policies
1. Dynamic Scaling:
   * Target Tracking Scaling
     * Simple to set-up
     * Example: I want the average ASG CPU to stay at around 40% 
   * Simple Scaling: 
     * When a CloudWatch alarm is triggered (example CPU > 70%), then add 2 units
     * When a CloudWatch alarm is triggered (example CPU < 30%), then remove I
   * Step scaling:
     * Even this works based on the clodwatch alarm, but if the cpu utilization is 60% add 1, if it is 80% add 2 instanes. if 90% add 3 instances
     * we can specifiy the steps to increase the number of instances based on the %age
2. Scheduled actions 
   * Anticipate a scaling based on known usage patterns
   * Example: increase the min capacity to 10 at 5 pm on Fridays
3. Predictive scaling: It is based on the Machine Learning metrices. continously forecast load and schedule scaling based on the forecast (ex: big billion day)

## Good metrics to scale on
1. CPUUtilization: Average CPU utilization across your instances
2. RequestCountPerTarget: to make sure the number of requests per EC2 instances is stable <br/> ![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/b54f5dfe-985d-4536-a428-c5ed1194c212)
3. Average Network In / Out (if you're application has too much uploads and downloads, and you know the network is going to be down)
4. Any custom metric (that you push using CloudWatch)

## ASG - scaling cooldowns
1. ASG after scale in/out the ASG enters the cooldown period (default 300 seconds)
2. During the cooldown period the ASG will not launch or termincate the new instances
3. The reson for the cooldown period is, we are giving sometime for the metrices to  be stabilize, and to see the what the new metric will come
4. The advice here is to use the ready-to-use AMI to reduce the configuration time in order to be serving the request fasters and reduce the cooldown period
5. we need to have something like the detailed monitoring for the ASG to get the access to metrics every one minute and to make sure that you have these metrics beign updated fast enough
