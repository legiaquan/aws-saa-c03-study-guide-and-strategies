# AWS Certified Solutions Architect – Associate (SAA-C03) Exam: Study Guide & Strategies

👉 [Xem bản Tiếng Việt tại đây](./README.vi.md)

## Introduction

This document summarizes effective strategies, common question patterns, and guidance on choosing the right AWS solutions for the AWS Certified Solutions Architect – Associate (SAA-C03) exam. The goal is to help you understand the underlying logic of exam questions and apply AWS knowledge efficiently, rather than memorizing answers.

---

## 1. How to Approach Exam Questions

- **Analyze the Scenario:** Identify the core problem, current architecture (if any), and key requirements.
- **Spot Keywords:** Specific keywords often point to the type of solution needed.
- **Apply Well-Architected Principles:** Correct answers usually align with these principles: Operational Excellence, Security, Reliability, Performance Efficiency, and Cost Optimization.
- **Prefer Managed Services:** AWS typically favors managed services to reduce operational overhead.
- **Understand Trade-offs:** Optimal solutions may involve trade-offs (e.g., lower cost but higher latency).

---

## 2. Common Question Types & Service Selection

### 2.1. Minimizing Operational Overhead / Choosing Managed Services

**Keywords:** “least operational overhead”, “fully managed”, “serverless”, “no code changes”

**Typical solutions:**
- **Amazon Athena:** Analyze logs in S3 with on-demand SQL queries.
- **AWS Lambda + EventBridge:** Automate starting/stopping EC2 or RDS outside business hours.
- **CloudWatch Container Insights:** Collect logs and metrics for EKS.
- **AWS Secrets Manager / Parameter Store:** Manage secrets and credentials.
- **Session Manager:** Secure EC2 access without SSH keys.
- **AWS DataSync:** Transfer data from on-premises SFTP to AWS.
- **AWS Glue:** Convert CSV files to Parquet.
- **Amazon Macie + SNS:** Detect PII in S3 and send notifications.

### 2.2. Cost Optimization

**Keywords:** “most cost-effective”, “minimize costs”, “reduce cost”

**Typical solutions:**
- **S3 + CloudFront:** Host and deliver static websites.
- **S3 Lifecycle + Glacier Deep Archive:** Archive infrequently accessed data long-term.
- **EC2 Reserved/Spot Instances, Compute Savings Plans:** Optimize compute costs.
- **VPC Gateway Endpoint:** Reduce data transfer costs between EC2 and S3 in the same region.
- **DynamoDB On-demand, Aurora Serverless:** Cost-effective databases for unpredictable workloads.
- **Spot Instances:** For batch or short-lived workloads.

### 2.3. High Availability & Disaster Recovery

**Keywords:** “highly available”, “fault tolerant”, “automatic failover”, “RPO”, “RTO”

**Typical solutions:**
- **RDS/Aurora Multi-AZ, Aurora Global Database:** Ensure high availability and disaster recovery.
- **EFS:** Shared file system with auto scaling.
- **ALB + Auto Scaling Group (multi-AZ):** High availability for web apps.
- **Amazon MQ (active/standby) + Auto Scaling:** HA for message brokers.
- **S3 Versioning + MFA Delete:** Protect data from accidental deletion.
- **SNS + SQS + Lambda:** Ensure event delivery and processing, even with network issues.
- **Global Accelerator + NLB:** High availability and low latency for UDP services.

### 2.4. Performance & Low Latency

**Keywords:** “lowest latency”, “high I/O”, “real-time”, “faster response time”

**Typical solutions:**
- **CloudFront:** CDN to reduce latency.
- **RDS Read Replica, ElastiCache:** Reduce database load, accelerate data retrieval.
- **DynamoDB DAX:** Accelerate DynamoDB performance.
- **FSx for Lustre:** HPC workloads, S3 integration, high throughput.
- **Kinesis Data Streams/Firehose:** Real-time data processing.

### 2.5. Security & Compliance

**Keywords:** “secure”, “encrypt”, “audit”, “compliance”, “DDoS attacks”

**Typical solutions:**
- **VPC Endpoint:** Private connectivity to S3/DynamoDB.
- **IAM Role:** Grant S3 access to EC2 securely.
- **AWS Config, CloudTrail:** Audit and monitor configuration/API changes.
- **WAF, Shield Advanced:** Protect against web/DDoS attacks.
- **SSE-KMS, EBS encryption default:** Automated data encryption and auditability.
- **IAM Role Cross-account, SCP:** Access management across multiple AWS accounts.

### 2.6. Data Storage & Management

**Keywords:** “archive”, “long-term retention”, “file system”, “object storage”, “database”

**Typical solutions:**
- **S3:** Object storage for data lakes, static websites, media.
- **EFS:** NFS file system for Linux EC2.
- **FSx for Windows:** SMB file shares for Windows workloads.
- **RDS:** Relational databases.
- **DynamoDB:** NoSQL, high performance.
- **Storage Gateway:** Hybrid storage solutions.
- **S3 Object Lock:** Data immutability and compliance.

### 2.7. Event-Driven Architectures & Messaging

**Keywords:** “decouple”, “asynchronous”, “queues”, “topics”

**Typical solutions:**
- **SQS (FIFO/Standard):** Decouple, buffer, ensure message order.
- **SNS:** Fan-out messaging.
- **S3 Event + SQS + Lambda:** Automate processing of uploaded files.
- **Kinesis Data Streams:** Real-time, ordered event processing.

---

## 3. Key Concepts to Remember

- **Shared Responsibility Model:** AWS is responsible “of the cloud”; you are responsible “in the cloud.”
- **Principle of Least Privilege:** Grant only the permissions necessary.
- **Separation of Concerns:** Decouple components for higher availability and scalability.
- **Infrastructure as Code (IaC):** Use CloudFormation for automated, repeatable deployments.
- **Global vs Regional:** Know which services are global (IAM, Route 53, CloudFront, WAF, Global Accelerator) and which are regional (EC2, RDS, S3).

---

## 4. Effective Study Techniques

- Read questions carefully, highlight keywords.
- Use elimination: discard options that don’t fit the requirements.
- Prefer managed, serverless services unless custom solutions are specified.
- Be aware of trade-offs: cost, performance, security, availability.
- Practice with labs and sample questions regularly.

---

## 5. References

- AWS Official Documentation
- AWS Well-Architected Framework
- AWS Exam Readiness: Solutions Architect – Associate

---

**Good luck with your studies and the exam!**
