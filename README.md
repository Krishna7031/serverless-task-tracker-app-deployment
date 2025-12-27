# Serverless Web Application – Fullstack AWS Implementation  

This repository contains a complete **serverless task tracking application** built using **Amazon Web Services (AWS)**.  
The project demonstrates how a modern cloud-native application can be designed, secured, and integrated using **fully managed AWS services**, without provisioning or managing any servers.

This project was developed as part of the **AWS Cloud Engineering Internship at HEProAI**, with a strong focus on **real-world architecture, security, and cloud integration challenges**.

---

## 📌 Project Objective

The primary objective of this project was to design and implement a **secure, scalable, and cost-effective serverless web application** that allows authenticated users to interact with backend APIs using **JWT-based authorization**.

The project emphasizes:
- Serverless architecture principles
- Secure authentication and authorization
- Frontend and backend integration
- Practical AWS service usage
- Real-world cloud debugging and troubleshooting

---

## 🧠 Problem Statement

Traditional web applications rely on always-on servers or virtual machines, which require manual scaling, monitoring, patching, and maintenance. This leads to:
- Higher operational costs
- Scalability challenges
- Increased infrastructure complexity

The problem addressed in this project was to build a **task tracking application** that:
- Automatically scales with demand
- Requires no server management
- Uses secure authentication
- Follows modern cloud best practices

---

## 🏗️ High-Level Architecture

The application follows a **decoupled serverless architecture**, where each layer is independently managed and integrated.

### Core Components:
- **Frontend:** Static web application
- **Authentication:** Managed identity service
- **Backend:** Serverless APIs
- **Database:** NoSQL storage
- **Security:** IAM + JWT-based authorization

---

## 🧱 AWS Services Used

### Frontend Layer
- **Amazon S3**
  - Hosts the static frontend files (HTML, CSS, JavaScript)
  - Configured for static website hosting

- **Amazon CloudFront**
  - Serves the frontend globally over HTTPS
  - Acts as a CDN for low latency and high availability

---

### Authentication Layer
- **Amazon Cognito User Pool**
  - Handles user sign-up, sign-in, and credential management
  - Provides a hosted login UI
  - Issues **JWT tokens** upon successful authentication

- **OAuth 2.0 Flow**
  - Used to authenticate users and obtain JWT tokens
  - Tokens are used to securely access backend APIs

---

### Backend Layer
- **AWS Lambda**
  - Implements serverless backend logic
  - Handles task creation and retrieval
  - Executes code only when invoked

- **Amazon API Gateway**
  - Exposes REST APIs
  - Acts as the entry point for backend services
  - Integrates with Lambda functions

- **Amazon DynamoDB**
  - Stores task data
  - Fully managed NoSQL database
  - Automatically scales with workload

---

### Security Layer
- **Amazon Cognito Authorizer**
  - Attached to API Gateway
  - Validates JWT tokens before allowing API access

- **AWS IAM**
  - Manages roles and permissions
  - Enforces least-privilege access between services

---

## 🔁 End-to-End Application Flow

1. User opens the frontend via CloudFront URL
2. User clicks **Login**
3. User is redirected to Cognito Hosted Login Page
4. User authenticates using email and password
5. Cognito issues a **JWT token**
6. Frontend extracts the token from the redirect response
7. Token is stored securely in browser storage
8. Frontend makes API calls using `fetch()`
9. JWT token is sent in the `Authorization` header
10. API Gateway validates the token using Cognito Authorizer
11. Lambda function is invoked
12. Lambda interacts with DynamoDB
13. Response is returned to the frontend

**Functional Flow:**  
`Login → Add Task → View Task List`

---

## 🧑‍💻 Frontend Implementation Details

- Written using **HTML, CSS, and JavaScript**
- No frontend frameworks used to keep the architecture simple
- Uses JavaScript `fetch()` API for backend communication
- Dynamically updates UI based on API responses
- JWT token is included in every protected request

Example API request:
```js
fetch("/tasks", {
  method: "POST",
  headers: {
    "Authorization": "<JWT_TOKEN>",
    "Content-Type": "application/json"
  },
  body: JSON.stringify({ task_name: "Sample Task" })
});
```

---

## ⚙️ Backend Implementation Details

### Lambda Functions
- Stateless serverless functions
- Written in Node.js
- Each function handles a single responsibility
  - Create Task
  - Get Tasks

### DynamoDB Table
- Table name: `Tasks`
- Primary key: `task_id`
- Stores task metadata
- Uses on-demand capacity mode

---

## 🔐 Security Implementation

- Authentication handled entirely by Amazon Cognito
- Authorization enforced at API Gateway using Cognito Authorizer
- Backend APIs are inaccessible without valid JWT tokens
- IAM roles restrict access between services
- No credentials or secrets are hardcoded

---

## 🧪 Testing & Validation

### API Testing
Tested using Postman

Verified behavior with:
- No token (401 Unauthorized)
- Valid token (200 OK)

### Frontend Testing
- Verified login redirect flow
- Verified task creation and retrieval
- Verified token storage and reuse

### Logging & Monitoring
- Amazon CloudWatch Logs
- Captures Lambda execution logs
- Used extensively for debugging

---

## ⚠️ Challenges Faced

This project involved several real-world challenges:

- OAuth redirect handling with CloudFront
- Cognito Hosted UI configuration
- JWT token flow alignment
- IAM permission debugging
- Distributed system troubleshooting

These challenges provided valuable production-level learning experience and improved understanding of cloud integration patterns.

---

## 📈 Results & Outcomes

- Successfully implemented serverless backend APIs
- Implemented secure JWT-based authentication
- Integrated frontend and backend securely
- Gained hands-on experience with AWS cloud services
- Built a scalable, cost-efficient architecture

---

## 🚀 Future Enhancements

- User-specific task isolation
- CI/CD pipeline using GitHub Actions
- Multi-region deployment
- Advanced monitoring with AWS X-Ray
- UI enhancements and validations

---

## 📂 Repository Structure

```
.
├── index.html              # Frontend UI
├── lambda/                 # Lambda function code
├── docs/                   # Architecture diagrams & screenshots
├── README.md
```

---

## 🙌 Acknowledgements

This project was developed as part of the AWS Cloud Engineering Internship at HEProAI, with guidance from mentors and coordinators who encouraged hands-on learning and real-world problem solving.

---

## 👤 Author

**Krishna**  
AWS Cloud Engineer | DevOps Enthusiast

- LinkedIn: [https://www.linkedin.com/in/your-profile](https://www.linkedin.com/in/your-profile)
- GitHub: [https://github.com/your-username](https://github.com/your-username)
- Newsletter: [DevOps Unplugged](https://devopsunplugged.substack.com)

---

## 📄 License

This project is licensed under the MIT License - see [LICENSE](LICENSE) file for details.

---

**Last Updated:** December 27, 2025
