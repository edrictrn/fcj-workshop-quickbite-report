---
title: "AWS Security Agent, SLA/Monitoring & Cloud Certification"
date: 2026-07-30
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---



# Summary Report: “AWS Security Agent, SLA/Monitoring & Cloud Certification Workshop”

### Event Objectives

- Introduce the new **AWS Security Agent** service to automate Pentesting, Code Reviews, and Design Reviews.
- Share system operations mindset centered on **Service Level Agreements (SLAs)** and **Effective Monitoring** from an enterprise perspective.
- Provide a clear roadmap, exam structure, and practical tips to pass the **AWS Certified Cloud Practitioner (CLF-C02)** exam.

### Speakers

- **Thinh** – DevSecOps Engineer @ 2Solutions & FirstFlow AI
- **Son** – Infrastructure Support Engineer @ Endava (Former Student Builder @ UIT)
- **Huy** – AWS Cloud Enthusiast & Speaker

### Key Highlights

#### 1. AWS Security Agent & Security Automation (Presenter: Thinh)
- **Solving Real-World Pain Points**: Traditional pentesting teams cost between $5,000 and $20,000 per project, take considerable time, and heavily depend on individual skill sets.
- **Core Features**:
  - **Design Security Review**: Analyzes Markdown, Doc, or Terraform files against standards like PCI-DSS and the AWS Well-Architected Framework (Free tier: 200 reviews/month).
  - **Code Review**: Integrates directly with GitHub/GitLab via Webhooks to scan code and suggest automated fixes on Pull Requests (Free tier: 1,000 PR reviews/month).
  - **Penetration Testing (Pentest)**: Simulates real attack vectors from Front-end to Back-end, generating detailed finding reports with step-by-step reproduction steps (Free trial: 2 months, 400 task-hours/month).
- **Technical Limitations**: Currently unable to bypass MFA (SMS/OTP prompts) and mutual TLS (mTLS) authentication.

#### 2. SLA & Enterprise Monitoring (Presenter: Son)
- **Importance of SLAs (Service Level Agreement)**: Formal commitments to customers regarding service quality. Failing SLAs (exceeding allowed downtime) leads to severe financial penalties.
- **Holistic Monitoring Mindset**:
  - **Healthy Infra ≠ Healthy User Experience**: A green infrastructure status (CPU/RAM) does not guarantee that users aren't experiencing application errors or broken workflows.
  - **Monitoring Pyramid**: Multi-layered observability covering Cloud Providers, Infrastructure (EC2/RDS), Applications (App/DB Connections), up to end-user Customer Journeys.
  - **Risk Response Process (SOP & SNS)**: Utilizing AWS CloudWatch Dashboards/Alarms paired with Amazon SNS for immediate alerting, alongside logging for continuous improvement.

#### 3. Path to AWS Cloud Practitioner Certification (Presenter: Huy)
- **CLF-C02 Exam Overview**:
  - Format: 65 questions (50 scored), 90 minutes (+30 minutes ESL accommodation = 120 minutes total), Passing Score: 700/1000, 3-year validity, Fee: $100.
  - 4 Domains: Cloud Concepts (24%), Security & Compliance (30%), Cloud Technology & Services (34%), Billing & Pricing (12%).
- **Core Knowledge Areas**:
  - **6 Pillars of the Well-Architected Framework** & **AWS Cloud Adoption Framework (CAF)**.
  - **Shared Responsibility Model**: Clear boundary between security "OF the Cloud" (AWS) vs. "IN the Cloud" (Customer).
  - **EC2 Pricing Models**: On-Demand, Reserved Instances (up to 72% savings), and Spot Instances (up to 90% savings but subject to 2-minute interruption notices).
- **Exam Tips & Tricks**:
  - **Keyword Mapping**: Spotting clues quickly (e.g., *Decouple/Microservices* → SQS; *List cost/Interruptible* → Spot Instance).
  - **Elimination Technique**: Instantly discard 2 irrelevant options to boost correct selection probability to 50/50.
  - **Utilize Flag for Review**: Tag difficult questions to review later without losing time momentum.

### Key Takeaways

#### Design Mindset
- **Security-First Approach**: Embed security early during the planning phase (Design Review) and integrate automated checking tools into CI/CD pipelines.
- **Customer-Oriented Monitoring**: Focus on user experience metrics rather than solely relying on raw server performance metrics.

#### Technical Architecture
- **Multi-Agent Automation**: Leverage AWS Bedrock & Multi-agent frameworks to automate vulnerability scanning and code auditing.
- **High Availability & Monitoring Architecture**: Build 3-tier best-practice architectures on AWS (ALB, EC2 in Multi-AZ, RDS) complemented by CloudWatch Alarms monitoring DB connections.

#### Modernization Strategy
- **Doc-First Approach**: Document every infrastructure change and architectural decision thoroughly prior to deployment.
- **Invest in Skill Standardization (Cloud Certification)**: Build structured foundations through AWS certifications to enhance enterprise-grade system design capabilities.

### Applying to Work

- **Integrate AWS Security Agent**: Test Code Review capabilities on personal or project GitHub/GitLab repositories.
- **Build Custom CloudWatch Alarms**: Configure alerts for critical indicators (Database Connections, HTTP Status 5xx) to deliver alerts via Email/SMS using SNS.
- **Practice & Register for CLF-C02**: Apply Keyword Mapping and Elimination techniques to successfully pass the foundational AWS certification exam.

### Event Experience

The workshop offered practical industry insights from speakers with rich experience working in enterprise and global tech environments:

#### Learning from highly skilled speakers
- Absorbed practical DevSecOps security mindsets and cutting-edge AI security tools from Thinh.
- Gained realistic operational perspectives on enterprise environments (NOC/SOC, SLA, Risk Management) from Son's engaging presentation.
- Acquired a complete roadmap and proven tips for AWS certification from Huy.

#### Hands-on technical exposure
- Watched live demonstrations of Domain Verification, GitHub Integration, Pentesting, and reading Security Findings reports.
- Participated in an incident response demo simulating database connection failures on AWS CloudWatch Dashboards & SNS.

#### Leveraging modern tools
- Explored modern AWS services including **AWS Security Agent**, **AWS Bedrock**, **Amazon CloudWatch**, **Amazon SNS**, and the **AWS Well-Architected Tool**.

#### Networking and discussions
- Exchanged real-world stories regarding IT careers, overcoming challenges in Layer-1 Support/Infra roles, and career progression in Cloud engineering.

#### Some event photos

{{< report-image src="images/events/aws-security-agent-sla-monitoring-cloud-cert.jpg" alt="Speaker presenting the SLA and enterprise monitoring session at the AWS Security Agent, SLA/Monitoring & Cloud Certification workshop" caption="Son presenting the “healthy infrastructure vs. happy user” monitoring gap during the SLA/Monitoring session." >}}

> Overall, the event delivered comprehensive knowledge spanning automated security, enterprise SLA-driven operations, and structured certification pathways for Cloud skills.