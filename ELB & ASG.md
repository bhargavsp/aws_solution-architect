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



