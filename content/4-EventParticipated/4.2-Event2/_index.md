---
title: "Event 2"
date: 2026-07-31
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---

# Report on "AWS Quiz Battle Grand Final"

### Event Information

&emsp;**Event name:** AWS Quiz Battle Grand Final

&emsp;**Date:** July 11, 2026

&emsp;**Venue:** 26th Floor, Bitexco Tower, 02 Hai Trieu Street, Saigon Ward, Ho Chi Minh City

&emsp;**Organiser:** Amazon Web Services Viet Nam Company Limited - First Cloud AI Journey program

&emsp;**Role in the event:** Attendee

&emsp;**Format:** A grand final built around three in-depth topics presented in turn

### Background

This was the final round of AWS Quiz Battle, the competition that started on June 20, 2026, which I followed as a member of the audience and wrote up in [Event 1](../4.1-event1/).

Unlike the opening round, which mainly tested fundamental knowledge through rapid questions, the grand final moved to in-depth topic presentations. The three topics chosen went into the areas that someone new to AWS usually skips: service level commitments and monitoring, securing web applications with an agent, and the actual structure of the foundational certification exam.

### Programme Structure

| Topic | Title | Focus |
|---|---|---|
| **Topic 1** | SLA and Monitoring - From SLA to Monitoring What Really Matters | Going from a service commitment to monitoring the things that actually matter |
| **Topic 2** | Securing Your Web Apps With AWS Security Agent | Automating security testing across the whole development lifecycle |
| **Topic 3** | Inside The Exam - AWS Cloud Practitioner | The structure and domain weighting of the exam |

## Topic 1 - SLA and Monitoring: From SLA to Monitoring What Really Matters

### What an SLA is and why it is needed

An **SLA (Service Level Agreement)** is a formal commitment on the expected level of service between a provider and a customer. It delivers four things:

- It sets clear expectations between the two parties
- It establishes accountability when an incident occurs
- It provides the basis for measuring performance
- It serves risk management

### Monitoring sits inside risk management

The point the speaker stressed is that monitoring is not a standalone activity but part of risk management. Its purpose is to detect a risk early, before it affects the SLA. The cycle has four steps:

| Step | Content |
|---|---|
| **Identify the risk** | Determine what could cause the system to breach the SLA |
| **Monitor the signals** | Collect metrics and logs, and set up alarms |
| **Respond** | Trigger notifications through Amazon SNS, run the predefined incident procedure, restore the system |
| **Improve** | Review the incident afterwards and tune things to prevent a recurrence |

### The Monitoring Pyramid

This was the most valuable part of the topic. The model stacks the layers to be monitored from the top down:

| Layer | What is monitored |
|---|---|
| **Customer Experience** (top) | The actual experience of the end user |
| **Business** | Successful login rate, number of orders, revenue |
| **Application** | Latency, error rate, request count |
| **Infrastructure** | CPU, memory, disk, network |
| **Cloud Provider** (bottom) | The status of the EC2, RDS, ALB and S3 services |

What is worth noticing is that this order runs opposite to how a beginner usually approaches it. Beginners tend to start at the bottom of the pyramid, watching CPU and memory, because those are the easiest metrics to obtain. Meanwhile the most important layer sits at the top and is the hardest to measure.

### Conclusions from the topic

- **Healthy infrastructure does not mean happy users.** A good infrastructure design does not guarantee a good user experience. A health check can still pass while the user experience is already broken. Infrastructure metrics alone cannot describe the true state of a system.
- **An SLA has to be understood in the context of shared responsibility.** AWS is responsible for the cloud infrastructure, while responsibility for the user experience belongs to whoever builds the system on top of it.
- **You have to understand what the user does and what the user needs**, not only know your own system.

## Topic 2 - Securing Your Web Apps With AWS Security Agent

### The bottleneck in traditional security testing

The speaker opened with three problems in the manual approach to penetration testing:

- A manual pentest engagement usually takes several weeks
- Hiring a third-party pentest specialist is expensive, in the range of five thousand to twenty thousand US dollars
- The result depends heavily on the individual skill of the pentester

These three problems push security testing to the end of the development cycle, or cause it to be skipped entirely on smaller projects.

### The Frontier Agent and how it differs from a chatbot

The product presented is a security agent powered by **Amazon Bedrock**, able to plan and execute complex security tasks on its own without a human stepping in at each stage.

The core difference from an ordinary chatbot built on a language model is that this agent **verifies a vulnerability by carrying out a real exploit**, instead of merely predicting which vulnerabilities might exist. It has three main capabilities:

| Capability | How it works |
|---|---|
| **Design review** | Analyses the architecture documents before any code is written, checking against PCI DSS, NIST CSF and AWS Well-Architected to make sure the design satisfies the security requirements |
| **Code review** | Automatically scans pull requests for security vulnerabilities and for private information leaked into the code, such as passwords or API keys |
| **Active penetration testing** | Attacks the application automatically, acting as a real user, performing multi-step attack chains and then producing an attack diagram together with detailed, verifiable evidence |

Together these three capabilities cover the full development lifecycle: design review, code security and active penetration testing.

### Integration into the workflow

The agent can be integrated directly into pull requests on GitHub or GitLab, leaving comments on individual lines of code and proposing valid source code patches as automatic pull requests.

This is what I found notable from a product design point of view: instead of producing a separate security report that a developer has to go and read, the findings are delivered straight into the place where the developer is already working.

