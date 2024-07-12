# AWS Snow Family

## Snow Family
offline devices, Highly-secure, portable devices to collect and process data at the edge, 
and migrate data into and out of AWS 
Snowball cannot import the data to S3 Glacier directly, we have to upload data to S3 and use the life cycle policies
![image](https://github.com/user-attachments/assets/ad04c762-bae2-43ea-bdc8-45e703ac2796)

## AWS OpsHub
used by the snow family devices, you needed a cli instead there is an AWS OpsHub to monitor and do other tasks for the snow devices

## AWS FSx
![image](https://github.com/user-attachments/assets/4d24d344-bd48-45be-ac10-a77e7898eba6)

## AWS storage gateway
1. It is a Bridge between on-premises data and clocd data
2. Use cases: 
  * disaster recovery
  * backup & restore
  * tiered storage
  * on-premises cache & low-latency files access
3. Types of Storage Gateway: 
  * S3 File Gateway
  * FSx File Gateway
  * Volume Gateway
  * Tape Gateway
4. For using the storage gateway we have to install the gateway access on the on-premises data center, to avoid it or if we dont have VM's in the on-premises we can buy the **storage Gateway Hardware Appliance** from amazon, it is compartable to all the storage gateways
![image](https://github.com/user-attachments/assets/49170506-a793-46ea-b3ab-bea1127b2aa0)

## AWS Transfer Family
1. A fully-man2ged service for file transfers into and out of Amazon S3 or Amazon EFb using the FTP protocol 
2. Supported Protocols 
  * AWSTransfer for FTP (File Transfer Protocol (FTP))
  * AWSTransfer for FTPS (File Transfer Protocol over SSL (FTPS))
  * AWSTransfer for SFTP (Secure File Transfer Protocol (SFTP)) 
3. Managed infrastructure, Scalable, Reliable, Highly Available (multi-AZ)
4. Pay per provisioned endpoint per hour + data transfers in GB
5. Store and manage users' credentials within the service 
6. Integrate with existing authentication systems (Microsoft Active Directory, LDkP Okta, Amazon Cognito, custom)
7. Usage: sharing files, public datasets, CRM, ERP
![image](https://github.com/user-attachments/assets/d1e67b39-4571-40bb-90d1-421f07bed4c7)

## Storage Comparision
* S3: Object Storage 
* S3 Glacier: Object Archival 
* EBS volumes: Network storage for one EQ instance at a time 
* Instance Storage: Physical storage for your EC2 instance (high IOPS) 
* EFS: Network File System for Linux instances, POSIX filesystem 
* FSx for windows: Network File System for windows servers 
* FSx for Lustre: High Performance Computing Linux file system 
* FSx for NetApp ONTAP: High OS Compatibility 
* FSx for OpenZFS: Managed ZFS file system 
* Storage Gateway: S3 & FSx File Gateway; Volume Gateway (cache & stored),Tape Gateway 
* Transfer Family: FTP FTPS, SFTP interface on top of Amazon S3 or Amazon EFS 
* DataSync: Schedule data sync from on-premises to AWS, or to AWS 
* Snowcone / Snowball / Snowmobile: to move large amount of data to the cloud, physically 
* Database: for specific workloads, usually with indexing and querying
