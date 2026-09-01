<div align="center">


Smart Doctor Appointment & Healthcare Management Platform

A secure, scalable, full-stack healthcare application that connects patients, doctors, and administrators through one unified digital platform.

✨ Features • 🛠 Tech Stack • 🏗 Architecture • 🚀 Setup • 🔌 APIs • 🔮 Roadmap

</div>

🌟 Project Overview

Management is a real-world doctor appointment and clinic management application developed using Java Full Stack technologies. It replaces manual appointment booking and fragmented patient records with a secure digital workflow.

Patients can discover doctors and book appointments, doctors can manage consultations, and administrators can monitor users and platform activity. The project demonstrates practical experience in responsive UI development, REST API design, authentication, database modelling, validation, testing, containerization, and deployment-ready configuration.

🎯 Problem: Long waiting times, appointment conflicts, and disconnected medical records.
💡 Solution: A role-based platform that manages the complete appointment lifecycle—from doctor discovery to consultation completion.

👥 User Roles

Role

Access

👤 Patient

Register/login, search doctors, view profiles, book or cancel appointments, track appointment history

👨‍⚕️ Doctor

Manage availability, view appointments, confirm/reject requests, update consultation status and notes

🛡️ Administrator

Manage users and doctors, monitor appointments, view platform statistics and maintain system control

✨ Key Features

🔐 Authentication & Security

Secure registration and login using Spring Security + JWT

Password encryption with BCrypt

Role-Based Access Control for Patient, Doctor, and Admin

Stateless authentication and protected REST endpoints

Request validation, centralized error handling, and CORS configuration

🩺 Doctor Management

Doctor profiles with specialization, qualification, experience, fee, and availability

Search and filter doctors by specialization

Availability and appointment-slot management

Doctor dashboard for consultation workflow

📅 Appointment Management

Book appointments using available date and time slots

Prevent duplicate bookings for the same doctor and time

Appointment lifecycle: REQUESTED → CONFIRMED → COMPLETED / CANCELLED

Patient and doctor appointment history

Consultation notes and status updates

📊 User Experience

Responsive, mobile-first interface using React.js

Reusable components and protected routes

Form validation, loading states, alerts, and meaningful error messages

REST API integration using Axios

Role-specific dashboards and navigation

🛠 Technology Stack

Layer

Technologies

🎨 Frontend

React.js 18, JavaScript ES6+, React Router, Axios, Context API, HTML5, CSS3, Bootstrap/Tailwind CSS, Angular.js

⚙️ Backend

Java 17, Spring Boot 3, Spring MVC, Spring Data JPA, Hibernate, Maven, Node.js, Express.js

🔐 Security

Spring Security, JWT, BCrypt, Role-Based Authorization

🗄️ Database

MySQL 8, H2 for local development/testing

🧪 Testing

JUnit 5, Mockito, Spring Boot Test, Postman

📚 API Docs

OpenAPI 3, Swagger UI

🧰 Tools

Git, GitHub, IntelliJ/Eclipse, VS Code, MySQL Workbench

☁️ DevOps

Docker, Docker Compose, GitHub Actions, AWS EC2/RDS deployment-ready

🏗 System Architecture

flowchart LR
    U["Patient / Doctor / Admin"] --> UI["React Web Application"]
    UI -->|"HTTPS + JWT"| API["Spring Boot REST API"]
    API --> SEC["Spring Security"]
    API --> SRV["Service Layer"]
    SRV --> JPA["JPA / Hibernate"]
    JPA --> DB[("MySQL Database")]

Backend Request Flow

Controller → DTO Validation → Service → Repository → MySQL
                     ↓
          Global Exception Handler

The backend follows a clean layered architecture to separate HTTP handling, business rules, persistence, and security concerns.

📁 Project Structure

medinexus/
├── frontend/
│   ├── src/
│   │   ├── api/             # Axios client and API services
│   │   ├── components/      # Shared UI components
│   │   ├── context/         # Authentication state
│   │   ├── pages/           # Login, doctors, booking, dashboards
│   │   └── App.jsx          # Routes and application shell
│   └── package.json
├── backend/
│   ├── src/main/java/com/medinexus/
│   │   ├── config/          # Security and application config
│   │   ├── controller/      # REST controllers
│   │   ├── dto/             # Validated request/response models
│   │   ├── exception/       # Global API error handling
│   │   ├── model/           # JPA entities and enums
│   │   ├── repository/      # Spring Data repositories
│   │   ├── security/        # JWT authentication
│   │   └── service/         # Business logic
│   └── pom.xml
├── docker-compose.yml
└── README.md

