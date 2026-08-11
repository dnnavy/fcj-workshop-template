---
title: "Reflection"
date: 2024-01-01
weight: 7
chapter: false
pre : " <b> 5.7. </b> "
---

### 1. Difficulties encountered & Solutions

**Difficulty 1: Resource collisions due to Hard-coded Names**
- **Issue:** Encountered naming collision errors when trying to deploy multiple environments (e.g., `develop` and `local`) on the same AWS account (due to duplicate `TopicName` and Secrets Manager `Name`).
- **Solution:** Removed hard-coded name configurations, replacing them with interpolated variables `${AWS::StackName}` or allowing AWS to auto-generate random physical IDs, making the environments completely isolated and infinitely scalable.

**Difficulty 2: Silent AccessDenied from Policy Templates**
- **Issue:** AWS SAM provides a template named `AWSSecretsManagerGetSecretValuePolicy` to grant Lambda permissions to read the HMAC key. However, upon deployment, Lambda still threw 500 errors due to `AccessDeniedException` and `ResourceNotFoundException`.
- **Solution:** Through API log debugging, discovered that SAM's Template handles ARN strings imperfectly when a Secret is recreated. Decided to discard the Template and rewrite it using CloudFormation's native **Inline IAM Policy** (`Statement` block with `Resource: !Ref HmacSecretV2`). Changing the Logical ID to `HmacSecretV2` also forced CloudFormation to provision a new resource, perfectly syncing the correct ARN.

These debugging experiences provided invaluable lessons on the meticulousness required when operating Serverless infrastructure and enforcing the Principle of Least Privilege on AWS.

### 2. Personal Contributions

During the project, I actively contributed to both the early-stage research for Cloud and FinOps testing and the subsequent frontend implementation. This experience broadened my technical scope with completely new concepts in Cloud and FinOps. Additionally, balancing frontend development with application testing provided me with a comprehensive, dual-perspective view as both a developer and a tester, allowing me to align technical solutions closely with end-user needs.