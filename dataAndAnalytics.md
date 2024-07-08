# data and analytics

## Amazon Athena
1.  It is a serverless query service to analyze the data that is stored in the s3 buckets
2.  uses standarad SQL language to query the files (build on presto)
3.  pay $5.00 per TB of data scanned, as it is a serverless
4.  commonly used with the amazon quicksight for reporting/dashboards 
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/00676d52-8f7a-42c2-a486-738f3448e700)

## athena - performance improvement
1. Basically we are paying for the TB data scanned in S3 bucket, so we should use a technique to less scan the data for cost-savings
2. we use the columnar data for the cost savings
3. the recommended formats to scan for the amazon athena are Apache Parquet or ORC is Huge performance improvement
4. we use the Amazon Glue to convert your data as an ETL job using the Parquet or ORC
5. the other technique used to lower the cost for less data scanning are compress data into zip for smaller retrivals and the data partition for easy querying on virtual columns
6. ![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/79993c99-65cb-47cf-9746-4d9b554e14e5)
7. we can also run the data scan queries on the other data stored in relational, non-relational, object and custom data sources (on-premises) using the Data source connectors that run on AWS lambda and stored the results back on the amazon s3
8. ![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/cf8932f7-0e2a-4cfb-b15e-18f844abef33)

## Amazon Redshift
1. Redshift is a type of RDBMS (database) but it doesnt run the online transaction processing (OLTP) as MySql, Redshift is optimized for Online Analytical Processing (OLAP) and the best data warehouse
2. It is a columnar storage of data and parallel query engine
3.  vs Athena- In Redshift we should load all the data, so it has much faster queries, joins, integrations as it used and concept of indexes adn it builds indexes to have this very high performance for a data warehouse.
4.  If its an ad hoc queries (un scheduled, user-defined searches that allow users to access specific information from a data set on demand)athena is the best choice
5.  You can configure Amazon Redshift to automatically copy snapshots (automated or manual) of a cluster to another AWS Region
6.  
## redshift cluster
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/ee18617f-7f32-4971-ba92-3113f7c7dc2b)

## diff between redshift vs athena
Data Structure: Because Redshift requires you to organize data into data sets within clusters, it works best for data that is structured. In contrast, Athena can analyze raw, unstructured data spread across S3.

## Loading data into the redshift
We have 3 ways to load data into the redshift
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/5c630465-f98c-46f5-92d6-4be55bd48108)

## we can also scan and analyse the data wihtout loading it into the redshift (redshift spectrum)
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/989d1f62-3684-445b-a8e4-c3d23c54f475)

## Amazon Opensearch service
1. previosuly it is called amazon ElasticSearch
2. It is basically used for the search in the database apart from using the primary key and the indexes
3. Here it searchs the matches, we can use this as an compliment to the database for the searches
4. there are 2 modes to provision it
   * managed cluster
   * serverless cluster
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/c9076aec-a574-4862-a142-b2dbbd833179)
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/3becbb38-6f10-4adb-b35b-2a29e18db495)
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/87431584-312a-4c3a-8e62-84645f538848)

## Amazon EMR
1. EMR stands for Elastic MapReduce
2. used for the creating Hadoop clusters to analyze and process vast amount of data

## Amazon QuickSight
Serverless machine learning powered business intelligence service to create interactive dashboards
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/9c700d8c-4700-404a-b01b-dd0384293313)

## Glue
Glue is an ETL
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/cee26d84-4eea-4007-bf71-2cd76358ff20)
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/290ce065-1c3e-4cd6-8df5-981fb0b678e5)

## Glue Data catalog
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/b5d8fccf-2258-442e-a2e4-90a7d124fb27)

## aws lake formation
 1. Data lake: It is a central place to have all your data for analytics purposes
 2. lake formation has blueprints of most of the aws service to connect to
 3. it basically gives the fine-grained access controls for your applciations at the row and the column level only to the services they are connected apart from individual security we give on each service to access the data  
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/0214eeeb-70a9-457a-9acc-7a122353e7e5)

## Kinesis data analystics for SQL applications
1. Real-time analytics on Kinesis Data Streams & Firehose using SQL 
2. Add reference data from Amazon S3 to enrich streaming data
3.  Fully managed, no servers to provision
4.  Automatic scaling
5.  Pay for actual consumption rate
6.  Output: 
* Kinesis Data Streams: create streams out of the real-time analytics queries 
* Kinesis Data Firehose: send analytics query results to destinations 
* Use cases: 
* Time-series analytics 
* Real-time dashboards 
* Real-time metrics
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/6e93aa48-e07c-495c-99f6-1df5f082a3f1)

## kinesis data analystics for apache flink
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/7a0cf9ac-c3e6-4d70-ae65-9b835524ef49)

## Amazon Managed Streaming for Apache Kafka (Amazon MSK) 
1. Alternative for amazon Kinesis (used for streaming services)
2. ![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/ef2cb6ad-6af2-4d5b-bd63-641c7d4df47d)

## Big data ingestion pipeline
![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/6ba11663-e9ed-4e18-a851-b797ffd58335)

## Diff b/w Kinesis and Redshift
Amazon Kinesis is a streaming analytics suite for data intake from video or other disparate sources and applying analytics for machine learning (ML) and business intelligence. Amazon Redshift is a hosted data warehouse solution, from Amazon Web Services.
