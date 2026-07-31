---
title: "Blog 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

# What is AWS SAM? Why Isn't AWS SAM Considered an AWS Serverless Service?

* After exploring core AWS Serverless services like Lambda, API Gateway, and DynamoDB, I started following application deployment tutorials in the official AWS documentation. What surprised me was that almost every example used the "AWS Serverless Application Model (AWS SAM)". However, when I returned to the AWS Serverless overview page, I didn't see AWS SAM listed alongside services like Lambda or EventBridge.
* This led me to ask: "If AWS SAM is so widely used, why isn't it considered a Serverless service?"
* After reading the official documentation and using AWS SAM throughout the workshop development process, I realized that AWS SAM is "not an application runtime service," but rather a "development tool" that helps define and deploy entire Serverless infrastructures as code.
---
Infrastructure as Code - A New Mindset in Infrastructure Management

* Previously, I thought deploying an application to AWS was primarily done through the AWS Management Console web interface (GUI). For example, to create a Lambda Function, I would log into the AWS Console, click "Create Function," and then proceed to create API Gateway, DynamoDB, IAM Roles, and connect these services together.
* This approach is quite intuitive for small applications. However, as the number of resources grows, managing everything via the GUI becomes difficult and error-prone. Simply forgetting a configuration or misconfiguring access permissions can cause the entire system to behave unexpectedly.
* That is why AWS encourages using "Infrastructure as Code (IaC)"—a method of defining the entire infrastructure using source code instead of manual operations. This way, infrastructure can be stored in Git, track change history, and be redeployed multiple times with consistent results.
---
What is AWS SAM?
* According to official AWS documentation, the "AWS Serverless Application Model (AWS SAM)" is an open-source framework built on AWS CloudFormation to simplify developing and deploying Serverless applications.
* In other words, AWS SAM does not replace Lambda or API Gateway. Instead, AWS SAM helps developers define these resources in a single configuration file, typically "template.yaml".
* For instance, instead of creating each Lambda Function, API Gateway, and DynamoDB Table through the web interface, developers simply define the resources in "template.yaml". AWS SAM then automatically transforms this definition into the corresponding AWS resources via CloudFormation.
* This was a turning point in how I viewed system deployment. Previously, I thought application source code was the most critical part. However, after using AWS SAM, I realized that "infrastructure should also be managed as source code."
--- 
Throughout the workshop development, I frequently used four basic AWS SAM commands:
* sam init: creates the initial structure of a Serverless project.
* sam build: compiles and prepares the application for deployment.
* sam local: enables running Lambda functions locally using Docker. This is my favorite command because it allows me to test functionality without deploying to AWS after every code change.
* sam deploy: reads the "template.yaml" file, creates a CloudFormation Stack, and deploys all resources to AWS.
--- 
The Role of "template.yaml"
* Initially, I viewed "template.yaml" as just another configuration file. However, as the number of Lambda functions and resources grew, I realized that it serves as the most accurate documentation of the system's architecture. Just by reading "template.yaml", I can understand which services make up the system, how they connect, and how permissions are configured.
* It is safe to say that "template.yaml" is the true "blueprint" of the entire Serverless system.
--- 
Why Isn't AWS SAM Considered a Serverless Service?
* This was the question that puzzled me most when I started learning. After thoroughly reviewing AWS documentation, I realized the distinction lies in AWS SAM's role.
* Services like Lambda, DynamoDB, or API Gateway are directly involved in running the application—they are active, continuous services while the application is running.
* Conversely, AWS SAM does not participate in application execution. AWS SAM does not store data, process HTTP requests, or execute business logic. Once the "sam deploy" command finishes, AWS SAM essentially "steps aside," and the application is run entirely by AWS Serverless services.
* Therefore, AWS SAM is categorized as a "development framework" rather than a "Serverless service."
--- 
References:
1. AWS. "What is the AWS Serverless Application Model (AWS SAM)?". (https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/what-is-sam.html)
2. "Serverless on AWS". (https://aws.amazon.com/vi/serverless/)
3. "What is AWS Well-Architected Tool?". (https://docs.aws.amazon.com/wellarchitected/latest/userguide/intro.html)
---
Blog's link: https://web.facebook.com/groups/awsstudygroupfcj/permalink/2227753051322988/?rdid=4BxzLitflB0OFY8E#