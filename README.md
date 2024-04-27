# AWS DMS Database Migration Project 

## Description

This project involves migrating a web application from an on-premises environment to AWS. The on-premises environment consists of a virtual web server and a MariaDB database server, both simulated using EC2 instances.

This project is part of Adrian Cantrill's labs: [learn-cantrill-io-labs](https://github.com/acantril/learn-cantrill-io-labs)

![Overall Architecture](https://github.com/guilhermefgonc/aws-dms-db-migration/blob/main/images/ARCHITECTURE-OVERALL.png)

### Stage 1: Provisioning the Environment

   The base lab infrastructure was provisioned using the following CloudFormation template: [DMS.yaml](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/quickcreate?templateURL=https://learn-cantrill-labs.s3.amazonaws.com/aws-dms-database-migration/DMS.yaml&stackName=DMS)

   CloudFormation is a service that facilitates modeling and setting up AWS resources. You create a template describing all the desired resources, and CloudFormation handles provisioning and configuration.

   ![Stage 1 Architecture](https://github.com/guilhermefgonc/aws-dms-db-migration/blob/main/images/ARCHITECTURE-STAGE1.png)

### Stage 2: Establishing Private Connectivity Between On-Premise and AWS

   VPC Peering Connections were used to establish a connection between the environments. VPC Peering Connection is a networking connection between two VPCs that enables routing traffic between them using private IPv4 addresses. Route Tables were also created between the on-premises side and the AWS side.

   Route Tables contain a set of rules (routes) that determine where network traffic from your subnet or gateway is directed.

   ![Stage 2 Architecture](https://github.com/guilhermefgonc/aws-dms-db-migration/blob/main/images/ARCHITECTURE-STAGE2.png)

### Stage 3: Creating and Configuring the AWS Side Infrastructure

   Initially, the RDS Instance was configured, starting with the Subnet Group, followed by the RDS Instance. RDS is a service that simplifies setting up, operating, and scaling a relational database in the AWS Cloud.

   Next, an EC2 Instance was created, and WordPress requirements were installed. WordPress content was then migrated from the on-premises server to the AWS server.

   ![Stage 3 Architecture](https://github.com/guilhermefgonc/aws-dms-db-migration/blob/main/images/ARCHITECTURE-STAGE3.png)

### Stage 4: Migrating the Database

To migrate the on-premises database, AWS DMS (Database Migration Service) was utilized. A DMS Instance and endpoints were created and configured. Subsequently, a migration task was created. The DMS task specifies the tables and schema for the migration, and the data is migrated to the RDS Instance.

![Stage 4 Architecture](https://github.com/guilhermefgonc/aws-dms-db-migration/blob/main/images/ARCHITECTURE-STAGE4.png)
