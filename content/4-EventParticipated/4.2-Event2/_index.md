---
title: "FCAJ x Agentic AI Build Week"
date: 2026-07-25
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---

# Summary Report: “FCAJ x Agentic AI Build Week: Show Up. Build. Pitch. WIN!”

### Event Objectives

- Provide a practical Hackathon arena for builders to collaborate and turn AI ideas into fully functional products
- Inspire the next generation of young talent to shift their mental model and leverage Agentic AI for innovation
- Showcase winning products, key technical architectures on AWS infrastructure, and real-world applications
- Share actionable insights on project management, teamwork dynamics, and effective pitching strategies in Hackathons

### Speakers

- **Joseph Marazota** – Head of Technology, Asia
- **Nguyễn Gia Hưng** – Head of Solutions Architecture, Vietnam
- **One Team** – 1st Place Winner (AWS Track)
- **Signal Scout** – 2nd Place Winner (AWS Track)
- **Team Plan** – Participating Hackathon Team
- **Team 3K** – Participating Hackathon Team
- **Six Pillars** – Participating Hackathon Team

### Key Highlights

#### Opening & Inspirational Keynote
- **A New Development Mindset**: Transitioning from traditional release cycles (months per release) to the Agentic AI era featuring continuous automated deployment.
- **Roles of AI and Humans**: Smart AI Agents help orchestrate massive infrastructure (such as millions of fulfillment robots) while keeping humans in the loop for key decisions.

#### Team 1: One Team (1st Place Winner) – Conversational AI Ordering Agent
- **Problem**: Forcing customers to switch to a standalone app causes friction, loss of momentum, and abandoned orders.
- **Solution**: Built a multi-channel AI Agent on Zalo/WhatsApp allowing users to place food orders directly within the chat interface.
- **Architecture & Cost**: Powered by AWS Bedrock, Agent Core with long-term memory for user preferences, and TinyFish for web scraping, optimizing cost down to ~$0.006 per order.

#### Team 2: Signal Scout (2nd Place Winner) – Multi-Agent Market Intelligence System
- **Problem**: Competitor and strategic insights are scattered across multiple financial reports, press releases, and public sources.
- **Solution**: A Multi-Agent pipeline that automatically scrapes and aggregates market signals via TinyFish/Apify to deliver strategic insights and ROI forecasts.
- **Architecture**: Hosted on AWS Amplify with Cognito authentication, utilizing Bedrock Agents and integrated with Langfuse for agent observability.

#### Team 3: Team Plan – AI Assistant for Architecture Design & IaC
- **Problem**: Solutions Architects spend considerable time manually drawing architecture diagrams, estimating costs, and writing deployment scripts.
- **Solution**: An AI tool that converts natural language or documentation into structured diagrams (Draw.io), cost breakdown reports, and deployment-ready Terraform/CloudFormation code.

#### Team 4: Team 3K – Shepherd: Real-Time Crowd Management & Monitoring System
- **Problem**: Localized congestion at airports, supermarkets, and event venues disrupts operational flow.
- **Solution**: Real-time crowd monitoring using computer vision to track density, identify bottlenecks, and trigger automated dispatch alerts.
- **Architecture**: Built with Kinesis Video Streams, ECS Fargate running YOLOv26 & ByteTrack, DynamoDB/S3 storage, and an AI Copilot interface for venue operators.

#### Team 5: Six Pillars – Adaptive Workflow Engine for AML Investigation
- **Problem**: 90-95% of Anti-Money Laundering (AML) alerts in financial institutions are false positives, leading to costly manual reviews.
- **Solution**: Multi-Agent system automating KYC checks, transaction flow analysis, and sanction list screening to streamline investigations.
- **Architecture**: Combines Kinesis Data Streams, XGBoost for rapid alert scoring, Bedrock Sub-agents, and Bedrock Guardrails for safety and compliance.

### Key Takeaways

#### Design Mindset
- **Focus on Real Business Pain Points**: No matter how sophisticated the tech stack is, system design must start with solving a concrete business problem.
- **Human-in-the-Loop Control**: Essential for sensitive domains like finance, banking, and enterprise risk management.

#### Technical Architecture
- **Multi-Agent Pattern**: Modularizing tasks into specialized sub-agents orchestrated by a supervisor agent improves accuracy and system maintainability.
- **Cost Optimization & Security**: Balancing native AWS services with third-party tools to ensure enterprise compliance while optimizing operational costs.

#### Modernization Strategy
- **MVP Scope Control**: In rapid prototyping environments, focus strictly on core user workflows rather than expanding project scope unnecessarily.
- **Experiential Learning**: Hackathons offer the fastest route to validate ideas, refine technical skills, and build professional networks.

### Applying to Work

- **Adopt Agentic Workflows**: Implement multi-agent automation for multi-step enterprise workflows to reduce manual effort.
- **Leverage Serverless & Managed AI**: Use AWS Bedrock, Agent Core, and Kinesis to construct scalable, event-driven architectures.
- **Integrate Intuitive Interfaces**: Embed conversational AI experiences into ubiquitous messaging channels (e.g., Zalo, WhatsApp) or internal dashboards.

### Event Experience

Attending the **“FCAJ x Agentic AI Build Week”** provided comprehensive insights into end-to-end GenAI product development—from ideation and architectural design to pitching. Key takeaways include:

#### Learning from highly skilled speakers
- Gained strategic technological perspectives directly from AWS tech leaders.
- Learned practical implementation lessons through real-world team case studies across F&B, Finance/Banking, and Retail domains.

#### Hands-on technical exposure
- Observed live demonstrations of multi-agent orchestration, real-time video stream processing, and automated IaC generation.
- Deepened understanding of architectural trade-offs regarding cost, latency, and system safety on AWS.

#### Leveraging modern tools
- Explored advanced AWS services including **AWS Bedrock**, **Agent Core**, **Kinesis Video Streams**, **ECS Fargate**, and **Amplify**.

#### Networking and discussions
- Engaged in meaningful technical exchanges with mentors, judges, and fellow builders in the developer community.

#### Lessons learned
- Effective scope management and team synergy are critical factors for delivering high-quality MVPs under strict time constraints.
- AI Agents serve as powerful copilots to boost human productivity rather than completely replacing domain expert decision-making.

#### Some event photos

{{< report-image src="images/events/fcaj-agentic-ai-build-week.jpg" alt="Attending the FCAJ x Agentic AI Build Week hackathon with fellow builders" caption="On-site at FCAJ x Agentic AI Build Week, alongside other builders during the event." >}}

> Overall, the event provided not only deep technical knowledge but also reshaped perspectives on modern system architecture, practical GenAI applications, and community-driven innovation.