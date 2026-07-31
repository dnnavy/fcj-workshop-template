---
title: "Event 1"
date: 2026-07-31
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# Report on "AWS Quiz Battle - First Cloud AI Journey Kick-off"

### Event Information

&emsp;**Event name:** AWS Quiz Battle - First Cloud AI Journey kick-off session

&emsp;**Date:** June 20, 2026

&emsp;**Venue:** 26th Floor, Bitexco Tower, 02 Hai Trieu Street, Saigon Ward, Ho Chi Minh City

&emsp;**Organiser:** Amazon Web Services Viet Nam Company Limited - First Cloud AI Journey program

&emsp;**Role in the event:** Attendee, following the competition as a member of the audience

&emsp;**Event format:** Team competition, four to five members per team

### Purpose Of The Event

- Create a sense of connection between the members at the first gathering of the program
- Let the attendees see the baseline AWS knowledge the program expects
- Introduce the kind of scenario questions a business actually faces, rather than stopping at pure theory
- Shape the self-study roadmap for the next phase based on the gaps that surfaced

### Format And Rules

The competing teams were formed randomly, with four to five people each. Because the split was random, most members of a team had never met before, which forced each team to assign roles in a very short time.

The competition ran over several rounds of increasing difficulty:

| Round | Content | Scoring |
|---|---|---|
| **Round 1 - Warm-up** | Rapid multiple-choice questions on cloud computing and AWS fundamentals | A correct and fast answer scores higher |
| **Round 2 - Service knowledge** | Questions on the characteristics, limits and pricing of the core services | Fixed points per correct answer |
| **Round 3 - Business scenarios** | Given a real business requirement, the team proposes a suitable AWS service and explains the reasoning | Scored on the soundness of the design and the argument |
| **Round 4 - Final stretch** | Open questions where the team picks the point value matching the difficulty | A wrong answer loses points |

After every question the judging panel, made up of AWS mentors and engineers, explained the answer and analysed why an option that looked correct did not fit the specific context. For someone attending as part of the audience, this was the most valuable part of the event, because I could follow the full line of reasoning without the time pressure the competing teams were under.

### Content Of The Question Set

#### Group 1 - Fundamentals

- Distinguishing the three service models IaaS, PaaS and SaaS
- Distinguishing Region, Availability Zone and Edge Location
- The Shared Responsibility Model between AWS and the customer
- The main service groups and the flagship service of each group

#### Group 2 - Core services

- Amazon EC2: the instance families, the four pricing models and the workload that fits each one
- Amazon S3: the storage classes, the durability guarantee and the lifecycle mechanism
- Amazon VPC: public and private subnets, the role of the Internet Gateway and the NAT Gateway
- AWS IAM: user, group, role and the policy evaluation order
- Amazon RDS: the difference between Multi-AZ and a read replica

#### Group 3 - Real business scenarios

This was the hardest group and the part that caused the most debate between the teams. Each question presented a business problem with a constraint on cost, time or security, and asked the team to propose a design on AWS.

Below are some of the scenarios I noted down while following the competition:

| Business requirement | What the teams proposed | The judging panel's explanation |
|---|---|---|
| An e-commerce platform sees a traffic spike during promotion hours and very low traffic the rest of the time. The cost of idle servers is too high | Use an Auto Scaling group with an Application Load Balancer and a scaling policy driven by CPU utilisation | A sound answer. The panel added that scheduled scaling would fit better because the promotion window is known in advance, so it reacts sooner than waiting for CPU to rise before scaling out |
| A company must keep accounting records for seven years by regulation, will almost never read them again, and wants the lowest possible cost | Store the data in Amazon S3 and use a lifecycle rule to move it to S3 Glacier Deep Archive | The right direction. The panel noted that the retrieval time of Deep Archive can be several hours, which has to be agreed with the business side beforehand |
| An internal application running inside a VPC needs to read and write on S3, but the security team does not allow the traffic to leave to the internet | One team proposed a NAT Gateway | Not accepted. The suitable answer is an S3 Gateway VPC Endpoint, which keeps the traffic off the internet and avoids the hourly charge of a NAT Gateway |
| The system must keep running when an entire Availability Zone is lost, with a very short tolerated downtime | Deploy the application tier across several Availability Zones with an Auto Scaling group and enable Multi-AZ on the database | A complete answer. The panel followed up on the difference between Multi-AZ and a read replica to clarify the purpose of each mechanism |
| An employee leaves the company, all access must be revoked immediately and the same risk must not happen again | Disable the IAM user and delete the access keys | Correct but incomplete. The panel steered the discussion towards IAM roles and centralised sign-in instead of long-lived access keys, so that revocation is immediate and auditable |

