# Elastic Block Storage Volume

## What is EBS 
1. It is an Network drive(not a physical drive) that is attached to the EC2 instance
2. we can terminate the instance and attach the same EBS volume to the other instance and we get our data back
3. Amazon EBS Multi-Attach feature enables you to attach a single Provisioned EBS , IOPS SSD ( io1 or io2 ) volume to multiple instances that are in the same Availability Zone.
4. To use the attached EBS volume to the instance, Its bit complicated, so follow the link https://docs.aws.amazon.com/ebs/latest/userguide/ebs-using-volumes.html
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/16ad9c78-341e-42a2-a825-0a38d0fe70e2)

## EBS snapshots
1. we can make a backup of the EBS volume at a point in time
2. Not necessracy to detach volume to do snapshot, but recommended
3. can copy snapshots across AZ or regions

## EBS snapshots features
1. EBS Archive -  We can archive the EBS snapshot, it is 75% cheaper, but it takes 24 - 72 hrs to restore the archive
2. recycle bin for EBS snapshots - we can recover if deleted accidentally from 1 day to 1 year
3. Fast snapshot restore -  It is used to force full initialization of the snapshot to have no latency on the first use, but costs alot of money
