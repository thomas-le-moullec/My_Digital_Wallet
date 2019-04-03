# My_Digital_Wallet
Digital Wallet that aim to execute an instrument following a specific protocol. The Service will offer an open API, a GUI for the end User and a backend processing solution in charge of handling Batch Transactions coming from different producers. 
For the PoC, the solution will be handling only one geographical zone (Hong Kong) and only one currency (US Dollar).
Nevertheless, the producers can differ and send different types of transactions.
Resiliancy, Maintenability and Fault Tolerance would be a priority for this solution.

## Industry Context
**To Define**

## Introduction and Concept
**To Define**
### Statistics and Game Changer Event

## Executive Summary
### Problem
**To Define**

### Features
**To List**

### Targets
A digital wallet is linked into an end-user, bank, or vendor application and provides the application with instrument management and protocol management services.
The Digital Wallet will provide a GUI for the End-User, the first version will be a web application.
Providing a SAAS would simplify the process of keeping protocol and software up to date.

### Technology and Architecture
In order to develop a scalable and fast Service, the Technological Stack will be based on Amazon Web Services. This choice is crucial for the potential deployment over different regions and currencies.

#### Potential AWS Services:
* **CodePipeline** for the Continuous Delivery
* Simple Storage Service (**S3**) for storing transactions
* **CodeCommit** for the hosting of highly scalable private Git repositories and anticipate future contributors
* **Elastic Beanstalk** for the automatic deployment
* **CloudFront** to deliver the fastest Services to end user
* **CloudFormation** to describe and provision all the infrastructure resources
* **Route53** for DNS alias and Balancing of Traffic
* **API Gateway** for API handling
* **VPC**  to split Development, Production and Management VPC for PCI DSS standards concerns.
* **Kinesis Stream and Kinesis Firehose** for Data ColleThomas LE MOULLECction
* **Dynamo DB** for Transactions Storage
* **Athena** or **RedShift** or **Kinesis Analytics** for transactions analysis (Suspicious / Fraud / Data Analytics)
* **CloudTrail** and **CloudWatch** For monitoring of resources usage, calls and status.
* **Glacier** for old transactions and old data analytics
* **IAM** for roles, groups and users rights to assure maximum security of accounts and resources

### Others Services:
    * Github
    * CloudCraft
    * Draw.io
    * Trello
    * Testing: TDD ?

### Logical Flow and Solution Architecture

1. Inputs
    * Frequency: Can be either Daily or Periodic
    * Producers: Different Producer with different frequency of production at different time
    * Type of Data: Can vary between CSV, JSON and XML
    * Sending Method: Can send data through Batch Process with a minimum of 3 different Client Accounts for the producer
    * (Prototype) Producer can be a small shop (E.g: SevenEleven) where you can top up your Card and pay with your Card.
    * (Vision) Producer can use a Payment Gateway, then the prepaid card can be used online and in-store
    * (Vision) Producer can potentially send periodic Data updates to give information on the system.

2. Transaction
    * Format: CSV, JSON, XML
    * Transaction is either a top up or a payment
    * Columns: TxDate (Date), ProducerId (Int), ClientId (Int), ProducerLocation (String), TxId (String), TxType (TopUp or Payment), Amount (Int)


3. Back End Processing
    * Auto-Scheduled job Update the Database by processing the incoming transactions.
    * The processing requires some rules to accept a transaction and a batch job
    * The processing needs to consider a Reconciliation phase to handle potential issues such as Batch issues, double batch etc...
    * Maintening a Database for Producers data (Batch job History, Failures etc...), this can be used for Financial Services Internal Tool
    * Update User view once the transactions have been confirm. Can also display "In process" if the Reconciliation or checks are running.

4. Consumer App
    * Check the Updated Balance
    * Check the Not Real Time Historic of Transactions with the Location, the Date and the Name of the Producer

5. Financial Services Internal Tool
    * Possibility to suspend Producer (Endpoint to stop their jobs), contact Producer or Client (E.g: Producer with suspicious risk ; 'did you do this transaction ?').
    * The Reconciliation and Potential Data Analytics reports can be deliver to the team (Finance and Operations) with potential action to respond to the facts
    * A Dashboard for the executives, a nice way of summarizing operations over the time (Total Volume, Reconciliation and Exceptions Stats, Operation Health Stats).

### Customer Experience - User Manual 

### Standards

1. **PCI DSS**: This Security standards will impact the Cloud Architecture a lot. We will use the Standardized Architecture for PCI DSS on the AWS Cloud to design a robust architecture (From AWS Professional Services).

### Costs
**To Define**

### Vision
The project aims to be used with another project that I am building: a Payment Gateway.

### Human Resources
1 person: **Thomas LE MOULLEC**

### Frequently Asked Questions

### Acknoledgements

Swaperoo - Stanford: https://s3.ap-northeast-2.amazonaws.com/tslemoullec-docs/SWAPEROO_A_Simple_Wallet_Architecture_for_Payments.pdf

### References

AWS Data Warehouse: https://aws.amazon.com/data-warehouse/
AWS CodePipeline setup: https://aws.amazon.com/getting-started/tutorials/continuous-deployment-pipeline/