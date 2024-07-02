# RDS, Aurora, Elastic Cache

## Amazon RDS overview
1. RDS stands for Relational Database Service
2. It's a managed DB service for DB use SQL as a query language.
3. It allows you to create databases in the cloud that are managed by AWS
4. some database services AWS offers
   * Postgres
   * MySQL
   * MariaDB
   * Oracle
   * Microsoft SQL Server
   * IBM DB2
   * Aurora (AWS Proprietary database)

## advantages of using the RDS vs deploying database on EC2
1. Automated provisioning, OS patching
2. Continuous backups and restore to specific timestamp (Point in Time Restore)!
3. Monitoring dashboards
4. Read replicas for improved read performance
5. Multi AZ setup for DR (Disaster Recovery)
6. Maintenance windows for upgrades
7. Scaling capability (vertical and horizontal)
8. Storage backed by EBS (gp2 or io l)
9. But we cannot SSH into the RDS instances as it is managed by the AWS completely

## Auto scaling for the storage RDS
1. Helps you increase storage on your RDS DB instance dynamically When RDS detects you are running out of free database storage, it scales automatically 
2. Avoid manually scaling your database storage If you have to set Maximum Storage Threshold (maximum limit for DB storage) 
3. Automatically modify storage if: 
  * Free storage is less than 10% of allocated storage
  * Low-storage lasts at least 5 minutes
  * 6 hours have passed since last modification
4. Autoscaling increases storage by 10 GiB, 10% of the current storage, or the predicted storage growth for the next seven hours, whichever is greatest.
Useful for applications with unpredictable workloads

## Read replicas in RDS
1. Read replicas databases are only for the reads (we cannot perform the insert delete and update select operations on the read replicas)
2. As the name indicates it helps us to scale your reads
3. If the application is doing more reads then the read replicas will be created
4. They can be created Up to 15 Read Replicas Within AZ, Cross AZ or Cross Region
5. Replication is ASYNC, so reads are eventually consistent
6. Replicas can be promoted to their own DB (lets say the replicated DB can be converted to their own database and the replicated DB will be out form the replication mechanism and it wil be the own database)
7. Applications must update the `connection string` to leverage all the read replicas connected and then convert one of them to the DB
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/b0e1e5f8-ee14-4acf-9e33-c548ddf45e22)

## RDS read replicas -use case
Lets say we want to perfome the analytics and reporting on the production database, running this might effect the production database and eventually effects the performance of the production applciation. Here the read replica DB helps to perform this reporting and doesnt effect any of the applciation performance ![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/14e4e740-4b38-4d23-a4d0-60bc10c92d7b)

## RDS Read replicas -- Network cost
1. In AWS there is a network cost when data goes from one AZ to another
2. But as the RDS is a managed service, there will be no cost for the data transfer to be payed foe the RDS read replicas 
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/0b8e0e85-8fda-4758-829e-dc3414677ec9)

## RDS Multi AZ (Disaster Recovery)
1. This is a SYNC replication
2. There will be by default an SYNC replication DB in an other AZ for the disaster recovery
3. if there is an Failover for the master DB the instance standy will be becoming master db, to increase the avaliability
4. not used for the scaling just a backup server no reads can be performed or cant be accessed by us the standyby DB
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/1946305a-c699-4bd4-9ff7-ab1f8bec4075)

## RDS custom
1. we dont have access to the underlying hardware for the RDS databases, they are fully managed by the AWS, but we RDS custom we can Manage the oracle and Microsoft SQL server Databse with OS and database customization
2. RDS: Automates setup, operation, and scaling of database in AWS
3. RDS Custom: access to the underlying database and OS so you can Configure settings, Install patches, Enable native features , Access the underlying EC2 Instance using SSH or SSM Session Manager
4. we should De-activate Automation Mode to perform your customization
5. better to take a DB snapshot before customization

## RDS vs. RDS Custom 
• RDS: entire database and the OS to be managed by AWS 
• RDS Custom: full admin access to the underlying OS and the database

## Amazon Aurora
1. Aurora is a proprietary technology from AWS (not open sourced)
2. Postgres and MySQL are both supported as Aurora DB (that means your drivers will work as if Aurora was a Postgres or MySQL database)
3. Aurora is "AWS cloud optimized" and claims 5x performance improvement over MySQL on RDS, over 3x the performance of Postgres on RDS
4. Aurora storage automatically grows in increments of 1OGB, up to 128 TB
5. Aurora can have up to 15 replicas and the replication process is faster than MySQL (sub 10 ms replica lag)
6. As the aurora is cloud native it has high avaliability
7. Aurora costs more than RDS (20% more) — but is more efficient

## aurora high avaliability and read scaling
1.  Aurora stores 6 copies of your data across 3 AZ every time we store the data
2.  Aurora can perform the self healing when its corrupted or bad, then it does the self healing with the peer-to-peer replication in the backend
3.  storage is triped across 100s of volumes, we dont need to interact wiht the storage, that is completely managed by the AWS <br/>
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/3a3eb9f4-7e49-4e89-a649-22d36e523775)

## Aurora as a cluster
Load balancing happens at the connetion level not the statement level
