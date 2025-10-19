# 🏪 Bookstore API

[![Java](https://img.shields.io/badge/Java-17-blue)](https://www.oracle.com/java/)  
[![Spring Boot](https://img.shields.io/badge/SpringBoot-3.x-green)](https://spring.io/projects/spring-boot)  
[![License](https://img.shields.io/badge/License-MIT-yellow)](LICENSE)

A RESTful backend application built with **Spring Boot** for managing users in a Bookstore application.  
This project demonstrates user registration, login, and retrieval of users using **Spring Boot**, **Spring Data JPA**, and **H2 in-memory database**.

---

## Overview

The **Bookstore API** exposes endpoints for:

- **User Registration** (`POST /api/register`)  
- **User Login** (`POST /api/login`)  
- **View All Users** (`GET /api/users`)  

It follows a layered architecture:

1. **Controller Layer** – Handles HTTP requests (`UserController`).  
2. **Repository Layer** – Performs database operations (`UserRepository`).  
3. **Model Layer** – Defines database entities (`User`).  

H2 database is used for quick testing, and all endpoints return JSON responses.

---

## Project Structure

```
bookstore-api/
├── src/main/java/com/example/demo/
│   ├── controller/UserController.java
│   ├── model/User.java
│   └── repository/UserRepository.java
├── src/main/resources/
│   ├── application.properties
│   └── static/index.html
├── pom.xml
├── .gitignore
└── README.md
```

- `UserController.java` – REST endpoints for register, login, and fetch users.  
- `User.java` – Entity class for user table.  
- `UserRepository.java` – JPA repository for database operations.  
- `application.properties` – Database configuration (H2).  
- `index.html` – Optional homepage.  

---

## Setup & Installation (Theory + Commands)

1. **Clone Repository**
```bash
git clone https://github.com/yourusername/bookstore-api.git
cd bookstore-api
```

2. **Initialize Git (if needed)**
```bash
git init
```

3. **Add all files & commit**
```bash
git add .
git commit -m "Initial commit: Spring Boot Bookstore API"
```

4. **Connect GitHub remote & push**
```bash
git remote add origin https://github.com/yourusername/bookstore-api.git
git branch -M main
git push -u origin main
```

5. **Build & run application**
```bash
mvn clean install
mvn spring-boot:run
```

6. **Access homepage**
```
http://localhost:8080/
```
> Displays a welcome message and directs users to `/api/users`.

---

## API Endpoints

| Endpoint        | Method | Description | Request Body Example |
|-----------------|--------|-------------|--------------------|
| `/api/register` | POST   | Register new user | `{ "name": "Sreekanth", "email": "test@example.com", "password": "123456" }` |
| `/api/login`    | POST   | Authenticate user | `{ "email": "test@example.com", "password": "123456" }` |
| `/api/users`    | GET    | Retrieve all users | None |

---

### Example: Register User

**Theory:** Registers a new user. Email must be unique.  

**Command (curl/Postman):**
```bash
curl -X POST http://localhost:8080/api/register -H "Content-Type: application/json" -d '{"name":"Sreekanth","email":"test@example.com","password":"123456"}'
```

**Response:**
```json
{ "message": "User registered successfully!" }
```
**If email exists:**
```json
{ "message": "Email already registered!" }
```

---

### Example: Login User

**Theory:** Authenticates a user.  

**Command:**
```bash
curl -X POST http://localhost:8080/api/login -H "Content-Type: application/json" -d '{"email":"test@example.com","password":"123456"}'
```

**Response (success):**
```json
{
  "message": "Login successful!",
  "name": "Sreekanth"
}
```
**Response (failure):**
```json
{ "message": "User not found!" }
```
or
```json
{ "message": "Invalid password!" }
```

---

### Example: Get All Users

**Theory:** Retrieves all registered users.  

**Command:**
```bash
curl -X GET http://localhost:8080/api/users
```

**Response:**
```json
[
  {
    "id": 1,
    "name": "Sreekanth",
    "email": "test@example.com",
    "password": "123456"
  }
]
```

---

## Database

- **H2 in-memory database** for testing  
- Accessible at: [H2 Console](http://localhost:8080/h2-console)  
- JDBC URL: `jdbc:h2:mem:testdb`  
- Username: `sa`  
- Password: *(empty)*  

> Data is lost on application restart. Use MySQL/PostgreSQL for persistence.

---

## Future Enhancements

- JWT authentication & password hashing (BCrypt)  
- Role-based access (admin/user)  
- CRUD for books & orders  
- Persistent database integration  
- Unit and integration testing  

---

## Quick Git + Run Commands

```bash
# Clone repository
git clone https://github.com/yourusername/bookstore-api.git
cd bookstore-api

# Initialize Git
git init

# Stage & commit
git add .
git commit -m "Initial commit"

# Connect remote & push
git remote add origin https://github.com/yourusername/bookstore-api.git
git branch -M main
git push -u origin main

# Build & run
mvn clean install
mvn spring-boot:run

# Test API with curl or Postman
```

---

✅ This README is **complete, GitHub-ready**, and combines **theory, commands, API examples, and database info** all in a single file.
