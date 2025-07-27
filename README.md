UNDER CONSTRUCTION #

✅ CloudSentry Project Flow (Step-by-Step Architecture)
👥 1. User Access & Authentication
Users (or Admins) open the React-based web app

They sign up or log in using AWS Cognito

Cognito assigns them a role: user or admin

📤 2. File Upload or Access
Users can upload/download confidential files

Files are stored in Amazon S3 (private bucket)

Every action (upload, download, delete) is passed through API Gateway

🧠 3. Lambda Handles Logic
API Gateway triggers AWS Lambda

Lambda logs:

User ID

Timestamp

Action type

File name

IP address

Geo-location (via IP lookup)

🗃️ 4. Activity Logging
This data is stored in DynamoDB

Each user has a list of their activities

Admins can query logs by time, IP, or file

🚨 5. Anomaly Detection
Lambda checks for patterns:

Too many downloads in a short time

Unusual access hours (e.g. 3am)

Multiple logins from different IPs

If triggered, Lambda sends alert via AWS SNS

📬 6. Admin Alerts
Admins receive alert via:

Email or SMS (SNS)

Real-time dashboard notifications

Admin can “disable” user or view logs

📊 7. Admin Dashboard (React)
Admin sees:

Activity Feed (audit logs from DynamoDB)

Flagged anomalies

User IP heatmaps (via GeoIP)

Downloadable CSV reports

Sentiment trends (if using Comprehend)

🧠 8. (Optional) Sentiment Analysis
User comments or messages analyzed via AWS Comprehend

Helps detect toxicity or suspicious communication

Results shown as part of admin analytics

🌐 9. Hosting & Access
Frontend hosted via AWS Amplify or S3 + CloudFront

Fully serverless, scalable, and secure