#### Group 4 - Cost and optimisation

- Estimating the cost of a simple architecture from the price list
- Spotting the components that are often forgotten but keep charging, such as a NAT Gateway, an unused Elastic IP or an orphaned EBS volume
- The role of cost allocation tags in attributing the cost to the right team

### Observations From The Audience

In the first two rounds most teams did fairly well, since those were concepts that can be memorised from the documentation.

The real separation only appeared in the business scenario round. Many questions had no single correct answer and depended on the specific constraints in the prompt. Some proposals worked perfectly well from a technical point of view yet still scored low because the cost was unreasonable or a security requirement stated in the prompt was violated. Watching from the audience, I noticed the teams' mistakes came mostly not from a lack of knowledge but from skimming over the constraints.

Another thing I observed was how the teams handled disagreement. The ones that settled on an answer quickly were usually the ones that went back to the requirement in the prompt, instead of arguing in general terms about which service is better.

Because I was not competing, I had the chance to write down both the questions and the panel's analysis in full. Those notes turned into a useful reference for the self-study phase that followed.

### What I Learned

#### On knowledge

- I got a clear picture of the baseline knowledge the program expects from an intern, and therefore of where I stood
- I realised the gap between knowing that a service exists and knowing when it should be used
- I understood that several AWS services look interchangeable but differ sharply in cost and security model, the clearest case being a NAT Gateway compared with a VPC Endpoint

#### On solving a business problem

- A technically correct design is not necessarily a good one. Cost, operational complexity and compliance requirements all have to be weighed at the same time
- The constraints in the prompt must be read carefully before thinking about a solution. Most of the low-scoring answers during the competition came from missing a condition that had been stated explicitly
- The reasoning behind a choice always has to be explainable, because in real work the argument matters as much as the result

#### On the value of observing

- Watching other people solve a problem under time pressure exposes the common reasoning mistakes clearly, the kind that are hard to notice when studying alone
- The panel's explanation after each question was worth more than the answer itself, because it showed how an experienced engineer analyses the constraints before picking a service

### Applying It To The Internship

The topics that came up most often during the competition became the study priorities for the following weeks:

- Permissions and the principle of least privilege were studied right in week 4 together with cost control
- The S3 storage classes and lifecycle rules were practised in depth in week 5
- Networking, and in particular the difference between a NAT Gateway and a VPC Endpoint, was clarified in week 6
- The habit of reading the constraints carefully and estimating the cost before deploying anything was kept for every later lab

### Photos From The Event

<!--
HOW TO INSERT IMAGES:
1. Put the image files in: static/images/4-EventParticipated/4.1-Event1/
2. Uncomment the lines below and correct the file names.
3. Use file names without accents or spaces. For example: overview.png, judges.png
-->

<!-- ![Overview of the competition on the 26th floor of Bitexco Tower](/images/4-EventParticipated/4.1-Event1/toan-canh.png) -->

<!-- ![The teams during the business scenario round](/images/4-EventParticipated/4.1-Event1/vong-tinh-huong.png) -->

<!-- ![The judging panel explaining the answer after each question](/images/4-EventParticipated/4.1-Event1/giai-thich-dap-an.png) -->

![Photo taken at the event](/fcj-workshop-template/static/images/4.1-Event1/event.jpg)

> Looking back, this was an effective way to open the program. Even though I only attended as a member of the audience, I took away more than I had expected. The greatest value was not learning a few more services, but the first exposure to AWS from the point of view of a real business problem with real constraints, rather than a list of services to memorise.