### Limitations worth noting

I found this part no less valuable than the feature walkthrough, because the speaker was explicit that the agent is not a complete replacement:

- Authentication mechanisms such as MFA, biometrics or mTLS interrupt the agent's ability to operate automatically
- The agent struggles to detect fraud flaws that live in the business logic when it lacks deep enough business context
- The more complex the application, the more execution time it consumes, so tracking the agent's runtime is mandatory

## Topic 3 - Inside The Exam: AWS Cloud Practitioner

### Where the certification sits

**AWS Certified Cloud Practitioner** is a foundational certification focused on the way of thinking and on the overall picture of the AWS Cloud. The exam does not require programming skills or deep configuration ability, which makes it a suitable first step for someone new to the platform.

### The four knowledge domains

| Domain | Weighting |
|---|---|
| Domain 1 - Cloud Concepts | 24% |
| Domain 2 - Security and Compliance | 30% |
| Domain 3 - Cloud Technology and Services | 34% |
| Domain 4 - Billing, Pricing, and Support | 12% |

What stands out in this weighting is that **Security and Compliance accounts for 30%**, nearly as much as the domain on technology and services, even though this is only a foundational certification. That shows AWS treats security understanding as mandatory knowledge from the most basic level, not as material reserved for those going deeper.

Billing, Pricing and Support accounts for 12%, which is not a small share for content learners often skip on the assumption that it is not technical.

### What I Learned

#### On monitoring and operations

- Monitoring is not a matter of turning on a monitoring service and considering the job done. The pyramid model shows that infrastructure metrics sit near the bottom, while what really matters is the user experience at the top.
- I understood why a system with normal health checks can still be delivering a poor experience, and why metrics at the business layer such as the successful login rate need to be measured as well.
- I grasped the full cycle from identifying a risk through to improving after an incident, rather than stopping at setting up an alarm.

#### On security

- I saw the shift from security testing as a separate activity at the end of the cycle towards security being checked continuously from the design stage onwards.
- I understood the important difference between a system that predicts vulnerabilities and one that verifies them through a real exploit. The second produces verifiable evidence, so its results are far more trustworthy.
- I realised that leaking passwords and API keys into source code is a mistake common enough to require an automated scanner, rather than relying on each person's carefulness.
- I noted the limits of automation: anything requiring business context or requiring multi-factor authentication to be bypassed still needs a human.

#### On the certification path

- I now have a concrete picture of the Cloud Practitioner exam structure instead of just knowing the certification by name.
- The 30% weighting given to security and compliance is a signal to redistribute my revision time, rather than concentrating too heavily on the list of services.

### Applying It To The Internship

The event took place right after week 6 of the internship, when I had just finished the networking material and was starting to prepare the load balancing and high availability content for week 7. The three topics from the grand final affected my work afterwards as follows:

- **From Topic 1:** in week 6 I had enabled VPC Flow Logs and sent them to CloudWatch Logs, but only for the purpose of debugging connectivity. The monitoring pyramid showed me that this is only a near-bottom layer. When deploying the load balanced architecture in week 7, I paid additional attention to application layer metrics such as latency and error rate rather than looking only at CPU utilisation.
- **From Topic 1:** the shared responsibility aspect of an SLA connects directly to the Shared Responsibility Model I studied in week 2, but from a more concrete angle: AWS guarantees the infrastructure, while the user experience is the part I have to answer for myself.
- **From Topic 2:** the problem of API keys leaking into source code reinforced the reason I had already chosen IAM roles over long-lived access keys back in week 4, and prompted me to review the configuration files in the report repository.
- **From Topic 2:** the agent checking a design against the AWS Well-Architected standard reminded me to use those same pillars as a review checklist for the solution proposal, instead of drawing an architecture and leaving it at that.
- **From Topic 3:** I adjusted the certification plan I had set in week 1, choosing Cloud Practitioner as a stepping stone before Solutions Architect Associate, and allocating more time to security and compliance in line with the actual exam weighting.

### Photos From The Event

<!--
HOW TO INSERT IMAGES:
1. Put the image files in: static/images/4-EventParticipated/4.2-Event2/
2. Uncomment the lines below and correct the file names.
3. Use file names without accents or spaces. For example: overview.png, topic1-sla.png
-->

<!-- ![Overview of the grand final](/images/4-EventParticipated/4.2-Event2/toan-canh.png) -->

<!-- ![Topic 1 - SLA and the monitoring pyramid](/images/4-EventParticipated/4.2-Event2/topic1-sla.png) -->

<!-- ![Topic 2 - AWS Security Agent](/images/4-EventParticipated/4.2-Event2/topic2-security-agent.png) -->

<!-- ![Topic 3 - The structure of the AWS Cloud Practitioner exam](/images/4-EventParticipated/4.2-Event2/topic3-exam.png) -->

![Photo taken at the event](/images/4.2-Event2/event.jpg)

> The grand final had a completely different character from the opening round. Where the June 20 session tested what the attendees knew, this one revealed the areas someone new to AWS most easily overlooks. For me the topic on SLA and monitoring changed my thinking the most: until then I had implicitly assumed that if the system was running and the infrastructure metrics looked normal, everything was fine. The monitoring pyramid showed that this is only the lowest layer, and that the hardest part of operations lies in measuring what the user actually feels.
