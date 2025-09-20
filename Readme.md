# 🚨 Serverless Alerting System on AWS

A lightweight, event-driven alerting pipeline built entirely with AWS serverless services. This solution delivers real-time notifications for high-priority CloudWatch alarms — without requiring storage, dashboards, or infrastructure management.

---

## 📦 Overview

This project provides a scalable alerting system using:

- **Amazon CloudWatch** – Monitors metrics and triggers alarms  
- **Amazon EventBridge** – Routes alarm events  
- **Amazon SQS** – Buffers events for reliable processing  
- **AWS Lambda** – Summarizes and formats alerts  
- **Amazon SNS** – Publishes notifications to subscribers

Ideal for developer teams who need fast feedback loops and operational visibility with minimal overhead.

---

## 🧱 Architecture

CloudWatch Alarm → EventBridge Rule → SQS Queue → Lambda → SNS Topic

| Layer         | Service Used         | Purpose |
|---------------|----------------------|---------|
| Monitoring    | CloudWatch           | Detects metric thresholds |
| Routing       | EventBridge          | Filters and forwards alarm events |
| Buffering     | SQS                  | Decouples event flow |
| Processing    | Lambda               | Summarizes alerts |
| Notification  | SNS                  | Publishes structured messages |

---

## 🚀 Deployment

### Prerequisites

- AWS account with CloudFormation permissions  
- Basic familiarity with AWS monitoring and serverless services

### Steps

1. Clone this repository  
2. Deploy the CloudFormation template in your preferred region  
3. Simulate alerts using `put-metric-data`  
4. Subscribe to the SNS topic for notifications (email, SMS, etc.)

---

## 💰 Cost Model

### Free Tier Coverage

This system runs entirely within the AWS Free Tier for small workloads:

| Service      | Free Tier Limit (Monthly) |
|--------------|---------------------------|
| Lambda       | 1M requests, 400K GB-sec   |
| SQS          | 1M requests                |
| SNS          | 1M publishes               |
| EventBridge  | 100K events                |
| CloudWatch   | 10 metrics + 10 alarms     |

### Paid Tier Example (2M alerts/month)

| Service      | Usage                     | Estimated Cost |
|--------------|---------------------------|----------------|
| Lambda       | 2M requests, 128MB, 1s     | ~$2.50         |
| SQS          | 2M messages                | ~$0.80         |
| SNS          | 2M publishes               | ~$0.50         |
| EventBridge  | 2M events                  | ~$4.00         |
| CloudWatch   | 30 metrics + 30 alarms     | ~$9.00         |

**Total Estimated Monthly Cost: ~$16.80 USD**

---

## 🔐 Security

- IAM roles scoped to least privilege  
- Lambda functions are stateless and isolated  
- SNS supports encrypted delivery and access control

---

## 🛠️ Customization

You can extend this system by:

- Adding Slack or MS Teams integration  
- Storing alert history in DynamoDB or S3  
- Filtering alerts by severity or service  
- Visualizing metrics with QuickSight or Grafana

---

## 🧭 Troubleshooting

| Issue                          | Resolution |
|--------------------------------|------------|
| No alerts received             | Check CloudWatch alarm threshold and EventBridge rule |
| Lambda not triggered           | Verify SQS permissions and event source mapping |
| SNS notifications not delivered| Confirm subscription and topic permissions |

---

## 📚 Resources

- [AWS CloudWatch Documentation](https://docs.aws.amazon.com/cloudwatch/)
- [AWS Lambda Best Practices](https://docs.aws.amazon.com/lambda/latest/dg/best-practices.html)
- [AWS Serverless Application Model](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/)

---

## 🙌 Author

**Abdul-Gafur**  
Cloud Automation & Infrastructure-as-Code Enthusiast  
Focused on developer experience, operational maturity, and scalable design

---

Feel free to fork, contribute, or reach out if you're building something similar!