🗃 Core Data Model

Entity

Important Fields

User

id, name, email, encryptedPassword, role

Doctor

id, userId, specialization, qualification, experience, fee, availability

Appointment

id, patientId, doctorId, scheduledAt, reason, status, notes, createdAt

Relationships

One User account can own one Doctor profile.

One Patient can book many Appointments.

One Doctor can receive many Appointments.

A database constraint protects each doctor’s date-time slot from duplicate booking.

🔌 API Endpoints

Authentication

Method

Endpoint

Access

Purpose

POST

/api/auth/register

Public

Create a patient or doctor account

POST

/api/auth/login

Public

Authenticate and receive JWT

Doctors

Method

Endpoint

Access

Purpose

GET

/api/doctors

Public

List/search doctors

GET

/api/doctors/{id}

Public

View doctor profile

PUT

/api/doctors/{id}

Doctor/Admin

Update doctor profile

Appointments

Method

Endpoint

Access

Purpose

POST

/api/appointments

Patient

Book an appointment

GET

/api/appointments/mine

Authenticated

View personal appointments

PATCH

/api/appointments/{id}/status

Doctor/Admin

Update appointment status

DELETE

/api/appointments/{id}

Patient/Admin

Cancel an appointment

📖 Interactive API documentation: http://localhost:8080/swagger-ui.html

🚀 Run Locally

Prerequisites

Java 17+

Maven 3.9+

Node.js 20+

MySQL 8+

Git

1️⃣ Clone the Repository

git clone https://github.com/ShanmukhaPonnada/medinexus.git
cd medinexus

2️⃣ Configure Environment Variables

DB_URL=jdbc:mysql://localhost:3306/medinexus
DB_USERNAME=root
DB_PASSWORD=your_password
JWT_SECRET=replace_with_a_secure_secret_of_at_least_32_characters

Create the database:

CREATE DATABASE medinexus;

3️⃣ Start the Backend

cd backend
mvn spring-boot:run

Backend URL: http://localhost:8080

4️⃣ Start the Frontend

cd frontend
npm install
npm run dev

Frontend URL: http://localhost:5173

🐳 Run with Docker

docker compose up --build

🧪 Testing

# Backend unit and integration tests
cd backend
mvn test

# Frontend quality checks
cd frontend
npm run lint
npm run test

API workflows can also be verified through the included Postman collection and Swagger UI.

⚡ Engineering Highlights

✅ Layered backend design with reusable and maintainable code

✅ DTO-based validation instead of exposing database entities directly

✅ Transactional service methods for reliable appointment updates

✅ Database-level and application-level duplicate-slot protection

✅ Stateless JWT authentication and least-privilege role access

✅ Environment-based configuration with no secrets committed to Git

✅ Consistent HTTP status codes and centralized error responses

✅ Development database support through H2 and production support through MySQL

🔮 Future Roadmap

💳 Razorpay/Stripe payment integration

🎥 Secure video consultations

📄 Digital prescriptions and downloadable reports

🔔 Email, SMS, and WhatsApp appointment reminders

🧠 AI-assisted symptom triage with explicit medical-safety controls

📈 Analytics dashboard for clinic performance

🌐 Multi-clinic and multilingual support

☁️ Production deployment using AWS EC2, RDS, S3, and CI/CD

Note: Roadmap features are planned enhancements and are not claimed as implemented.

🔒 Privacy & Disclaimer

This is a portfolio and learning project. Use only fictional test data. It is not a certified medical system and must undergo privacy, security, regulatory, and clinical review before handling real patient information.

👨‍💻 Developer

Ponnada V V Naga Shanmukha
Java Full Stack Developer | Spring Boot | React.js | REST APIs | MySQL





<div align="center">

⭐ If this project helped or inspired you, consider starring the repository!

Built with ☕ Java, ⚛️ React, and a goal to simplify healthcare access.

</div>
