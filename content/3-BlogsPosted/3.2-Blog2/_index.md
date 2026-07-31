---
title: "Blog 2"
date: 2026-07-29
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

## Getting Started with AWS Serverless: The Serverless Services I Chose to Build the Workshop

When selecting technologies for the workshop, I was recommended to use a Serverless architecture on the Amazon Web Services (AWS) platform. Initially, I thought Serverless simply meant "no need to rent servers" or "no need to install Linux." However, after reading official AWS documentation and directly deploying my first application, I realized that this concept is much broader.
Serverless is not an isolated service, but an application development model. In this model, developers no longer need to worry about managing servers, updating operating systems, or configuring scalability. Instead, AWS takes full responsibility for operating the infrastructure, allowing developers to focus solely on solving business logic problems.
---
Is Serverless Really "Serverless"?
This was my most common misconception when I first started exploring it. In reality, servers still exist, but developers do not need to manage them directly. AWS automatically provisions compute resources, deploys applications, monitors status, and scales server capacity up or down based on incoming traffic.
In a Serverless architecture, execution follows an event-driven model. When an event occurs—such as a user sending an HTTP request or uploading a file—AWS automatically triggers the corresponding code. Once execution completes, resources are released rather than remaining continuously active. Consequently, the system saves costs by paying only for the time resources are actively used.
---
AWS Lambda - The Heart of Serverless Architecture
In the AWS Serverless ecosystem, the most critical service is AWS Lambda. Lambda enables developers to deploy business logic functions without managing servers. When an event takes place, Lambda initializes the execution environment, runs the code, and returns the result.
At first, I thought splitting code into multiple Lambda functions would make the system overly complex. However, after studying AWS documentation, I realized this is a recommended design pattern because each Lambda function handles a single responsibility, making maintenance and scaling much simpler.
---
API Gateway - The Front Door of the System
While Lambda handles business logic processing, Amazon API Gateway acts as the "front door" for the entire system. Whenever a user sends a request from the React application, API Gateway receives it, authenticates the user, routes it to the appropriate Lambda function, and returns the result to the client.
Previously, I viewed API Gateway merely as a place to define APIs. However, after practical deployment, I learned that this service also manages tasks such as JWT Token validation, CORS configuration, Rate Limiting, and activity logging. As a result, code inside Lambda functions can stay fully focused on business logic instead of infrastructure concerns.
---
DynamoDB - A Database Designed for Serverless
For Serverless applications, AWS recommends Amazon DynamoDB because it is a NoSQL database featuring automatic scaling and extremely low latency.
An important lesson I learned is that DynamoDB should not be designed like traditional relational databases. Instead, AWS recommends designing around Access Patterns—focusing on how data will actually be queried in practice. For instance, rather than scanning an entire table to find classes taught by an instructor, I use a Global Secondary Index (GSI) to perform targeted Query operations. This approach makes system operations significantly more efficient as data grows.
---
Amazon Cognito - Do Not Build Custom Authentication Systems
Initially, I thought writing custom authentication logic using Lambda would offer greater flexibility. However, after reading AWS documentation, I realized that Cognito already provides critical out-of-the-box features such as user authentication, password management, JWT Token issuance, and support for standard security practices.
---
Conclusion
After researching and building the project, my biggest mindset change was recognizing that Serverless is not just about AWS Lambda. A complete Serverless system relies on the seamless integration of multiple services, including API Gateway, Cognito, DynamoDB, IAM, and security mechanisms.
---
References:
* "What is AWS Lambda?". (https://docs.aws.amazon.com/lambda/latest/dg/welcome.html)
* "What is Amazon API Gateway?". (https://docs.aws.amazon.com/.../developerguide/welcome.html)
* "What is Amazon DynamoDB?". (https://docs.aws.amazon.com/.../develop.../Introduction.html)
* "Amazon Cognito user pools". (https://docs.aws.amazon.com/.../cognito-user-pools.html)
---
Blog's link: https://web.facebook.com/groups/awsstudygroupfcj/permalink/2227753051322988/?rdid=4BxzLitflB0OFY8E#
