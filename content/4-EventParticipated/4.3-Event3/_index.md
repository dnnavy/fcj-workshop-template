---
title: "Event 3"
date: 2026-07-31
weight: 3
chapter: false
pre: " <b> 4.3. </b> "
---

# Report on "FCAJ x AABW - Sharing session after Agentic AI Build Week 2026"

### Event Information

&emsp;**Event name:** FCAJ x AABW - Sharing session after Agentic AI Build Week (AABW) 2026

&emsp;**Date:** July 25, 2026

&emsp;**Venue:** 26th Floor, Bitexco Tower, 02 Hai Trieu Street, Saigon Ward, Ho Chi Minh City

&emsp;**Organiser:** First Cloud AI Journey program together with the Agentic AI Build Week community

&emsp;**Role in the event:** Attendee

&emsp;**Format:** A two-part session, opening with a keynote from a guest speaker and followed by a sharing panel from the teams that competed in AABW 2026

### Background

**Agentic AI Build Week (AABW) 2026** was the largest AI agent hackathon in Southeast Asia, hosted by GenAI Fund in Ho Chi Minh City from July 8 to July 12, 2026, with more than two thousand participants and around five hundred projects. What made the competition distinctive was that the briefs came directly from enterprises and the judging leaned towards readiness for real deployment rather than the polish of the demo. The competition was divided into industry tracks, one of which was dedicated to solutions built on AWS.

The **FCAJ x AABW** session on July 25, 2026 was an opportunity for the teams that had competed in AABW to come back and share their experience with the interns of the First Cloud AI Journey program, most of whom had never taken part in a hackathon.

### Purpose Of The Event

- Inspire students and interns who are at the beginning of their path in information technology
- Create a forum where teams that had been through a hackathon could pass their practical experience on to those who had never attended one
- Help the attendees see the gap between learning a service and using that service to build something that works within a hard deadline
- Connect the community of cloud learners with people who already have a real product and real competition experience

### Programme Structure

| Part | Content | Format |
|---|---|---|
| **Part 1** | A guest speaker sharing their career journey in information technology | Keynote with a question and answer session |
| **Part 2** | Three teams that competed in AABW 2026 presenting their product, their technical work, their difficulties and their lessons | Team presentations with open discussion between the teams and the attendees |

## Part 1 - A Career Journey Shared By The Guest Speaker

The session opened with a talk by a foreign speaker working in the information technology industry. Instead of presenting a specific technology, the speaker walked through their own career path.

### Main points

- **A career path is not a straight line.** The speaker showed that their own path involved several changes of direction, including periods spent on work unrelated to the original plan, and that those very periods produced skills that became useful later.
- **The value of starting early even when you are not good enough yet.** Most opportunities come from having already started and having something to show, not from waiting until you feel confident enough.
- **Continuous learning is a requirement in this industry.** Technology moves fast, so the knowledge of any given moment becomes obsolete quickly. What holds its value is the ability to learn independently and the way you approach an unfamiliar problem.
- **Failing at a personal project costs very little.** This was the point the speaker stressed the most when addressing young people: a failed personal project only costs time, while what it returns is experience that cannot be learned from documentation.
- **The role of community.** Joining technical communities, asking questions and sharing back shortens the learning curve considerably compared with figuring everything out alone.

### The message that stayed with me

The message running through the whole talk was to dare to try and dare to do. The speaker did not present it as a slogan but backed it up with the times they had accepted work beyond their ability at that moment and learned while doing it. For an intern just entering the industry, that way of framing it is far more convincing than generic encouragement.

## Part 2 - Sharing Panel From The AABW 2026 Teams

Three teams took turns presenting their product and how they had built it:

| Team | Product | Problem addressed |
|---|---|---|
| **3KA** - The Journey Ahead | S.H.E.P.H.E.R.D. | Monitoring and forecasting crowd density from existing cameras |
| **Plan V** | Solution Architect Professional AI Native App | Automating solution architecture design and cost estimation work |
| **Signal Scout** | Strategic signal detection platform | Detecting early signals of corporate strategic change from scattered data sources |

### Team 1 - 3KA with S.H.E.P.H.E.R.D.

Team 3KA presented a product named **S.H.E.P.H.E.R.D.**, a system that analyses live camera footage to turn ordinary video data into operational information that can be acted on.

