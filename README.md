# Project 4: Serverless Data Engineering Pipeline
### Project Objectives
- Reproduce the architecture of the example serverless data engineering project or perform something similar using only serverless technologies
- Enhance the project by extending the functionality of the NLP analysis: adding entity extraction, key phrase extraction, or some other NLP feature or doing Applied Computer Vision.
## Introduction
In this project, I will learn to build a serverless data engineering pipeline.
## Structure Diagram
![55354483-bae7af80-547a-11e9-9909-a5621251065b](https://user-images.githubusercontent.com/84234596/228644401-a6a3406a-af7c-4504-a3e3-38293c3272c7.png)
## Step
### 1. Create a table in DynamoDB
- DynamoDB: A fast and flexible NoSQL database service for any scale
- Table: lambda-dynamodb-stream
- partition key: id(String)  
### 2. Create lambda functions and add trigger
- AWS lambda
- Function1: ProcessDynamoDBRecords
  - add trigger, remember to add the DynamoDB permission for this IAM role
- Function2: updateTable. 
### 3. Setup an Amazon EventBridge schedule*  
- choose API: AWS Lambda and `invoke`  
- to invoke the `updateTable` lambda function every 60 seconds  
### 4. Result
- The EventBridge will invoke the `updateTable` function every minute, and it will insert a new item in the table in the DynamoDB;  
- The `ProcessDynamoDBRecords` will detect the change of DynamoDB database, and it will write the result to S3 bucket.  
## Week 9 progress
**1.AWS lambda**
- https://github.com/noahgift/awslambda
## Week 10 progress
CloudWatch Timer: schedule a 30-second job to code the lambda function;  
Lambda function: update data from the database;  
Log Lambda function: detect the changes from the database, then create some logs to S3;  
**1.AWS S3**
<img width="1023" alt="截屏2023-04-05 22 08 24" src="https://user-images.githubusercontent.com/84234596/230254462-78ad70f5-7a04-49f0-8037-cb6a372d6436.png">
**2.lambda function**
- Revisit project 3.
