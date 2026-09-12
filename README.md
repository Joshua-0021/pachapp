# PachaPP ♻️

### AI-Based Smart Waste Management and Reward System

PachaPP is an intelligent waste management platform designed to improve household waste collection, verification, monitoring, and participation through **Artificial Intelligence, Computer Vision, GPS-based Geotagging, and a digital reward system**.

The system connects **Household Owners, Green Army Workers (Haritha Karma Sena), Local Self-Government Bodies, Waste Management Authorities, Supplyco Stores, and System Administrators** through a centralized mobile and web-based platform.

---

## 📌 Problem Statement

Traditional household waste collection systems face several challenges, including:

* Improper waste segregation
* Low public participation
* Manual record keeping
* Limited transparency
* Inaccurate collection reporting
* Unnecessary trips by Green Army workers
* Difficulty verifying waste quantity and collection locations
* Duplicate or potentially fraudulent submissions

PachaPP addresses these challenges by digitizing the collection process and combining AI-based waste verification with GPS-based location validation.

---

## 💡 Proposed Solution

PachaPP provides a digital workflow where Green Army workers can:

1. Record household waste collections.
2. Capture images of collected waste.
3. Submit the collection along with GPS location information.
4. Use AI-based verification to identify waste categories and estimate quantities.
5. Validate the collection location using GPS.
6. Detect duplicate or suspicious submissions.
7. Update verified collection records.
8. Allocate reward points to eligible users.

Households can receive collection notifications, view their collection history, monitor plastic consumption, and access their reward information. Administrators and authorized authorities can monitor workers, collections, rewards, and waste-related analytics.

---

## ✨ Key Features

### 👤 User Management

* User registration and secure login
* Role-based access control
* Profile management

### 🏠 Household Management

* Household information management
* Collection history
* Collection status updates
* Vacant/no-waste reporting

### ♻️ Waste Collection

* Digital collection recording
* Waste image capture
* GPS location submission
* Collection history management

### 🤖 AI-Based Waste Verification

* Waste category identification
* Waste quantity estimation
* Computer Vision-based image analysis
* AI-assisted collection verification

### 📍 GPS-Based Verification

* Collection location verification
* Geotagging of collection records
* Duplicate submission detection
* Suspicious/fraudulent submission detection

### 🔔 Notifications

* Collection reminders
* Collection status notifications
* Plastic consumption alerts

### 🎁 Reward System

* Reward points for verified collections
* Household reward tracking
* Green Army worker reward tracking
* Support for eligible Supplyco reward redemption

### 📊 Monitoring & Analytics

* Worker performance monitoring
* Collection monitoring
* Waste statistics
* Waste analytics
* Household plastic consumption monitoring

These modules are defined in the project's functional requirements.

---

## 🏗️ System Architecture

```text
                    ┌──────────────────────┐
                    │   Household Owners   │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │   React Native App   │
                    └──────────┬───────────┘
                               │
              ┌────────────────┴────────────────┐
              │                                 │
              ▼                                 ▼
     ┌──────────────────┐             ┌──────────────────┐
     │  Spring Boot API │             │ FastAPI AI Service│
     └────────┬─────────┘             └─────────┬────────┘
              │                                 │
              │                         ┌───────┴────────┐
              │                         │ YOLOv8 / CV /  │
              │                         │ TensorFlow     │
              │                         └────────────────┘
              │
       ┌──────┴──────────┐
       │                 │
       ▼                 ▼
┌──────────────┐   ┌───────────────┐
│  PostgreSQL/ │   │ Firebase /    │
│  MongoDB     │   │ AWS S3        │
└──────────────┘   └───────────────┘
       │
       ▼
┌──────────────────────┐
│ React.js Admin       │
│ Dashboard            │
└──────────────────────┘
```

The SRS specifies a mobile application, web-based administrative dashboard, Spring Boot backend, FastAPI AI service, database, cloud storage, GPS/location services, and notification infrastructure.

---

## 🛠️ Technology Stack

| Layer              | Technology                     |
| ------------------ | ------------------------------ |
| Mobile Application | React Native                   |
| Admin Dashboard    | React.js                       |
| Backend            | Spring Boot                    |
| API                | RESTful APIs                   |
| Database           | PostgreSQL / MongoDB           |
| AI Service         | Python, FastAPI                |
| Machine Learning   | TensorFlow                     |
| Computer Vision    | OpenCV                         |
| Object Detection   | YOLOv8                         |
| Cloud Storage      | Firebase Storage / AWS S3      |
| Notifications      | Firebase Cloud Messaging (FCM) |
| Authentication     | JWT, Spring Security           |
| Deployment         | Docker                         |
| Hosting            | Railway / Render / AWS         |
| Version Control    | Git, GitHub                    |