#### Main capabilities

- Detect and track people in the frame
- Measure crowd density
- Estimate queue conditions
- Identify early signs of congestion
- Predict overcrowding pressure before it happens
- Create proactive alerts rather than raising an alarm after the fact
- Recommend concrete actions for the staff on site

#### What stood out to me

What impressed me most about this product is that it does not require the business to buy any new equipment. The team works with the camera system already in place, and all of the value created sits in the analysis layer behind it. That is a very practical way to approach a business problem, because the barrier to deployment drops considerably.

The other notable point is the shift from reactive alerting to proactive forecasting. Instead of notifying once an area is already overcrowded, the system tries to detect the trend and warn beforehand, along with a recommended action. That is exactly what makes the product agentic rather than a pure computer vision system.

On the technical side, the team also discussed the constraints of processing a live video stream: the latency requirement, the volume of data to be transferred, and the trade-off between processing on site and sending everything to the cloud.

### Team 2 - Plan V with the Solution Architect Professional AI Native App

Team Plan V opened their presentation with an exchange familiar to anyone who has worked with a client:

> Customer: "Hey, could you design an AI system for SOP documents for me? Please have it ready by Thursday."
>
> Solution Architect: "Sure!"
>
> Customer: "Hey, I need it immediately."

From that situation the team pointed out that most of a solution architect's time goes into four repetitive tasks: extracting the requirements, drafting an initial architecture, creating the diagrams, and producing a high-level cost estimate. Their product targets exactly those four.

#### Main capabilities

- Analyses project requirements in both natural language and structured form
- Drafts high-level architecture options that are hybrid-cloud aware and aligned to the company's own standards once confirmed
- Generates editable Drawio diagrams and AWS diagrams using the official AWS Architecture Icons
- Produces directional AWS cost estimates for the ap-southeast-1 region
- Surfaces recommendations, the assumptions it used, and the gaps in the requirements
- Refines iteratively through a chat sidebar, with custom instructions per project

#### What stood out to me

This was the team whose work related most directly to what I am learning during the internship, because the four tasks the product automates are exactly the ones I have been doing by hand while writing the solution proposal: extracting requirements, drawing the architecture diagram and estimating the cost on the Pricing Calculator.

Two design details caught my attention:

- **The product generates editable diagrams, not images.** This is an important design decision, because an architecture diagram almost always has to be revised after a discussion with the client. Exporting only an image would sharply reduce how usable it is.
- **The product states the assumptions it used and where the requirements are still incomplete.** This is a mature way to handle the tendency of a language model to fabricate. Instead of hiding the uncertain parts, the system puts them in front of the user so they can decide.

Limiting the cost estimate to a directional figure for a single region is also a sensible scoping choice. The team acknowledged that a perfectly accurate estimate is impossible, so they deliberately bounded what the product promises.

### Team 3 - Signal Scout with a strategic signal detection platform

Team Signal Scout went beyond an ordinary chat bot and built a platform for detecting early signals of strategic change at a company. This was also the only team that presented a complete business model canvas alongside their work, meaning they covered the commercial side and not only the engineering.

#### The problem

The signs that a company is preparing a strategic shift, such as a restructuring or a move between business lines, are usually scattered across many public sources that appear unrelated on the surface. Strategy teams often only recognise them once the event has already happened. The product aims to collect and validate those scattered signals and assemble them into a story that can actually be read.

#### The value the product promises

- Detect corporate strategic changes early
- Connect scattered signals into a clear story
- Support every conclusion with evidence
- Support the three decision types: maintain, adapt or accelerate

#### The system's key activities

- Collect and validate evidence
- Detect restructuring signals
- Analyse metrics and build scenarios
- Present the results through a dashboard

#### Resources and technology partners

| Component | Role in the system |
|---|---|
| AWS | Infrastructure running the platform |
| Apify and TinyFish | Collecting data and evidence from public sources |
| LangFuse | Observing and evaluating the quality of the AI layer |
| Corporate data and the analysis rule set | The basis on which the system reaches a conclusion |

#### Target customers and channels

The team identified four customer groups: corporate strategy teams, enterprise risk management teams, competitive intelligence teams and B2B enterprise account management teams. The product reaches users through three channels: analysis reports, a website with an executive dashboard, and risk alerts along a timeline.

