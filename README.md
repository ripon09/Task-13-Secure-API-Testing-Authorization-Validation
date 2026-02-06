# Task 13: Secure API Testing & Authorization Validation

## 🎯 Objective
The primary goal of this task is to evaluate the security posture of RESTful APIs. By simulating real-world attack vectors, this project focuses on identifying broken authorization, authentication bypasses, and improper input validation to ensure backend services are resilient against common exploits.

---

## 🛠️ Tooling
* **Primary Tool:** [Postman](https://www.postman.com/) (Collections, Environment Variables, and Test Scripts)
* **Alternative Tools:** `cURL` (CLI testing), [Insomnia](https://insomnia.rest/) (GUI alternative)

---

## 📖 Methodology & Mini-Guide

Testing is conducted through a systematic 8-step process to ensure full coverage of the API's attack surface:

### 1. Fundamentals & Reconnaissance
Understand the architecture of **REST APIs**. Analyze how the application utilizes HTTP methods:
* `GET`: Retrieve data.
* `POST`: Create new resources.
* `PUT/PATCH`: Update existing resources.
* `DELETE`: Remove resources.

### 2. Environment Configuration
Set up the testing environment in Postman by defining:
* **Base URL/Endpoints**
* **Headers** (e.g., `Content-Type: application/json`, `User-Agent`)
* **Request Bodies** based on provided API documentation (Swagger/OpenAPI).

### 3. Authentication Testing
Validate the "front door."
* Send requests with **valid** credentials (JWT, API Keys, Basic Auth).
* Send requests with **invalid/expired** credentials to ensure the 401 Unauthorized response is correctly triggered.

### 4. Broken Authentication Check
Test for "Fail Open" vulnerabilities by removing authentication headers entirely. 
> **Goal:** Ensure the API does not improperly allow unauthenticated access to sensitive data.

### 5. Authorization & IDOR Testing
Test for **Broken Object Level Authorization (BOLA/IDOR)**.
* Modify resource identifiers (e.g., changing `/api/v1/user/100` to `/api/v1/user/101`) to see if you can access data belonging to other users.

### 6. Fuzzing & Input Validation
Send malformed, unexpected, or "garbage" data (e.g., long strings, special characters, SQL injection payloads) to observe how the server handles unexpected input.

### 7. Rate Limiting & DoS
Perform multiple rapid-fire requests in a short duration.
* **Target:** Verify if the server implements `429 Too Many Requests` or if it is susceptible to resource exhaustion.

### 8. Response Analysis
Review HTTP response codes and error messages.
* Check for **Verbose Error Messages** that might leak backend stack traces, database versions, or internal logic.

---

## 📄 Deliverables
The following documents are produced upon completion:
1.  **API Security Testing Report:** A detailed log of all tests performed and results.
2.  **Vulnerability Mapping:** All discovered flaws mapped to the **OWASP API Security Top 10** (e.g., API1:2023 Broken Object Level Authorization).

---

## ✅ Final Outcome
Upon completion, I have demonstrated the ability to:
* Identify security misconfigurations in API environments.
* Detect and document authorization flaws.
* Recommend remediation strategies for securing backend communication.
