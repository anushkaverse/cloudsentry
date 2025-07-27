UNDER CONSTRUCTION #

# 🔐 CloudSentry — Secure Cloud Activity Monitoring Platform

CloudSentry is a serverless, AWS-powered platform that monitors file access activity, detects suspicious behavior, and alerts admins in real-time. Built with modern cloud technologies, it offers intelligent anomaly detection, secure file handling, and visual dashboards — making it ideal for small teams, startups, or internal enterprise tools that prioritize security, auditability, and user accountability.

---

## ✅ CloudSentry Project Flow (Step-by-Step Architecture)

### 👥 1. User Access & Authentication
- Users (or Admins) open the **React-based web app**
- They **sign up or log in** using **AWS Cognito**
- Cognito assigns them a **role**: `user` or `admin`

### 📤 2. File Upload or Access
- Users can **upload/download confidential files**
- Files are stored in **Amazon S3 (private bucket)**
- Every action (upload, download, delete) is passed through **API Gateway**

### 🧠 3. Lambda Handles Logic
- **API Gateway** triggers **AWS Lambda**
- Lambda logs:
  - `User ID`
  - `Timestamp`
  - `Action type`
  - `File name`
  - `IP address`
  - `Geo-location` (via IP lookup)

### 🗃️ 4. Activity Logging
- Logs are stored in **DynamoDB**
- Each user has a list of their activity history
- Admins can query logs by **time**, **IP**, or **file**

### 🚨 5. Anomaly Detection
Lambda checks for:
- ✅ Too many downloads in a short time
- ✅ Unusual access hours (e.g., 3:00 AM)
- ✅ Multiple logins from different IPs

If triggered:
- Lambda sends an **alert via AWS SNS**

### 📬 6. Admin Alerts
- Admins receive alerts through:
  - Email or SMS (**SNS**)
  - Real-time dashboard notifications
- Admin can:
  - **View flagged users**
  - **Disable user**
  - **Review access history**

### 📊 7. Admin Dashboard (React)
Admins can:
- View full **Activity Feed** from DynamoDB
- Monitor **Flagged Anomalies**
- See **User IP Heatmaps** (via GeoIP)
- Export **CSV reports**
- *(Optional)* View **sentiment trends** from user messages

### 🧠 8. (Optional) Sentiment Analysis
- User comments/messages analyzed with **AWS Comprehend**
- Detects:
  - Toxic behavior
  - Suspicious communication patterns
- Displayed on the admin dashboard

### 🌐 9. Hosting & Access
- Hosted via **AWS Amplify** *(or S3 + CloudFront)*
- Fully **serverless**, **scalable**, and **secure**
