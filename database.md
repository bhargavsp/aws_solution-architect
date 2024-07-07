# Database

## How to choose the Right database
1. We have a lot of managed databases on AWS to choose from 
2. Questions to choose the right database based on your architecture: 
3. Read-heavy, write-heavy, or balanced workload? Throughout needs? Will it change, does it need to scale or fluctuate during the day? 
4. How much data to store and for how long? Will it grow? Average object size?
5. How are they accessed?
6. Data durability? Source of truth for the data ?
7. Latency requirements? Concurrent users?
8. Data model? How will you query the data? Joins? Structured? Semi-Structured?
9. Strong schema? More flexibility? Reporting? Search? RDBMS / NoSQL?
10. License costs? Switch to Cloud Native DB such as Aurora? ![image](https://github.com/bhargavsp/aws_solution-architect/assets/45779321/44586337-7579-4fbf-83b0-5bcc3fcb97f3)

## Database Types
1. RDBMS SQL/ OLTP): RDS,Aurora - great for joins 
2. NoSQL database — no joins, no SQL : DynamoDB (—JSON , ElastiCache key / value pairs), Neptune (graphs), DocumentDB (for MongoD ), Keyspaces for Apache Cassandra) 
3. Object Store: S3 (for big objects) / Glacier (for backups / archives) 
4. Data Warehouse (z SQL Analytics / Bl): Redshift (OLAP),Athena, EMR 
5. Search: OpenSearch (JSON) — free text, unstructured searches 
6. Graphs: Amazon Neptune — displays relationships between data 
7. Ledger. Amazon Quantum Ledger Database 
8. Time series: Amazon Timestream

 
