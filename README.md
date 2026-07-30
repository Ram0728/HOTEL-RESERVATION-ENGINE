# 🏨 Hotel Reservation Engine

> An enterprise-grade Hotel Reservation System built with **Spring Boot**, **React**, **MySQL**, and **Redis (Redisson)** to handle high-concurrency booking scenarios while preventing overbooking through distributed locking.

![Java](https://img.shields.io/badge/Java-21-orange)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.x-brightgreen)
![React](https://img.shields.io/badge/React-Frontend-61DAFB)
![MySQL](https://img.shields.io/badge/MySQL-Database-blue)
![Redis](https://img.shields.io/badge/Redis-Distributed_Lock-red)
![License](https://img.shields.io/badge/License-MIT-green)

---

# 📖 Project Overview

Travel platforms process thousands of hotel reservations simultaneously. One of the biggest engineering challenges is ensuring that **multiple users cannot book the same room for overlapping dates**.

This project implements a **High-Concurrency Hotel Reservation Engine** that provides:

- Real-time room availability search
- Date-range overlap validation
- Secure reservation workflow
- Distributed locking using Redis (Redisson)
- Automatic lock expiration
- Inventory synchronization
- RESTful APIs
- Responsive React frontend

The system is designed using enterprise software architecture and modern backend technologies.

---

# 🚀 Key Features

✅ Hotel Management

✅ Room Type Management

✅ Room Inventory Management

✅ Real-Time Room Availability Search

✅ Date Range Overlap Detection

✅ Reservation Management

✅ Distributed Locking using Redis

✅ Automatic Lock Expiration

✅ Secure Booking Workflow

✅ REST APIs

✅ Swagger API Documentation

✅ Layered Architecture

✅ Global Exception Handling

---

# 📊 Key Performance Indicators (KPIs)

- No Overbooking
- Availability Search < 100 ms
- Accurate Date Overlap Validation
- Distributed Lock Success
- High Concurrent Booking Support
- Consistent Inventory Management

---

# 👥 User Personas

## Customer

### Responsibilities

- Search available rooms
- View room details
- Book rooms
- Complete payment

### Workflow

1. Select Check-in & Check-out Dates
2. Search Available Rooms
3. Select Room
4. Confirm Booking
5. Complete Payment

---

## Hotel Administrator

### Responsibilities

- Manage Hotels
- Manage Rooms
- Manage Room Types
- Monitor Reservations
- Update Room Pricing

### Workflow

- Add Hotels
- Add Rooms
- Update Availability
- View Reservations
- Block Rooms for Maintenance

---

# 🏗 System Architecture

```
                   React Frontend
                          │
                          │ REST API
                          ▼
                Spring Boot Backend
                          │
        ┌─────────────────────────────────┐
        │        Service Layer            │
        │ Availability Service            │
        │ Reservation Service             │
        │ Distributed Lock Service        │
        └─────────────────────────────────┘
                          │
                  Spring Data JPA
                          │
            ┌─────────────┴─────────────┐
            │                           │
         MySQL Database            Redis Server
                                   (Redisson Lock)
```

---

# ⚙ Technology Stack

| Component | Technology |
|------------|------------|
| Language | Java 21 |
| Backend | Spring Boot |
| Frontend | React.js |
| ORM | Spring Data JPA |
| Database | MySQL |
| Cache | Redis |
| Distributed Lock | Redisson |
| Build Tool | Maven |
| Documentation | Swagger/OpenAPI |
| Boilerplate Reduction | Lombok |

---

# 📂 Project Structure

```
hotel-reservation-engine

backend
│
├── config
├── controller
├── dto
├── entity
├── exception
├── repository
├── security
├── service
├── serviceimpl
├── util
├── resources
│     ├── application.properties
│     └── data.sql
└── pom.xml

frontend
│
├── src
├── public
├── package.json
└── vite.config.js
```

---

# 🔄 Booking Workflow

```
Customer

      │

Search Available Rooms

      │

Availability Check

      │

Date Overlap Validation

      │

Acquire Redis Lock

      │

Create Reservation

      │

Process Payment

      │

Payment Success

      │

Confirm Reservation

      │

Release Lock
```

---

# 🔐 Distributed Locking

To prevent overbooking, the booking workflow uses **Redis Distributed Locks (Redisson)**.

### Booking Flow

Customer clicks **Book Now**

↓

Redis Lock Created

↓

Room temporarily unavailable

↓

Payment Completed

↓

Reservation Saved

↓

Lock Released

If payment fails or times out, the lock expires automatically, making the room available again.

---

# 📅 Date Range Validation

The system checks for overlapping reservations before confirming a booking.

Example:

Existing Booking

```
Oct 5 -------------- Oct 10
```

Customer Request

```
        Oct 8 -------- Oct 12
```

Result:

❌ Booking Rejected (Date Overlap)

---

# 🛠 Installation

## Clone Repository

```bash
git clone https://github.com/yourusername/hotel-reservation-engine.git
```

---

## Navigate to Backend

```bash
cd backend
```

---

## Configure Database

Update:

```
src/main/resources/application.properties
```

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/hotel_db
spring.datasource.username=root
spring.datasource.password=your_password

spring.jpa.hibernate.ddl-auto=update
```

---

## Start Redis

Ensure Redis or Memurai is running.

Default Port

```
6379
```

---

## Build Project

```bash
mvn clean install
```

---

## Run Backend

```bash
mvn spring-boot:run
```

Runs on

```
http://localhost:8080
```

---

## Run Frontend

```bash
cd frontend

npm install

npm start
```

Runs on

```
http://localhost:3000
```

---

# 📚 API Documentation

Swagger UI

```
http://localhost:8080/swagger-ui/index.html
```

---

# 📌 Sample API Endpoints

### Hotel APIs

```
POST /api/hotels

GET /api/hotels

PUT /api/hotels/{id}

DELETE /api/hotels/{id}
```

---

### Room APIs

```
POST /api/rooms

GET /api/rooms

GET /api/rooms/available
```

---

### Reservation APIs

```
POST /api/reservations

GET /api/reservations

GET /api/reservations/{id}

DELETE /api/reservations/{id}
```

---

# 👨‍💻 Author

**Janakiram Thota**

B.Tech | Java Full Stack Developer

---