#### What stood out to me

- **The principle that every conclusion must carry evidence.** This addresses the fabrication tendency of a language model head on. What makes it different is that evidence is not treated as a side feature but placed directly in the core value of the product.
- **Positioning as decision support rather than decision making.** The team states explicitly that the human retains control of the final decision. For a sensitive problem such as assessing another company's moves, that is a sound position and also easier for an enterprise to accept.
- **Building an observability tool for the AI layer into the system from the start.** This was the detail I found most worth learning from across all three teams. Every other team said the hardest part was judging whether the product was good enough, while this team deliberately put a component dedicated to observation and evaluation into the architecture instead of relying on manual trials.
- **Covering the business model, not only the engineering.** The fact that the team spelled out who pays and what they pay for shows that the real deployment readiness criterion at AABW measures more than the technical work.

### Architectural Patterns Common To All Three Teams

Although the three problems are very different, the way the teams organised their systems had a lot in common:

- **An orchestration layer** that receives the request and decides which steps to take, rather than a fixed flow written into the source code
- **A large language model** handling the reasoning and the interpretation of the request
- **A set of tools** the system is allowed to call in order to actually act, for example querying data, generating a diagram or looking up a price
- **A context layer** so the system answers from company-specific data rather than from the model's prior knowledge
- **An observability layer over the AI**, although only team Signal Scout built this in as an explicit component, while the others still relied on manual testing
- **Serverless infrastructure**, because a hackathon is far too short to stand up and operate servers. The components mentioned most often were serverless functions for the processing, an API layer for communication, a NoSQL database for conversation state and object storage for static data. The teams in the AWS track described using AWS Lambda, Amazon API Gateway, Amazon DynamoDB, Amazon S3 and the AWS AI services for the model layer

All three teams were candid about the trade-offs they accepted: choosing the fast option over the optimal one, skipping part of the security or scalability requirements to hit the deadline, and recording those gaps as technical debt to be handled later.

### The Difficulties The Teams Faced

- **Time pressure.** All three teams raised this. Going from an idea to a working demo in a very short window forces constant cutting.
- **Too broad a scope at the start.** Many of the early hours went into narrowing the idea down. The lesson shared was to lock a minimum scope right at the beginning.
- **The system behaving inconsistently between runs.** This difficulty is specific to this kind of problem. Given the same input, the system may take a different path on two separate runs, which makes testing and demonstrating far less predictable than with an ordinary application.
- **The system looping endlessly or drifting off course.** There were situations where the system kept calling tools without converging on a result, which forced the teams to add a step limit and a stopping condition.
- **The model fabricating information.** When no suitable data is retrieved, the model may produce an answer that sounds plausible but is wrong. The teams had to add a verification layer, require citations, or state the assumptions explicitly the way team Plan V did.
- **The cost and latency of model calls.** Every reasoning step is a model call, so a multi-step system is both slow and expensive. Some teams had to shorten the number of steps or switch to a smaller model for the simpler ones. For team 3KA the latency requirement was even tighter because of the live video stream.
- **Difficulty in evaluating quality.** There is no clear pass or fail test as with ordinary software, so deciding whether the product is good enough came down largely to manual trials. Team Signal Scout was the only one to tackle this systematically, by building an observability and evaluation tool for the AI layer into the architecture from the start.
- **Quota limits and access configuration.** Some teams lost unplanned time to model request limits and to configuring permissions for the cloud services.
- **Last-minute integration and role assignment.** Working in parallel and merging at the end regularly produced unexpected errors. For teams whose members had never worked together, agreeing on an approach and a toolchain also consumed a fair share of the time.

### The Experience And Benefits The Teams Gained

- **A clearly higher learning rate.** Several participants said they had learned more in a few days of the hackathon than in weeks of reading documentation, because they had to make things work rather than stopping at understanding them.
- **A real product for a personal portfolio.** This was the benefit mentioned most often, along with having a concrete story to tell in an interview.
- **Direct feedback from mentors and from the enterprises that wrote the briefs.** That feedback pointed out things nobody would notice working alone, especially the real constraints of putting a system into operation.
- **Teamwork under pressure.** Including dividing the work, deciding quickly, and accepting the removal of a feature you had already invested effort in.
- **A wider network.** Several teams kept working together after the hackathon, and some projects continued to be developed once the competition ended.
- **Presentation skills.** Explaining a technical system in a few minutes to someone who knows nothing about it is a distinct skill, different from writing code.

