# HireHive
Freelancing  Platforms

# 💼 Freelancing Service Platform – Backend (Spring Boot)

A powerful backend service for a freelancing platform where users can hire tech experts, manage wallets, and perform secure transactions. Built using **Spring Boot**, **JWT**, **MySQL**, and **Razorpay Integration**.

---

## 📌 Features

### ✅ User Roles
- **User** – Registers, logs in, adds wallet balance, hires experts.
- **Admin** – Approves/rejects tech experts, manages users.
- **Tech Expert** – Registers and waits for admin approval to provide services.

### 🔐 Authentication & Authorization
- **JWT Token-based Authentication**
- **Role-based Authorization** for secure access control
- Secure **password hashing** with BCrypt

### 💳 Wallet & Payments
- **Add Money to Wallet** (via Razorpay)
- **Deduct Money on Hiring**
- **Refunds to Wallet**
- Wallet balance is managed internally on successful payments.

### ⚙️ Admin Panel Functionalities
- Approve / Reject Tech Experts
- View all Users by Role
- Remove Users

---

## 🧱 Tech Stack

| Layer       | Tech                     |
|-------------|--------------------------|
| Backend     | Spring Boot (Java)       |
| Database    | MySQL                    |
| Auth        | JWT (JSON Web Tokens)    |
| Security    | Spring Security, BCrypt  |
| Payments    | Razorpay API Integration |
| Documentation | Swagger UI (optional) |

---

## 🗂️ Modules Overview

### 1. **User Management**
- Register / Login / Logout
- Update Profile (Name, Email, Password)
- Roles: `USER`, `ADMIN`, `TECH_EXPERT`
- Tech Expert status: `PENDING`, `APPROVED`, `REJECTED`

### 2. **Wallet Management**
- Razorpay integration for adding funds
- Deduct funds while hiring experts
- Refund functionality (e.g., service canceled)

### 3. **Admin Functionalities**
- View users by roles
- Approve / Reject tech experts
- Delete users

---

## 🔧 APIs Overview (Some key endpoints)

| Method | Endpoint                          | Description                         |
|--------|-----------------------------------|-------------------------------------|
| POST   | `/api/user/register`              | Register a new user                 |
| POST   | `/api/user/login`                 | Login and receive JWT token         |
| GET    | `/api/user/me`                    | Get current logged-in user details  |
| POST   | `/api/wallet/add`                 | Add money to wallet (post-payment)  |
| POST   | `/api/wallet/deduct`              | Deduct money when hiring            |
| GET    | `/api/admin/users/{role}`         | Get users by role                   |
| PUT    | `/api/admin/tech-expert/{id}`     | Change approval status              |

> 🔐 Most endpoints are secured using JWT and role-based access.

---

## 🔄 Flow Diagram

```text
User → Registers/Login → JWT Generated → Uses JWT to Access APIs  
↳ Adds Money (via Razorpay) → Balance Updated  
↳ Hires Tech Expert → Balance Deducted  

Admin → Approves Tech Experts → Manages Platform

Tech Expert → Registers → Waits for Approval → Gets Hired
git clone https://github.com/your-username/freelancing-platform-backend.git
cd freelancing-platform-backend




spring.datasource.url=jdbc:mysql://localhost:3306/your_db
spring.datasource.username=root
spring.datasource.password=your_password

jwt.secret=your_jwt_secret_key

razorpay.key_id=your_key_id
razorpay.key_secret=your_key_secret


com.yourapp
│
├── config/           → JWT, CORS, Security Config
├── controller/       → REST Controllers
├── dto/              → Data Transfer Objects
├── entity/           → User, Wallet Entities
├── exception/        → Custom Exception Handling
├── repository/       → JPA Repositories
├── service/          → Business Logic
└── util/             → JWT Utility Classes

