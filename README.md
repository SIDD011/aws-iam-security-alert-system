🚨 AWS IAM Security Alert System
------------------
The AWS IAM Security Alert System is a real-time security monitoring solution designed to detect IAM user creation events and notify administrators instantly via email.

This system leverages AWS native services to create an automated event-driven security workflow without using any custom servers or infrastructure.

It demonstrates practical implementation of:

- Event-driven architecture

- AWS security monitoring

- Cloud-native alerting mechanisms

- Real-time IAM activity detection


🏗 Architecture
---------

Event Flow

          IAM CreateUser API Call
                     ↓
      AWS CloudTrail logs the API activity
                     ↓
    Amazon EventBridge detects matching rule
                     ↓ 
      Amazon SNS publishes notification
                     ↓
        Email sent to Administrator
        
---------

🧩 Architecture Diagram
---------

  
     IAM   →  CloudTrail  →  EventBridge  →  SNS  →  Email Notification

---

🧠 How It Works
------

1. An IAM user is created in AWS.

2. AWS CloudTrail logs the CreateUser API call.

3. Amazon EventBridge continuously monitors CloudTrail events.

4. A rule filters events using:


       - source = aws.iam

       - detail-type = AWS API Call via CloudTrail

       - eventName = CreateUser

5. When the event matches, EventBridge triggers an SNS topic.

6. SNS sends an email notification to the subscribed administrator

--------

🔍 EventBridge Rule Configuration
---
        {
           "source": ["aws.iam"],
        "detail-type": ["AWS API Call via CloudTrail"],
        "detail": {
        "eventName": ["CreateUser"]
        }
       }

----------

🛠 AWS Services Used
------

Service	Purpose
- (IAM)	Identity management
- CloudTrail	Logs API activity
- EventBridge	Event filtering & routing
- SNS	Notification service
- Email Subscription	Alert delivery

 ---------

⚙️ Implementation Steps
--------

1. Enable AWS CloudTrail (Management Events).

2. Create an SNS topic (e.g., iam-security-alerts).

3. Subscribe an email endpoint and confirm subscription.

4. Create an EventBridge rule:

       - Event source: IAM via CloudTrail

       - Filter: CreateUser

5. Add SNS topic as the target.

6. Enable the rule.

7. Test by creating a new IAM user.
---------

📂 Project Structure
--------
        aws-iam-security-alert-system/
        │
        ├── architecture/
        │   └── architecture-diagram.png
        │
        ├── screenshots/
        │   ├── eventbridge-rule.png
        │   ├── sns-topic.png
        │   ├── email-confirmation.png
        │   └── monitoring-metrics.png
        │
        └── README.md
        
---------        

🔐 Security Use Case
------

This project helps organizations:

- Detect unauthorized IAM user creation

- Improve security visibility

- Implement real-time governance alerts

- Strengthen AWS account monitoring
-------- 

📊 Monitoring & Validation
--------

EventBridge monitoring metrics can be viewed in:

- Matched Events

- Invocations

- Failed Invocations

- End-to-End Latency

These metrics confirm that the alert pipeline is functioning correctly.

---------

🚀 Future Enhancements
-------

1. Monitor additional IAM activities:

       - DeleteUser

       - AttachRolePolicy

       - CreateAccessKey

2. Add AWS Lambda for enriched alert messages

3. Send notifications to Slack or Microsoft Teams

4. Store events in DynamoDB for audit history

5. Integrate with AWS Security Hub
   
6. Convert to Infrastructure-as-Code (Terraform/CloudFormation)
--------

📈 Skills Demonstrated
--------

- AWS IAM

- AWS CloudTrail

- Amazon EventBridge

- Amazon SNS

- Event-driven architecture

- Cloud security monitoring

- Real-time alerting systems