The SRS currently lists PostgreSQL/MongoDB and Firebase Storage/AWS S3 as alternatives; one database and one storage solution should be selected before final implementation for technical consistency.

---

## 🔄 System Workflow

```text
User Registration
       ↓
Secure Login
       ↓
Role-Based Access
       ↓
Active Profile
       ↓
Waste Collection Recorded
       ↓
Waste Image + GPS Submitted
       ↓
AI Verification
       ↓
GPS Location Verification
       ↓
Collection Verified
       ↓
Collection History Updated
       ↓
Reward Points Updated
```

If verification cannot be completed, the system moves the collection to an issue/verification-failed state instead of automatically marking it as verified.

---

## 🤖 AI Components

### 1. Waste Identification & Quantity Estimation

Computer Vision and Machine Learning models analyze captured waste images to identify supported waste categories and estimate the quantity of collected waste.

### 2. Collection Verification

AI-based image verification is combined with GPS-based geotagging to validate collection records and help detect duplicate or potentially fraudulent submissions.

### 3. Plastic Consumption Monitoring

The system analyzes household plastic waste records over time. A continuous increase can trigger an appropriate alert for the household.

---

## 👥 User Roles

### Household Owner

* Manage household profile
* Receive collection notifications
* View collection history
* Monitor plastic consumption
* View rewards

### Green Army Worker

* Access assigned collection details
* Record waste collections
* Capture waste images
* Submit GPS location
* Track rewards

### Administrator / Authorized Authority

* Manage users
* Monitor collections
* Monitor worker performance
* View verified records
* Manage reward information
* Access waste statistics and analytics

### Supplyco

Participating Supplyco stores may support redemption of eligible household reward points for approved benefits, subject to the final reward implementation.

---

## 🔐 Security

PachaPP is designed with:

* Secure authentication
* JWT-based access
* Spring Security
* Role-based authorization
* Protected user and household information
* Secure handling of location and image data
* Protection against unauthorized requests

Security is also included as a non-functional requirement of the system.

---

## ⚠️ Constraints

The system may be affected by:

* Unstable internet connectivity
* Smartphone camera and image quality
* GPS accuracy
* AI model accuracy
* Environmental conditions affecting image recognition
* User digital literacy
* Third-party service availability
* Cloud storage and deployment resources
* Supplyco participation in reward redemption

AI and GPS validation are intended to reduce fraudulent submissions but may not eliminate every possible case.

---

## 🧪 Testing

The project includes several testing levels:

* **Unit Testing** — Individual modules such as authentication, waste collection, AI verification, and reward management.
* **Integration Testing** — Interaction between the mobile app, backend, AI service, database, GPS, and notification services.
* **System Testing** — Complete end-to-end workflows.
* **AI Model Testing** — Evaluation of waste identification and quantity estimation.
* **Security Testing** — Authentication and role-based access control.

---

## 📁 Project Structure

```text
PachaPP/
│
├── mobile-app/
│   └── React Native application
│
├── admin-dashboard/
│   └── React.js web application
│
├── backend/
│   └── Spring Boot REST API
│
├── ai-service/
│   └── FastAPI + Python AI service
│
├── database/
│   └── Database scripts and configuration
│
├── docs/
│   └── Project documentation and SRS
│
├── docker/
│   └── Docker configuration
│
└── README.md
```

---

## 🚀 Future Scope

The modular architecture allows future improvements to the mobile application, backend, AI services, and administrative dashboard.

Potential future development areas include:

* Improved AI waste classification
* More accurate quantity estimation
* Enhanced fraud detection
* Better handling of low-connectivity environments
* Expansion to additional platforms
* Improved waste analytics
* Integration with additional government services
* Expansion of reward and redemption mechanisms

---

## 🎯 Project Objective

The main objective of PachaPP is to create a more **efficient, transparent, data-driven, and participatory household waste management system** by combining digital collection records, AI-based verification, GPS validation, monitoring, and rewards.

---

## 👩‍💻 Project Team

**Group No.: 11**

* Athira M P
* Joshua George Abraham
* Raisha Hashly
* Suhana K

**Project:** PachaPP — AI-Based Smart Waste Management and Reward System

---

## 📄 Documentation

The Software Requirements Specification (SRS) follows an IEEE SRS format and documents the system background, functional requirements, non-functional requirements, behavioural description, validation criteria, AI components, and technology stack.

---

## 📜 License

This project is developed as an academic project. Licensing details can be added when the project is finalized.
