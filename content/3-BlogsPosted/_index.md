---
title: "Blogs Posted"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3. </b> "
---


###  [Blog 1 - DSQL SQL Dialect: How Amazon Aurora DSQL Differs from Single-Instance PostgreSQL](3.1-Blog1/)
This blog post introduces an in-depth analysis of the Amazon Aurora DSQL SQL dialect and its core differences from single-instance PostgreSQL. While Aurora DSQL retains full, high compatibility with the PostgreSQL v16 standard, its shared-nothing distributed architecture and decoupled compute-storage model bring key changes regarding primary-key-based storage, Optimistic Concurrency Control (OCC), asynchronous DDL, and AWS IAM authentication. This is a valuable reference for architects and developers to optimize system design and minimize risks when working with a fully serverless distributed database.

###  [Blog 2 - What is AWS SAM? Why is AWS SAM Not Considered an AWS Serverless Service?](3.2-Blog2/)
This blog shares practical hands-on experience with getting started with AWS Serverless architecture and selecting the right service stack for workshop building. The article clarifies common misconceptions about the "serverless" concept, event-driven architecture mindsets, and the close integration of core services including AWS Lambda, API Gateway, DynamoDB (with lessons on Access Patterns & GSIs), and Amazon Cognito. It provides a practical, high-level overview to help you envision the full picture for designing a complete, cost-effective, and highly scalable serverless system.

###  [Blog 3 - What is AWS SAM? Why is AWS SAM Not Considered an AWS Serverless Service?](3.3-Blog3/)
This blog explains the nature of the AWS Serverless Application Model (AWS SAM) and why this popular tool is not categorized as an AWS "serverless service." Through this post, you will understand the Infrastructure as Code (IaC) mindset, the blueprint role of the template.yaml file, key CLI commands used during development (sam init, build, local, deploy), and the fundamental difference between a development framework and a runtime execution service.