### What I Learned

#### On the technical side

- I saw how cloud services are assembled into a complete system, instead of learning each service in isolation. That is the hardest part to picture when studying alone.
- I understood why serverless architecture is preferred in projects with little time and few people, since no effort goes into standing up and running the infrastructure.
- I got a first sense of how an AI agent system differs from an ordinary application: the flow is not fixed in advance, the result is not consistent between runs, and therefore testing and setting safety limits become part of the design itself.
- I learned an honest way of handling model uncertainty, through team Plan V's example of stating assumptions and requirement gaps instead of hiding them, and team Signal Scout's of requiring every conclusion to carry evidence.
- I learned that in a system built on a language model, observing and evaluating quality has to be designed in from the start as a component of the system, not added on at the end.
- I realised that most of the errors encountered in practice are not in the application logic but in permissions, configuration and the wiring between services.

#### On choosing a problem

- A product that requires no new equipment from the business, the way team 3KA worked with existing cameras, has a far lower barrier to deployment and is therefore more convincing to a decision maker.
- Deliberately bounding what a product promises, the way team Plan V limited its estimate to a directional figure for one region, is a sign of understanding the limits of your own solution.
- A good problem is usually one that automates a repetitive task a real person is currently doing by hand every day.

#### On career direction

- A career path does not have to be clear from the start. Starting and adjusting along the way is more realistic than waiting for a perfect plan.
- One product finished at a minimum level is worth more than several large ideas that were never started.
- Taking part in the community and in activities like a hackathon returns more than technical knowledge, in particular a network and opportunities.

#### On how to work

- Locking a minimum scope before starting is the most important step in a project with a short deadline.
- Components should be integrated as early as possible rather than left until the end.
- Recording clearly what has been traded away makes it possible to defend a design when it is questioned, instead of pretending everything is perfect.

### Applying It To The Internship

The event took place right after week 8 of the internship, exactly when I had finished the database topics and was starting to prepare the serverless material for week 9. The teams' sharing therefore had a direct effect on how I worked afterwards:

- The architecture combining serverless functions with an API layer and a NoSQL database, which all three teams used, became my reference model when I built a CRUD API in week 9
- The way team Plan V states its assumptions and requirement gaps was applied to my own solution proposal: writing down the assumptions behind a cost estimate instead of presenting a figure as if it were certain
- Team Plan V generating diagrams with the official AWS Architecture Icons reminded me to use the correct notation when drawing diagrams for the report
- The permission errors the teams described made me pay closer attention to the Lambda execution role from the very first lab, instead of attaching an overly broad policy for convenience
- The principle of locking a minimum scope before starting was applied to narrowing the proposal down to what fits the remaining time of the internship

### Photos From The Event

<!--
HOW TO INSERT IMAGES:
1. Put the image files in: static/images/4-EventParticipated/4.3-Event3/
2. Uncomment the lines below and correct the file names.
3. Use file names without accents or spaces. For example: keynote.png, team-3ka.png
-->

<!-- ![The keynote from the guest speaker](/images/4-EventParticipated/4.3-Event3/keynote.png) -->

<!-- ![Team 3KA presenting S.H.E.P.H.E.R.D.](/images/4-EventParticipated/4.3-Event3/doi-3ka.png) -->

<!-- ![Team Plan V presenting the Solution Architect Professional AI Native App](/images/4-EventParticipated/4.3-Event3/doi-plan-v.png) -->

<!-- ![Team Signal Scout presenting their business model canvas](/images/4-EventParticipated/4.3-Event3/doi-signal-scout.png) -->

![Photo taken at the event](/static/images/4.3-Event3/event.jpg)

> Compared with the two earlier events, which were weighted towards knowledge and technical depth, this one leaned towards experience and real stories. What I found most valuable was hearing the specific difficulties the teams had run into, including the parts they had not handled well. Technical documentation usually only presents the correct approach, whereas the reason an approach fails in a specific situation can only be heard from someone who went through it. Team Plan V's presentation in particular showed me that the very work I am learning can be looked at as a problem worth automating. The session also made me far less hesitant about signing up for a hackathon myself.
