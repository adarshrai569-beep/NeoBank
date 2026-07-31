# NEO BANK - Complete Technical Documentation

---

## Table of Contents
1. Executive Summary
2. Introduction
3. System Overview
4. Technology Stack
5. System Architecture
6. UI/UML Diagrams
7. Functional Modules
8. Database Design
9. User Interface Overview
10. API Documentation
11. Security & Validation
12. Testing & Quality Assurance
13. Challenges & Solutions
14. Future Enhancements
15. Conclusion

---

## 1. Executive Summary

Neo Bank is a full-stack digital banking application developed using modern web technologies to provide a secure, scalable, and user-friendly banking platform. The application integrates customer-facing features with a comprehensive admin panel, enabling customers to manage their financial activities while providing administrators with centralized control over banking operations.

### Key Highlights:
- **Full-Stack Implementation**: Angular-based responsive frontend with Spring Boot backend
- **Role-Based Access Control**: Separate user and admin modules with JWT authentication
- **Core Features**: Account management, bill payments, loan applications, budgeting, financial insights, and rewards
- **Security-First Design**: JWT tokens, encryption, input validation, and secure API endpoints
- **Scalable Architecture**: Modular design supporting future enhancements and integrations
- **Production-Ready**: Comprehensive testing, error handling, and exception management

### Technology Stack at a Glance:
- Frontend: Angular, TypeScript, HTML, CSS
- Backend: Java, Spring Boot, Spring Security
- Database: MySQL
- Security: JWT, Route Guards, HTTP Interceptors
- Build Tools: Maven, npm, Git

### Project Outcomes:
- Fully functional banking platform
- Secure authentication and authorization
- Seamless user experience across modules
- Extensible architecture for future features
- Comprehensive API documentation and codebase

---

## 2. Introduction

### 2.1 Objective

The primary objective of Neo Bank is to develop a comprehensive, secure, and user-centric digital banking platform that centralizes banking operations. The application aims to:

1. **Simplify Banking Operations**: Consolidate multiple banking services into a single, intuitive platform
2. **Enhance Security**: Implement industry-standard security practices with JWT-based authentication and role-based access control
3. **Improve User Experience**: Deliver a responsive, clean interface for seamless banking transactions
4. **Enable Administrative Control**: Provide admins with centralized tools to manage banking products and monitor operations
5. **Demonstrate Full-Stack Development**: Showcase practical implementation of modern web development principles
6. **Support Scalability**: Design architecture that can accommodate future enhancements and integrations

### 2.2 Scope

**In Scope:**
- User registration and authentication
- Account management and overview
- Bill payment processing and tracking
- Loan application and status management
- Budget creation and expense tracking
- Financial insights and analytics
- Reward point management
- Admin dashboard with loan product management
- User activity monitoring
- Transaction history and reporting

**Out of Scope:**
- Mobile app development
- Third-party payment gateway integration
- Real-time banking notifications (future enhancement)
- Advanced fraud detection algorithms (future enhancement)
- Cloud deployment (future enhancement)

**Project Duration**: 8-10 weeks
**Development Team**: Full-stack developer (individual project)
**Target Users**: Bank customers (18+ years) and bank administrators

---

## 3. System Overview

### 3.1 Application Overview

Neo Bank is a comprehensive digital banking platform designed to serve two primary user roles:

1. **Regular Users (Customers)**
   - Register and manage accounts securely
   - View account summaries and transaction histories
   - Make bill payments and track payment status
   - Apply for loans and monitor applications
   - Create budgets and track expenses
   - View financial insights and analytics
   - Manage rewards points

2. **Admin Users (Administrators)**
   - Manage loan products and configurations
   - Monitor loan applications and user requests
   - View user activity logs
   - Control banking operations
   - Generate operational reports
   - Manage system-level configurations

### 3.2 Architecture Overview

The application follows a **three-tier architecture pattern**:

```
┌─────────────────────────────────────────┐
│   Presentation Layer (Angular UI)       │
│   - Components, Services, Guards        │
│   - Route-based navigation              │
│   - State management                    │
└────────────────┬────────────────────────┘
                 │ HTTP/REST
                 ▼
┌─────────────────────────────────────────┐
│   API Layer (Spring Boot Controllers)   │
│   - REST endpoints                      │
│   - Request validation                  │
│   - Response formatting                 │
└────────────────┬────────────────────────┘
                 │
┌────────────────┴────────────────────────┐
│   Business Logic Layer (Services)       │
│   - Core banking operations             │
│   - Business rules and validations      │
│   - Transaction processing              │
└────────────────┬────────────────────────┘
                 │
┌────────────────┴────────────────────────┐
│   Data Layer (Repositories & JPA)       │
│   - Database operations                 │
│   - Entity mapping                      │
│   - Query execution                     │
└────────────────┬────────────────────────┘
                 │ JDBC
                 ▼
┌─────────────────────────────────────────┐
│   MySQL Database                        │
│   - Persistent data storage             │
│   - Relational data management          │
└─────────────────────────────────────────┘
```

### 3.3 Key Capabilities

1. **Authentication & Authorization**
   - JWT-based stateless authentication
   - Role-based access control (User, Admin)
   - Secure password handling
   - Token refresh mechanism

2. **Account Management**
   - User registration and profile management
   - Account overview and balance tracking
   - Transaction history and filtering
   - Account linking and configuration

3. **Financial Operations**
   - Bill payment processing
   - Loan application and management
   - Budget creation and tracking
   - Expense categorization and analysis

4. **Analytics & Insights**
   - Financial dashboards
   - Spending patterns analysis
   - Budget vs. actual tracking
   - Predictive insights (future)

5. **Administrative Functions**
   - Loan product management
   - User activity monitoring
   - Request approval workflows
   - Operational reporting

---

## 4. Technology Stack

### Frontend Technologies

| Technology | Version | Purpose |
|-----------|---------|---------|
| Angular | 17+ | Framework for building responsive UI |
| TypeScript | 5.0+ | Type-safe JavaScript for frontend development |
| HTML5 | Latest | Markup language for UI structure |
| CSS3 | Latest | Styling and responsive design |
| Angular Router | 17+ | Client-side routing and navigation |
| Angular Forms | 17+ | Form handling and validation |
| Angular Material | Optional | UI component library |
| RxJS | 7.0+ | Reactive programming and observables |

### Backend Technologies

| Technology | Version | Purpose |
|-----------|---------|---------|
| Java | 11+ | Primary programming language |
| Spring Boot | 2.7+ | Web application framework |
| Spring Security | 5.7+ | Authentication and authorization |
| Spring Data JPA | 2.7+ | ORM and database operations |
| Maven | 3.6+ | Build automation and dependency management |
| Lombok | 1.18+ | Reduce boilerplate code |
| Jackson | 2.13+ | JSON serialization/deserialization |

### Database

| Component | Details |
|-----------|---------|
| Database | MySQL 5.7+ |
| ORM | Hibernate via Spring Data JPA |
| Connection Pool | HikariCP (included with Spring Boot) |
| Migration Tool | Optional: Flyway or Liquibase (future) |

### Security Technologies

| Technology | Purpose |
|-----------|---------|
| JWT (JSON Web Token) | Stateless authentication |
| BCrypt | Password hashing and encryption |
| CORS | Cross-origin resource sharing |
| HTTPS | Secure communication (production) |

### Development & Testing Tools

| Tool | Purpose |
|------|---------|
| VS Code | IDE for frontend development |
| IntelliJ IDEA | IDE for backend development |
| Postman | API testing and documentation |
| Git | Version control system |
| JUnit 5 | Unit testing framework |
| Mockito | Mocking framework for testing |
| npm | Node package manager for frontend |

### Build & Deployment

| Tool | Purpose |
|------|---------|
| Maven | Java build tool and dependency management |
| npm/Angular CLI | Frontend build and development server |
| Docker | Containerization (future) |
| GitHub/GitLab | Repository hosting |

---

## 5. System Architecture

### 5.1 Layered Architecture Pattern

Neo Bank follows a clean, layered architecture that separates concerns and promotes maintainability:

```
┌────────────────────────────────────────────────┐
│         PRESENTATION LAYER                     │
│  ┌──────────────────────────────────────────┐  │
│  │  Angular Components & Templates          │  │
│  │  - LoginComponent                        │  │
│  │  - DashboardComponent                    │  │
│  │  - BillPaymentComponent                  │  │
│  │  - LoanApplicationComponent              │  │
│  │  - BudgetComponent                       │  │
│  │  - AdminDashboardComponent               │  │
│  └──────────────────────────────────────────┘  │
│  ┌──────────────────────────────────────────┐  │
│  │  Angular Services & Guards               │  │
│  │  - AuthService, AccountService           │  │
│  │  - AuthGuard, AdminAuthGuard             │  │
│  │  - JwtInterceptor                        │  │
│  └──────────────────────────────────────────┘  │
└────────────────────────────────────────────────┘
                        ▲
                        │ HTTP REST
                        ▼
┌────────────────────────────────────────────────┐
│         API LAYER (Controllers)                │
│  ┌──────────────────────────────────────────┐  │
│  │  @RestController Annotated Classes:      │  │
│  │  - AuthController                        │  │
│  │  - AccountController                     │  │
│  │  - BillController                        │  │
│  │  - LoanController                        │  │
│  │  - AdminController                       │  │
│  │  - UserController                        │  │
│  └──────────────────────────────────────────┘  │
│  ┌──────────────────────────────────────────┐  │
│  │  Exception Handling & Validation         │  │
│  │  - GlobalExceptionHandler                │  │
│  │  - Custom Validators                     │  │
│  └──────────────────────────────────────────┘  │
└────────────────────────────────────────────────┘
                        ▲
                        │
                        ▼
┌────────────────────────────────────────────────┐
│      BUSINESS LOGIC LAYER (Services)           │
│  ┌──────────────────────────────────────────┐  │
│  │  Service Interfaces & Implementations:   │  │
│  │  - AuthService (Interface + Impl)        │  │
│  │  - AccountService (Interface + Impl)     │  │
│  │  - BillService (Interface + Impl)        │  │
│  │  - LoanService (Interface + Impl)        │  │
│  │  - UserService (Interface + Impl)        │  │
│  │  - BudgetService (Interface + Impl)      │  │
│  │  - RewardService (Interface + Impl)      │  │
│  └──────────────────────────────────────────┘  │
│  ┌──────────────────────────────────────────┐  │
│  │  Business Rules & Validation             │  │
│  │  - Loan eligibility checking             │  │
│  │  - Transaction validation                │  │
│  │  - Budget constraints                    │  │
│  └──────────────────────────────────────────┘  │
└────────────────────────────────────────────────┘
                        ▲
                        │
                        ▼
┌────────────────────────────────────────────────┐
│     DATA ACCESS LAYER (Repositories)           │
│  ┌──────────────────────────────────────────┐  │
│  │  JPA Repository Interfaces:              │  │
│  │  - UserRepository                        │  │
│  │  - AccountRepository                     │  │
│  │  - TransactionRepository                 │  │
│  │  - BillRepository                        │  │
│  │  - LoanRepository                        │  │
│  │  - BudgetRepository                      │  │
│  │  - RewardRepository                      │  │
│  └──────────────────────────────────────────┘  │
│  ┌──────────────────────────────────────────┐  │
│  │  JPA Entities (Domain Models)            │  │
│  │  - User, Account, Transaction            │  │
│  │  - Bill, Loan, Budget, Reward            │  │
│  └──────────────────────────────────────────┘  │
└────────────────────────────────────────────────┘
                        ▲
                        │ JDBC
                        ▼
┌────────────────────────────────────────────────┐
│       MYSQL DATABASE                           │
│  ┌──────────────────────────────────────────┐  │
│  │  Core Tables:                            │  │
│  │  - users, roles, user_roles              │  │
│  │  - accounts, transactions                │  │
│  │                                          │  │
│  │  Finance Tables:                         │  │
│  │  - bills, budgets, rewards               │  │
│  │                                          │  │
│  │  Loan Tables:                            │  │
│  │  - loan_products, loans, loan_documents │  │
│  └──────────────────────────────────────────┘  │
└────────────────────────────────────────────────┘
```

### 5.2 Component Interaction Flow

**User Login Flow:**
```
User Input → LoginComponent → AuthService → 
  AuthController → AuthServiceImpl → UserRepository → 
  Database → JWT Token Generated → Frontend Storage → 
  Redirect to Dashboard
```

**Bill Payment Flow:**
```
User Action → BillPaymentComponent → BillService → 
  BillController → BillServiceImpl → 
  BillRepository & AccountRepository → 
  Database Transaction → Response → UI Update
```

**Loan Application Flow:**
```
User Form → LoanApplicationComponent → LoanService → 
  LoanController → LoanServiceImpl → 
  LoanRepository & AccountRepository → 
  Validation → Database Storage → 
  Confirmation → Admin Notification
```

### 5.3 Security Architecture

```
┌─────────────────────────────────────────┐
│   Client (Angular Application)          │
└────────────────┬────────────────────────┘
                 │
                 │ 1. Login Credentials
                 ▼
┌─────────────────────────────────────────┐
│   AuthController (POST /auth/login)     │
└────────────────┬────────────────────────┘
                 │
                 │ 2. Authenticate User
                 ▼
┌─────────────────────────────────────────┐
│   AuthService (Verify Credentials)      │
│   - UserRepository lookup               │
│   - Password validation (BCrypt)        │
└────────────────┬────────────────────────┘
                 │
                 │ 3. Generate JWT Token
                 ▼
┌─────────────────────────────────────────┐
│   JWT Token (Header.Payload.Signature)  │
│   - User ID, Role, Expiry               │
└────────────────┬────────────────────────┘
                 │
                 │ 4. Return Token to Client
                 ▼
┌─────────────────────────────────────────┐
│   Angular Frontend                      │
│   - Store Token in LocalStorage         │
│   - Attach to JwtInterceptor            │
└────────────────┬────────────────────────┘
                 │
                 │ 5. Subsequent Requests
                 │    (Token in Header)
                 ▼
┌─────────────────────────────────────────┐
│   Protected API Endpoints               │
│   @PreAuthorize("hasRole('ADMIN')")     │
│   @PreAuthorize("hasRole('USER')")      │
└────────────────┬────────────────────────┘
                 │
                 │ 6. Validate Token
                 ▼
┌─────────────────────────────────────────┐
│   JwtTokenProvider                      │
│   - Verify signature                    │
│   - Check expiry                        │
│   - Extract claims                      │
└────────────────┬────────────────────────┘
                 │
                 │ 7. Grant/Deny Access
                 ▼
         ┌───────┴────────┐
         │                │
    (Valid Token)    (Invalid/Expired)
         │                │
         ▼                ▼
    Execute API    Return 401/403
    Return Data    Redirect to Login
```

---

## 6. UI/UML Diagrams

### 6.1 Entity Relationship Diagram (ERD)

```
┌──────────────┐         ┌──────────────┐
│    USER      │         │    ROLE      │
├──────────────┤         ├──────────────┤
│ user_id (PK) │────┐    │ role_id (PK) │
│ username     │    │    │ role_name    │
│ email        │    │    │              │
│ password     │    │    └──────────────┘
│ phone        │    │
│ is_active    │    │    ┌──────────────┐
│ created_at   │    └────┤  USER_ROLE   │
│ updated_at   │         ├──────────────┤
└──────────────┘         │ user_id (FK) │
       │                 │ role_id (FK) │
       │                 └──────────────┘
       │
       │         ┌──────────────────┐
       ├─────────┤  ACCOUNT         │
       │         ├──────────────────┤
       │         │ account_id (PK)  │
       │         │ user_id (FK)     │
       │         │ account_number   │
       │         │ balance          │
       │         │ account_type     │
       │         │ currency         │
       │         │ status           │
       │         │ created_at       │
       │         │ updated_at       │
       │         └──────────────────┘
       │                │
       │                │
       │         ┌──────┴────────────────┐
       │         │                       │
       │         ▼                       ▼
       │    ┌─────────────┐      ┌─────────────┐
       │    │TRANSACTION  │      │BUDGET       │
       │    ├─────────────┤      ├─────────────┤
       │    │ trans_id(PK)│      │ budget_id(P)│
       │    │ account_id  │      │ user_id(FK) │
       │    │ amount      │      │ category    │
       │    │ type        │      │ limit       │
       │    │ status      │      │ spent       │
       │    │ created_at  │      │ start_date  │
       │    └─────────────┘      │ end_date    │
       │                         └─────────────┘
       │
       │         ┌──────────────────┐
       └─────────┤  BILL            │
               ├──────────────────┤
               │ bill_id (PK)     │
               │ user_id (FK)     │
               │ account_id (FK)  │
               │ amount           │
               │ due_date         │
               │ status           │
               │ description      │
               │ created_at       │
               └──────────────────┘

┌──────────────────┐         ┌──────────────────┐
│  LOAN_PRODUCT    │         │  LOAN            │
├──────────────────┤         ├──────────────────┤
│ product_id (PK)  │────┐    │ loan_id (PK)     │
│ name             │    │    │ product_id (FK)  │
│ interest_rate    │    │    │ user_id (FK)     │
│ tenure_months    │    │    │ amount           │
│ max_amount       │    │    │ approved_amount  │
│ min_amount       │    │    │ status           │
│ eligibility      │    │    │ applied_date     │
│ is_active        │    │    │ approved_date    │
└──────────────────┘    │    │ disbursed_date   │
                        │    └──────────────────┘
                        │              │
                        │              ▼
                        │    ┌──────────────────┐
                        │    │LOAN_DOCUMENT     │
                        │    ├──────────────────┤
                        │    │ doc_id (PK)      │
                        │    │ loan_id (FK)     │
                        │    │ doc_type         │
                        │    │ file_path        │
                        │    │ uploaded_date    │
                        │    └──────────────────┘

┌──────────────────┐
│  REWARD          │
├──────────────────┤
│ reward_id (PK)   │
│ user_id (FK)     │
│ points           │
│ transaction_type │
│ earned_date      │
│ expires_at       │
└──────────────────┘
```

### 6.2 Use Case Diagram

```
                        ┌─────────────────┐
                        │  Neo Bank System│
                        └─────────────────┘
                               │
                ┌──────────────┬┴──────────────┐
                │                             │
           ┌────▼────┐                   ┌───▼────┐
           │   USER  │                   │  ADMIN │
           └────┬────┘                   └───┬────┘
                │                            │
    ┌───────────┼──────────────┐             │
    │           │              │             │
    ▼           ▼              ▼             ▼
┌────────┐ ┌────────┐ ┌──────────┐  ┌──────────────┐
│Register│ │  Login │ │Dashboard │  │ Admin Login  │
└────────┘ └────┬───┘ └────┬─────┘  └──────┬───────┘
                │           │               │
        ┌───────┴────────┐   │       ┌───────┴──────────┐
        │                │   │       │                  │
        ▼                ▼   ▼       ▼                  ▼
    ┌────────┐     ┌─────────────┐  ┌──────────────┐  ┌──────────────┐
    │ Profile│     │Transaction  │  │Loan Product  │  │Monitor Users │
    │Mgmt    │     │History      │  │Management    │  │              │
    └────────┘     └─────────────┘  └──────────────┘  └──────────────┘
                           │
            ┌──────────────┼──────────────┐
            │              │              │
            ▼              ▼              ▼
        ┌────────┐   ┌─────────┐   ┌──────────┐
        │Pay Bill│   │Apply for│   │View Budget│
        │        │   │Loan     │   │& Insights │
        └────────┘   └─────────┘   └──────────┘
```

### 6.3 Activity Diagram (User Registration)

```
  ╔════════════════════════════════════════╗
  ║  User Opens Neo Bank Application      ║
  ╚═════════════┬════════════════════════╝
                │
                ▼
        ┌───────────────────┐
        │ Click "Register"  │
        └────────┬──────────┘
                 │
                 ▼
        ┌──────────────────────────┐
        │ Enter Registration Form: │
        │ - Username               │
        │ - Email                  │
        │ - Password               │
        │ - Confirm Password       │
        │ - Phone Number           │
        └────────┬─────────────────┘
                 │
                 ▼
        ┌──────────────────────────┐
        │ Validate Input Data:     │
        │ - Check required fields  │
        │ - Email format           │
        │ - Password strength      │
        └────────┬─────────────────┘
                 │
        ┌────────┴────────┐
        │                 │
    ▼  (Invalid)    ▼  (Valid)
 ┌─────────┐       ┌────────────────┐
 │Show Error│      │Check Username  │
 │Message  │      │Exists          │
 └────┬────┘       └────┬───────────┘
      │                 │
      │          ┌──────┴───────┐
      │          │              │
      │      ▼ (Exists)    ▼ (Not Exists)
      │   ┌──────────┐   ┌──────────────────┐
      │   │Show Error│   │Hash Password     │
      │   │          │   │with BCrypt       │
      │   └────┬─────┘   └────┬─────────────┘
      │        │              │
      │        │              ▼
      │        │       ┌──────────────────┐
      │        │       │Save User in DB   │
      │        │       │Create User Role  │
      │        │       │(USER role)       │
      │        │       └────┬─────────────┘
      │        │            │
      └────────┼────────────┬┘
               │            │
               ▼            ▼
        ┌──────────────────────────┐
        │ Registration Successful  │
        │ Redirect to Login        │
        └──────────────────────────┘
```

---

## 7. Functional Modules

### 7.1 Authentication & User Management

#### Overview
The Authentication & User Management module handles user registration, login, password management, and role-based access control.

#### Key Components

**Frontend (Angular)**
- `LoginComponent` - User login interface
- `RegisterComponent` - User registration form
- `AuthService` - Authentication logic
- `JwtInterceptor` - Automatic token attachment to requests
- `AuthGuard` - Route protection for authenticated users
- `AdminAuthGuard` - Route protection for admin users

**Backend (Spring Boot)**
- `AuthController` - REST endpoints for login/register
- `AuthService` - Core authentication logic
- `JwtTokenProvider` - JWT token generation and validation
- `UserService` - User CRUD operations
- `PasswordEncoder` - BCrypt password hashing

#### Key Features

1. **User Registration**
   - Username and email validation
   - Password strength requirements
   - Unique email check
   - Default USER role assignment
   - Automatic account creation

2. **User Login**
   - Credential verification
   - JWT token generation
   - Token storage in frontend
   - Automatic token refresh

3. **Role-Based Access**
   - Two roles: USER and ADMIN
   - Endpoint-level authorization
   - Frontend route guards

#### API Endpoints

```
POST /api/auth/register
- Request: { username, email, password, phone }
- Response: { message, status }

POST /api/auth/login
- Request: { email, password }
- Response: { token, userId, username, role }

POST /api/auth/logout
- Request: { token }
- Response: { message }

GET /api/auth/validate-token
- Request: Authorization: Bearer {token}
- Response: { valid, userId, role }
```

#### Security Features

- Password hashing with BCrypt
- JWT token expiry (24 hours)
- CORS enabled for frontend domain
- Token validation on every request
- Role-based endpoint access

#### Database Schema

```sql
CREATE TABLE users (
    user_id INT PRIMARY KEY AUTO_INCREMENT,
    username VARCHAR(255) UNIQUE NOT NULL,
    email VARCHAR(255) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    phone VARCHAR(20),
    is_active BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);

CREATE TABLE roles (
    role_id INT PRIMARY KEY AUTO_INCREMENT,
    role_name VARCHAR(50) UNIQUE NOT NULL
);

CREATE TABLE user_role (
    user_id INT,
    role_id INT,
    PRIMARY KEY (user_id, role_id),
    FOREIGN KEY (user_id) REFERENCES users(user_id),
    FOREIGN KEY (role_id) REFERENCES roles(role_id)
);
```

---

### 7.2 Account & Transaction Management

#### Overview
This module manages user accounts, balances, and transaction history.

#### Key Components

**Frontend**
- `AccountService` - Account operations
- `DashboardComponent` - Account overview
- `TransactionHistoryComponent` - Transaction listing

**Backend**
- `AccountController` - Account endpoints
- `AccountService` - Business logic
- `TransactionService` - Transaction operations
- `AccountRepository`, `TransactionRepository` - Data access

#### Key Features

1. **Account Management**
   - Multiple account support per user
   - Account types (Savings, Checking)
   - Account balance tracking
   - Account status management

2. **Transaction Tracking**
   - Complete transaction history
   - Transaction filtering (date, amount, type)
   - Transaction details view
   - Balance updates on transactions

#### API Endpoints

```
GET /api/accounts
- Response: [{ accountId, accountNumber, balance, type, status }]

GET /api/accounts/{accountId}
- Response: { accountId, accountNumber, balance, type, currency }

GET /api/accounts/{accountId}/transactions
- Query params: from, to, type, limit
- Response: [{ transactionId, amount, type, date, description }]

GET /api/accounts/{accountId}/balance
- Response: { balance, lastUpdated }
```

#### Database Schema

```sql
CREATE TABLE accounts (
    account_id INT PRIMARY KEY AUTO_INCREMENT,
    user_id INT NOT NULL,
    account_number VARCHAR(50) UNIQUE NOT NULL,
    balance DECIMAL(15, 2) DEFAULT 0,
    account_type VARCHAR(50),
    currency VARCHAR(10) DEFAULT 'USD',
    status VARCHAR(50) DEFAULT 'ACTIVE',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(user_id)
);

CREATE TABLE transactions (
    transaction_id INT PRIMARY KEY AUTO_INCREMENT,
    account_id INT NOT NULL,
    amount DECIMAL(15, 2) NOT NULL,
    transaction_type VARCHAR(50),
    description VARCHAR(255),
    status VARCHAR(50),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (account_id) REFERENCES accounts(account_id)
);
```

---

### 7.3 Budgeting & Expense Management

#### Overview
Helps users create budgets and track expenses against budget limits.

#### Key Components

**Frontend**
- `BudgetComponent` - Budget creation and management
- `BudgetService` - Budget operations

**Backend**
- `BudgetController` - Budget endpoints
- `BudgetService` - Business logic
- `BudgetRepository` - Data access

#### Key Features

1. **Budget Creation**
   - Category-based budgets
   - Monthly budget limits
   - Custom category creation
   - Budget alerts

2. **Expense Tracking**
   - Categorize expenses
   - Track spending vs. budget
   - Visual budget progress
   - Budget recommendations

#### API Endpoints

```
POST /api/budgets
- Request: { category, limit, startDate, endDate }
- Response: { budgetId, category, limit, spent }

GET /api/budgets
- Response: [{ budgetId, category, limit, spent, percentage }]

PUT /api/budgets/{budgetId}
- Request: { limit, category }
- Response: { budgetId, category, limit }

DELETE /api/budgets/{budgetId}
- Response: { message, status }

GET /api/budgets/{budgetId}/spending
- Response: { spent, limit, remaining, percentage }
```

#### Database Schema

```sql
CREATE TABLE budgets (
    budget_id INT PRIMARY KEY AUTO_INCREMENT,
    user_id INT NOT NULL,
    category VARCHAR(100) NOT NULL,
    budget_limit DECIMAL(15, 2) NOT NULL,
    spent DECIMAL(15, 2) DEFAULT 0,
    start_date DATE NOT NULL,
    end_date DATE NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(user_id)
);
```

---

### 7.4 Bills, Rewards & Notifications

#### Overview
Manages bill payments and reward points for users.

#### Key Components

**Frontend**
- `BillPaymentComponent` - Bill payment interface
- `BillService` - Bill operations
- `RewardComponent` - Reward display

**Backend**
- `BillController`, `RewardController`
- `BillService`, `RewardService`
- `BillRepository`, `RewardRepository`

#### Key Features

1. **Bill Management**
   - Add bills and due dates
   - Mark bills as paid/pending
   - Track payment history
   - Payment reminders

2. **Reward System**
   - Earn points on transactions
   - Redeem rewards
   - Track reward balance
   - Reward expiry dates

#### API Endpoints

```
POST /api/bills
- Request: { accountId, amount, dueDate, description }
- Response: { billId, amount, status, dueDate }

GET /api/bills
- Query params: status, from, to
- Response: [{ billId, amount, dueDate, status }]

POST /api/bills/{billId}/pay
- Request: { amount }
- Response: { billId, status, paidDate }

GET /api/rewards
- Response: { totalPoints, usablePoints, expiredPoints }

POST /api/rewards/redeem
- Request: { rewardId, points }
- Response: { message, remainingPoints }
```

#### Database Schema

```sql
CREATE TABLE bills (
    bill_id INT PRIMARY KEY AUTO_INCREMENT,
    user_id INT NOT NULL,
    account_id INT NOT NULL,
    amount DECIMAL(15, 2) NOT NULL,
    due_date DATE NOT NULL,
    status VARCHAR(50) DEFAULT 'PENDING',
    description VARCHAR(255),
    paid_date DATE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(user_id),
    FOREIGN KEY (account_id) REFERENCES accounts(account_id)
);

CREATE TABLE rewards (
    reward_id INT PRIMARY KEY AUTO_INCREMENT,
    user_id INT NOT NULL,
    points INT DEFAULT 0,
    transaction_type VARCHAR(100),
    earned_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    expires_at DATE,
    FOREIGN KEY (user_id) REFERENCES users(user_id)
);
```

---

### 7.5 Loan Management System

#### Overview
Handles loan products, applications, approvals, and disbursements.

#### Key Components

**Frontend**
- `LoanApplicationComponent` - Loan application form
- `LoanStatusComponent` - Application status tracking
- `LoanService` - Loan operations

**Backend**
- `LoanController`, `LoanProductController`
- `LoanService`, `LoanProductService`
- `LoanRepository`, `LoanProductRepository`

#### Key Features

1. **Loan Products**
   - Define loan products with rates, tenure
   - Set eligibility criteria
   - Configure min/max amounts
   - Product management (admin only)

2. **Loan Applications**
   - Users apply for loans
   - Automatic eligibility checking
   - Document upload support
   - Status tracking (Applied, Approved, Rejected, Disbursed)

3. **Admin Controls**
   - Review applications
   - Approve/reject loans
   - Track disbursements
   - Manage products

#### API Endpoints

```
GET /api/loan-products
- Response: [{ productId, name, rate, tenure, minAmount, maxAmount }]

POST /api/loans
- Request: { productId, amount, accountId }
- Response: { loanId, status, appliedDate }

GET /api/loans
- Response: [{ loanId, status, amount, appliedDate, approvedDate }]

GET /api/loans/{loanId}
- Response: { loanId, productId, amount, status, documents }

POST /api/loans/{loanId}/upload-document
- Request: Form file
- Response: { documentId, fileName, uploadDate }

# Admin endpoints
GET /api/admin/loans
- Response: [{ loanId, userId, status, amount, appliedDate }]

POST /api/admin/loans/{loanId}/approve
- Request: { approvedAmount }
- Response: { loanId, status, approvedAmount }

POST /api/admin/loans/{loanId}/reject
- Request: { reason }
- Response: { loanId, status, rejectionReason }

POST /api/admin/loan-products
- Request: { name, rate, tenure, minAmount, maxAmount }
- Response: { productId, name, rate }
```

#### Database Schema

```sql
CREATE TABLE loan_products (
    product_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    interest_rate DECIMAL(5, 2) NOT NULL,
    tenure_months INT NOT NULL,
    max_amount DECIMAL(15, 2) NOT NULL,
    min_amount DECIMAL(15, 2) NOT NULL,
    eligibility_criteria VARCHAR(500),
    is_active BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE loans (
    loan_id INT PRIMARY KEY AUTO_INCREMENT,
    product_id INT NOT NULL,
    user_id INT NOT NULL,
    account_id INT NOT NULL,
    applied_amount DECIMAL(15, 2) NOT NULL,
    approved_amount DECIMAL(15, 2),
    status VARCHAR(50) DEFAULT 'APPLIED',
    applied_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    approved_date TIMESTAMP,
    disbursed_date TIMESTAMP,
    reason_for_rejection VARCHAR(500),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    FOREIGN KEY (product_id) REFERENCES loan_products(product_id),
    FOREIGN KEY (user_id) REFERENCES users(user_id),
    FOREIGN KEY (account_id) REFERENCES accounts(account_id)
);

CREATE TABLE loan_documents (
    document_id INT PRIMARY KEY AUTO_INCREMENT,
    loan_id INT NOT NULL,
    document_type VARCHAR(100),
    file_path VARCHAR(500),
    uploaded_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (loan_id) REFERENCES loans(loan_id)
);
```

---

### 7.6 Financial Insights & Analytics

#### Overview
Provides users with analytics and insights about their financial activities.

#### Key Components

**Frontend**
- `InsightsComponent` - Insights dashboard
- `InsightsService` - Analytics logic
- `ChartsComponent` - Visualization

**Backend**
- `InsightsController` - Endpoints
- `InsightsService` - Business logic

#### Key Features

1. **Spending Analysis**
   - Monthly spending breakdown
   - Category-wise analysis
   - Spending trends
   - Budget adherence

2. **Financial Insights**
   - Income vs. expense analysis
   - Savings rate calculation
   - Account health score
   - Recommendations

#### API Endpoints

```
GET /api/insights/spending
- Query params: from, to, period
- Response: { totalSpending, byCategory: [...], trend: [...] }

GET /api/insights/analysis
- Response: { income, expense, savings, savingsRate }

GET /api/insights/budget-comparison
- Response: [{ category, budget, spent, percentage }]

GET /api/insights/recommendations
- Response: [{ category, recommendation, priority }]
```

---

### 7.7 Admin Dashboard & Controls

#### Overview
Provides administrators with complete control and visibility over banking operations.

#### Key Components

**Frontend**
- `AdminDashboardComponent` - Admin overview
- `AdminService` - Admin operations

**Backend**
- `AdminController` - Admin endpoints
- `AdminService` - Business logic

#### Key Features

1. **User Management**
   - View all users
   - User activity monitoring
   - Account status control
   - User reports

2. **Loan Operations**
   - View all loan applications
   - Approve/reject loans
   - Product management
   - Loan status tracking

3. **System Monitoring**
   - Transaction volumes
   - System health
   - Error logs
   - Performance metrics

#### API Endpoints

```
GET /api/admin/users
- Response: [{ userId, username, email, status, createdDate }]

GET /api/admin/users/{userId}
- Response: { userId, username, email, accounts, loans, activity }

GET /api/admin/transactions
- Query params: from, to, limit
- Response: [{ transactionId, userId, amount, type, date }]

GET /api/admin/dashboard
- Response: { totalUsers, totalTransactions, totalLoans, revenue }

GET /api/admin/reports/monthly
- Response: { period, transactions, revenue, newUsers, loanStats }
```

---

## 8. Database Design

### 8.1 Core Tables

#### Users Table
Stores user account information and authentication details.

```sql
CREATE TABLE users (
    user_id INT PRIMARY KEY AUTO_INCREMENT,
    username VARCHAR(255) UNIQUE NOT NULL,
    email VARCHAR(255) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    phone VARCHAR(20),
    full_name VARCHAR(255),
    date_of_birth DATE,
    address VARCHAR(500),
    city VARCHAR(100),
    state VARCHAR(100),
    postal_code VARCHAR(20),
    country VARCHAR(100),
    is_active BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);
```

**Indexes:**
- PRIMARY KEY: user_id
- UNIQUE: username, email
- INDEX: is_active, created_at

#### Roles Table
Manages user roles and permissions.

```sql
CREATE TABLE roles (
    role_id INT PRIMARY KEY AUTO_INCREMENT,
    role_name VARCHAR(50) UNIQUE NOT NULL,
    description VARCHAR(255),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Insert default roles
INSERT INTO roles (role_name, description) VALUES 
('USER', 'Regular banking customer'),
('ADMIN', 'Banking administrator');
```

#### User_Role Table
Junction table for user-role mapping (many-to-many relationship).

```sql
CREATE TABLE user_role (
    user_id INT NOT NULL,
    role_id INT NOT NULL,
    assigned_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    PRIMARY KEY (user_id, role_id),
    FOREIGN KEY (user_id) REFERENCES users(user_id) ON DELETE CASCADE,
    FOREIGN KEY (role_id) REFERENCES roles(role_id) ON DELETE CASCADE
);
```

### 8.2 Finance Tables

#### Accounts Table
Stores bank account information for users.

```sql
CREATE TABLE accounts (
    account_id INT PRIMARY KEY AUTO_INCREMENT,
    user_id INT NOT NULL,
    account_number VARCHAR(50) UNIQUE NOT NULL,
    account_holder_name VARCHAR(255) NOT NULL,
    account_type VARCHAR(50) NOT NULL,
    balance DECIMAL(15, 2) DEFAULT 0,
    currency VARCHAR(10) DEFAULT 'USD',
    status VARCHAR(50) DEFAULT 'ACTIVE',
    branch_code VARCHAR(50),
    ifsc_code VARCHAR(20),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(user_id) ON DELETE CASCADE,
    INDEX (user_id),
    INDEX (status),
    UNIQUE INDEX (account_number)
);
```

#### Transactions Table
Logs all financial transactions.

```sql
CREATE TABLE transactions (
    transaction_id INT PRIMARY KEY AUTO_INCREMENT,
    account_id INT NOT NULL,
    transaction_type VARCHAR(50) NOT NULL,
    amount DECIMAL(15, 2) NOT NULL,
    reference_id VARCHAR(100),
    description VARCHAR(500),
    status VARCHAR(50) DEFAULT 'COMPLETED',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    FOREIGN KEY (account_id) REFERENCES accounts(account_id) ON DELETE CASCADE,
    INDEX (account_id),
    INDEX (transaction_type),
    INDEX (created_at)
);
```

#### Bills Table
Stores bill payment records.

```sql
CREATE TABLE bills (
    bill_id INT PRIMARY KEY AUTO_INCREMENT,
    user_id INT NOT NULL,
    account_id INT NOT NULL,
    amount DECIMAL(15, 2) NOT NULL,
    due_date DATE NOT NULL,
    status VARCHAR(50) DEFAULT 'PENDING',
    description VARCHAR(500),
    paid_date DATE,
    paid_amount DECIMAL(15, 2),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(user_id) ON DELETE CASCADE,
    FOREIGN KEY (account_id) REFERENCES accounts(account_id) ON DELETE CASCADE,
    INDEX (user_id),
    INDEX (status),
    INDEX (due_date)
);
```

#### Budgets Table
Stores user budget configurations.

```sql
CREATE TABLE budgets (
    budget_id INT PRIMARY KEY AUTO_INCREMENT,
    user_id INT NOT NULL,
    category VARCHAR(100) NOT NULL,
    budget_limit DECIMAL(15, 2) NOT NULL,
    spent DECIMAL(15, 2) DEFAULT 0,
    start_date DATE NOT NULL,
    end_date DATE NOT NULL,
    status VARCHAR(50) DEFAULT 'ACTIVE',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(user_id) ON DELETE CASCADE,
    INDEX (user_id),
    INDEX (category),
    UNIQUE INDEX (user_id, category, start_date)
);
```

#### Rewards Table
Stores reward points and redemption history.

```sql
CREATE TABLE rewards (
    reward_id INT PRIMARY KEY AUTO_INCREMENT,
    user_id INT NOT NULL,
    points INT DEFAULT 0,
    transaction_type VARCHAR(100),
    earned_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    expires_at DATE,
    is_redeemed BOOLEAN DEFAULT FALSE,
    redeemed_date TIMESTAMP,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(user_id) ON DELETE CASCADE,
    INDEX (user_id),
    INDEX (is_redeemed),
    INDEX (expires_at)
);
```

### 8.3 Loan Tables

#### LoanProducts Table
Defines available loan products offered by the bank.

```sql
CREATE TABLE loan_products (
    product_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    description VARCHAR(500),
    interest_rate DECIMAL(5, 2) NOT NULL,
    tenure_months INT NOT NULL,
    max_amount DECIMAL(15, 2) NOT NULL,
    min_amount DECIMAL(15, 2) NOT NULL,
    processing_fee DECIMAL(15, 2) DEFAULT 0,
    prepayment_allowed BOOLEAN DEFAULT TRUE,
    prepayment_charges DECIMAL(5, 2),
    eligibility_criteria VARCHAR(1000),
    is_active BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    INDEX (is_active),
    UNIQUE INDEX (name)
);
```

#### Loans Table
Stores loan application records.

```sql
CREATE TABLE loans (
    loan_id INT PRIMARY KEY AUTO_INCREMENT,
    product_id INT NOT NULL,
    user_id INT NOT NULL,
    account_id INT NOT NULL,
    applied_amount DECIMAL(15, 2) NOT NULL,
    approved_amount DECIMAL(15, 2),
    monthly_emi DECIMAL(15, 2),
    status VARCHAR(50) DEFAULT 'APPLIED',
    applied_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    approved_date TIMESTAMP,
    disbursed_date TIMESTAMP,
    maturity_date DATE,
    reason_for_rejection VARCHAR(500),
    approval_notes VARCHAR(500),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    FOREIGN KEY (product_id) REFERENCES loan_products(product_id),
    FOREIGN KEY (user_id) REFERENCES users(user_id) ON DELETE CASCADE,
    FOREIGN KEY (account_id) REFERENCES accounts(account_id) ON DELETE CASCADE,
    INDEX (user_id),
    INDEX (status),
    INDEX (applied_date),
    UNIQUE INDEX (product_id, user_id, applied_date)
);
```

#### LoanDocuments Table
Stores loan application documents.

```sql
CREATE TABLE loan_documents (
    document_id INT PRIMARY KEY AUTO_INCREMENT,
    loan_id INT NOT NULL,
    document_type VARCHAR(100),
    file_name VARCHAR(255),
    file_path VARCHAR(500),
    file_size BIGINT,
    uploaded_by INT,
    uploaded_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    is_verified BOOLEAN DEFAULT FALSE,
    verified_by INT,
    verified_date TIMESTAMP,
    FOREIGN KEY (loan_id) REFERENCES loans(loan_id) ON DELETE CASCADE,
    FOREIGN KEY (uploaded_by) REFERENCES users(user_id),
    FOREIGN KEY (verified_by) REFERENCES users(user_id),
    INDEX (loan_id),
    INDEX (document_type),
    INDEX (is_verified)
);
```

#### LoanEMI Table (Future Enhancement)
Track EMI payments for loans.

```sql
CREATE TABLE loan_emi (
    emi_id INT PRIMARY KEY AUTO_INCREMENT,
    loan_id INT NOT NULL,
    emi_number INT NOT NULL,
    emi_amount DECIMAL(15, 2) NOT NULL,
    due_date DATE NOT NULL,
    paid_date DATE,
    status VARCHAR(50) DEFAULT 'PENDING',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (loan_id) REFERENCES loans(loan_id) ON DELETE CASCADE,
    INDEX (loan_id),
    INDEX (due_date),
    UNIQUE INDEX (loan_id, emi_number)
);
```

---

## 9. User Interface Overview

### 9.1 User Interface Components

#### Login & Registration
- Clean, minimal design
- Email/password validation
- Responsive layout
- Error message display

#### Dashboard
- Account summary cards
- Quick action buttons
- Transaction widgets
- Balance overview
- Responsive grid layout

#### Bill Payment
- Bill selection and preview
- Amount confirmation
- Payment confirmation modal
- Success/failure messages

#### Loan Application
- Loan product selection
- Application form
- Amount and tenure selection
- Document upload
- Application summary

#### Budget & Insights
- Budget creation interface
- Visual budget progress bars
- Expense categorization
- Chart visualizations
- Spending analysis

#### Admin Dashboard
- User list and search
- Loan application queue
- Product management grid
- Transaction dashboard
- Reports section

### 9.2 Navigation Structure

```
Neo Bank Application
├── Public Routes
│   ├── /login
│   ├── /register
│   └── /home
│
├── User Routes (Protected by AuthGuard)
│   ├── /dashboard
│   ├── /accounts
│   ├── /bills
│   │   └── /bills/pay
│   ├── /loans
│   │   ├── /loans/apply
│   │   └── /loans/:id
│   ├── /budget
│   ├── /insights
│   ├── /rewards
│   └── /profile
│
└── Admin Routes (Protected by AdminAuthGuard)
    ├── /admin/dashboard
    ├── /admin/users
    ├── /admin/loans
    ├── /admin/loan-products
    ├── /admin/transactions
    └── /admin/reports
```

### 9.3 Key UI Features

1. **Responsive Design**
   - Mobile-first approach
   - Works on desktop, tablet, mobile
   - Flexible grid layouts
   - Touch-friendly buttons

2. **User Feedback**
   - Loading spinners
   - Success/error messages
   - Form validation feedback
   - Toast notifications

3. **Accessibility**
   - Semantic HTML
   - ARIA labels
   - Keyboard navigation
   - Color contrast compliance

4. **Performance**
   - Lazy loading modules
   - Image optimization
   - Caching strategies
   - Minimal external dependencies

---

## 10. API Documentation

### 10.1 API Base URL
```
Production: https://api.neobank.com
Development: http://localhost:8080
```

### 10.2 Authentication

All protected endpoints require JWT token in Authorization header:
```
Authorization: Bearer {jwt_token}
```

### 10.3 Response Format

Success Response:
```json
{
  "success": true,
  "message": "Operation successful",
  "data": {
    // Response data
  },
  "timestamp": "2024-01-15T10:30:00Z"
}
```

Error Response:
```json
{
  "success": false,
  "message": "Error description",
  "errorCode": "ERROR_CODE",
  "details": {
    // Error details
  },
  "timestamp": "2024-01-15T10:30:00Z"
}
```

### 10.4 API Endpoints Summary

#### Authentication APIs
```
POST /api/auth/register - Register new user
POST /api/auth/login - Login user
POST /api/auth/logout - Logout user
GET /api/auth/validate-token - Validate JWT token
POST /api/auth/refresh-token - Refresh JWT token
```

#### Account APIs
```
GET /api/accounts - List user accounts
GET /api/accounts/{id} - Get account details
GET /api/accounts/{id}/balance - Get account balance
GET /api/accounts/{id}/transactions - List transactions
GET /api/accounts/{id}/statement - Download statement
```

#### Bill APIs
```
GET /api/bills - List bills
POST /api/bills - Create new bill
POST /api/bills/{id}/pay - Pay a bill
GET /api/bills/{id} - Get bill details
PUT /api/bills/{id} - Update bill
DELETE /api/bills/{id} - Delete bill
```

#### Loan APIs
```
GET /api/loan-products - List loan products
POST /api/loans - Apply for loan
GET /api/loans - List user loans
GET /api/loans/{id} - Get loan details
POST /api/loans/{id}/upload-document - Upload document
GET /api/loans/{id}/documents - List documents
```

#### Budget APIs
```
GET /api/budgets - List budgets
POST /api/budgets - Create budget
PUT /api/budgets/{id} - Update budget
DELETE /api/budgets/{id} - Delete budget
GET /api/budgets/{id}/spending - Get spending details
```

#### Insights APIs
```
GET /api/insights/dashboard - Dashboard data
GET /api/insights/spending - Spending analysis
GET /api/insights/analysis - Financial analysis
GET /api/insights/recommendations - Recommendations
GET /api/insights/reports - Generate reports
```

#### Reward APIs
```
GET /api/rewards - Get reward balance
POST /api/rewards/redeem - Redeem rewards
GET /api/rewards/history - Reward history
GET /api/rewards/expiring - Expiring rewards
```

#### Admin APIs
```
GET /api/admin/users - List all users
GET /api/admin/users/{id} - Get user details
GET /api/admin/loans - List all loans
POST /api/admin/loans/{id}/approve - Approve loan
POST /api/admin/loans/{id}/reject - Reject loan
GET /api/admin/loan-products - List products
POST /api/admin/loan-products - Create product
PUT /api/admin/loan-products/{id} - Update product
DELETE /api/admin/loan-products/{id} - Delete product
GET /api/admin/transactions - List transactions
GET /api/admin/dashboard - Dashboard data
GET /api/admin/reports - Generate reports
```

### 10.5 HTTP Status Codes

| Code | Meaning |
|------|---------|
| 200 | OK - Request successful |
| 201 | Created - Resource created |
| 400 | Bad Request - Invalid parameters |
| 401 | Unauthorized - Authentication required |
| 403 | Forbidden - Access denied |
| 404 | Not Found - Resource not found |
| 409 | Conflict - Duplicate resource |
| 500 | Server Error - Internal error |
| 503 | Service Unavailable - Maintenance |

---

## 11. Security & Validation

### 11.1 Authentication Security

1. **JWT Implementation**
   - Algorithm: HS256 (HMAC with SHA-256)
   - Secret Key: Environment variable (production)
   - Token Expiry: 24 hours
   - Refresh Token: 7 days

2. **Password Security**
   - Hashing: BCrypt with salt (strength 10)
   - Minimum length: 8 characters
   - Complexity: Mix of uppercase, lowercase, numbers, special characters
   - Never stored in plain text

3. **Token Management**
   - Tokens stored in HttpOnly cookies (frontend localStorage for now)
   - Token validation on every request
   - Automatic token refresh
   - Token blacklisting on logout

### 11.2 Authorization

1. **Role-Based Access Control (RBAC)**
   ```
   USER Role:
   - Access own dashboard
   - Manage own accounts
   - Apply for loans
   - Pay bills
   - View insights
   
   ADMIN Role:
   - Access admin dashboard
   - Manage loan products
   - Approve/reject loans
   - View all transactions
   - Generate reports
   - Manage users
   ```

2. **Endpoint Protection**
   ```java
   @PreAuthorize("hasRole('USER')")
   public ResponseEntity getMyAccounts() { }
   
   @PreAuthorize("hasRole('ADMIN')")
   public ResponseEntity getAllLoans() { }
   ```

3. **Frontend Route Guards**
   - AuthGuard for user routes
   - AdminAuthGuard for admin routes
   - Redirect to login if unauthorized

### 11.3 Input Validation

#### Frontend Validation
- Required field checks
- Email format validation
- Phone number format
- Password strength validation
- Amount validation (numeric, positive)
- Date validation (future dates for bills)

#### Backend Validation
```java
@Entity
public class User {
    @NotBlank(message = "Username cannot be empty")
    @Size(min = 3, max = 50)
    private String username;
    
    @Email(message = "Invalid email format")
    private String email;
    
    @NotBlank(message = "Password required")
    @Size(min = 8, message = "Password must be at least 8 characters")
    private String password;
    
    @NotNull(message = "Phone is required")
    @Pattern(regexp = "^[0-9]{10}$")
    private String phone;
}
```

### 11.4 Data Protection

1. **Encryption**
   - Sensitive fields encrypted in database (future)
   - HTTPS for all API calls (production)
   - Database credentials in environment variables

2. **SQL Injection Prevention**
   - JPA/Hibernate parameterized queries
   - Input validation and sanitization
   - PreparedStatements

3. **CORS Configuration**
   ```java
   @Configuration
   public class CorsConfig {
       @Bean
       public WebMvcConfigurer corsConfigurer() {
           return new WebMvcConfigurer() {
               @Override
               public void addCorsMappings(CorsRegistry registry) {
                   registry.addMapping("/api/**")
                       .allowedOrigins("http://localhost:4200")
                       .allowedMethods("GET", "POST", "PUT", "DELETE")
                       .allowCredentials(true)
                       .maxAge(3600);
               }
           };
       }
   }
   ```

### 11.5 Security Best Practices Implemented

1. **No sensitive data in logs**
2. **Error messages don't reveal system details**
3. **Rate limiting (future implementation)**
4. **Account lockout after failed attempts (future)**
5. **Audit logging for admin actions**
6. **Regular security updates**
7. **Input sanitization**
8. **Parameterized queries**

---

## 12. Testing & Quality Assurance

### 12.1 Testing Strategy

#### Unit Testing
- Service layer testing with Mockito
- Repository testing
- Utility function testing
- Coverage target: 70%+

#### Integration Testing
- API endpoint testing
- Database integration tests
- Service-to-service communication

#### End-to-End Testing
- User flows (login, bill payment, loan application)
- Admin workflows
- Error handling scenarios

### 12.2 Test Coverage

| Component | Test Type | Status |
|-----------|-----------|--------|
| AuthService | Unit + Integration | ✅ Complete |
| AccountService | Unit + Integration | ✅ Complete |
| LoanService | Unit + Integration | ✅ Complete |
| BillService | Unit + Integration | ✅ Complete |
| ValidationRules | Unit | ✅ Complete |
| Controllers | Integration | ✅ Complete |
| Frontend Components | Unit (Jasmine) | ✅ In Progress |

### 12.3 Quality Checks

1. **Code Quality**
   - SonarQube analysis
   - PMD for code smells
   - CheckStyle for coding standards
   - Coverage analysis

2. **Performance Testing**
   - Load testing with JMeter
   - Database query optimization
   - API response time benchmarks
   - Frontend performance metrics

3. **Security Testing**
   - OWASP Top 10 compliance
   - SQL injection testing
   - XSS testing
   - CSRF protection verification
   - Authentication/authorization testing

4. **Bug Reporting**
   - Defect tracking system
   - Severity classification
   - Root cause analysis
   - Resolution tracking

### 12.4 Testing Tools

| Tool | Purpose |
|------|---------|
| JUnit 5 | Unit testing framework |
| Mockito | Mocking objects |
| Spring Boot Test | Integration testing |
| Postman | API testing |
| Jasmine | Frontend unit testing |
| Karma | Test runner for Angular |
| SonarQube | Code quality analysis |
| JMeter | Performance testing |

---

## 13. Challenges & Solutions

### 13.1 Role-Based Access Control Inconsistency

**Challenge:**
Inconsistent authorization between frontend and backend routes. Users could sometimes access routes they shouldn't have permission for, especially when the frontend route guard logic didn't align with backend @PreAuthorize annotations.

**Root Cause:**
- Route guards and controllers not synchronized
- Missing validation on some endpoints
- Token payload not properly validated

**Solution Implemented:**
```java
// Backend: Proper authorization on all endpoints
@PreAuthorize("hasRole('USER')")
@GetMapping("/api/accounts")
public ResponseEntity getMyAccounts() {
    // Get authenticated user from security context
    String username = SecurityContextHolder
        .getContext().getAuthentication().getName();
    return ResponseEntity.ok(accountService.getUserAccounts(username));
}

// Frontend: Route guard implementation
@Injectable()
export class AuthGuard implements CanActivate {
  canActivate(route: ActivatedRouteSnapshot): boolean {
    const token = this.authService.getToken();
    const role = this.authService.getUserRole();
    
    if (route.data['role'] && 
        route.data['role'] !== role) {
      this.router.navigate(['/dashboard']);
      return false;
    }
    return true;
  }
}
```

**Outcome:**
- Synchronized frontend-backend authorization
- All endpoints properly secured
- Consistent access control across application

---

### 13.2 Loan Workflow State Transition Issues

**Challenge:**
Loan applications failed in certain scenarios:
- User could apply multiple times for same product
- State transitions (Applied → Approved → Disbursed) weren't properly validated
- Loan could be approved and then updated to pending state

**Root Cause:**
- Missing business logic validations
- Incomplete state machine implementation
- Race conditions in concurrent requests

**Solution Implemented:**
```java
@Service
public class LoanService {
    public LoanDTO applyForLoan(LoanApplicationDTO request) {
        // Validate: Only one active application per product
        Optional<Loan> existingLoan = loanRepository
            .findByUserIdAndProductIdAndStatusNot(
                userId, 
                request.getProductId(), 
                LoanStatus.REJECTED
            );
        
        if (existingLoan.isPresent()) {
            throw new BusinessException(
                "You already have an active application for this product"
            );
        }
        
        // Create new loan
        Loan loan = new Loan();
        loan.setStatus(LoanStatus.APPLIED);
        return loanRepository.save(loan);
    }
    
    public LoanDTO approveLoan(Long loanId, BigDecimal approvedAmount) {
        Loan loan = loanRepository.findById(loanId)
            .orElseThrow(() -> new ResourceNotFoundException());
        
        // Validate: Can only approve APPLIED loans
        if (loan.getStatus() != LoanStatus.APPLIED) {
            throw new BusinessException(
                "Only APPLIED loans can be approved"
            );
        }
        
        loan.setStatus(LoanStatus.APPROVED);
        loan.setApprovedAmount(approvedAmount);
        return loanRepository.save(loan);
    }
}
```

**Outcome:**
- Proper state machine validation
- Prevented duplicate applications
- Ensured valid state transitions

---

### 13.3 Frontend-Backend Response Mismatch

**Challenge:**
API responses had inconsistent structure:
- Some endpoints returned data, others returned message
- Date formats varied
- Error responses weren't standardized
- This caused UI binding issues

**Root Cause:**
- No standardized response format defined
- Different controllers implemented responses differently
- Frontend assumed certain structure

**Solution Implemented:**
```java
// Standard response wrapper
public class ApiResponse<T> {
    private boolean success;
    private String message;
    private T data;
    private String errorCode;
    private LocalDateTime timestamp;
    
    // Constructors and getters
}

// Standardized controller responses
@RestController
@RequestMapping("/api/accounts")
public class AccountController {
    @GetMapping
    public ResponseEntity<ApiResponse<List<AccountDTO>>> getAccounts() {
        List<AccountDTO> accounts = accountService.getUserAccounts();
        return ResponseEntity.ok(
            new ApiResponse<>(true, "Accounts retrieved", accounts)
        );
    }
    
    @PostMapping
    public ResponseEntity<ApiResponse<AccountDTO>> createAccount(
            @RequestBody AccountCreateDTO request) {
        AccountDTO account = accountService.createAccount(request);
        return ResponseEntity.status(HttpStatus.CREATED)
            .body(new ApiResponse<>(true, "Account created", account));
    }
}

// Frontend standardized handling
export class ApiService {
  handleResponse<T>(response: ApiResponse<T>): T {
    if (!response.success) {
      throw new Error(response.errorCode);
    }
    return response.data;
  }
}
```

**Outcome:**
- Consistent API response format
- Simplified frontend handling
- Clear error communication

---

### 13.4 Authentication Token Issues

**Challenge:**
- Tokens stored in localStorage were vulnerable to XSS attacks
- Token refresh mechanism wasn't implemented
- Session expiry wasn't handled gracefully
- Logout didn't clear data properly

**Root Cause:**
- Simple token implementation without refresh logic
- XSS protection not implemented
- Session management incomplete

**Solution Implemented:**
```java
// Backend: Token refresh endpoint
@PostMapping("/api/auth/refresh-token")
public ResponseEntity<TokenResponse> refreshToken(
        @RequestHeader("Authorization") String token) {
    String newToken = jwtTokenProvider.refreshToken(token);
    return ResponseEntity.ok(new TokenResponse(newToken));
}

// Frontend: Interceptor with refresh logic
@Injectable()
export class JwtInterceptor implements HttpInterceptor {
  constructor(private authService: AuthService) {}
  
  intercept(req: HttpRequest<any>, next: HttpHandler): Observable<HttpEvent<any>> {
    const token = this.authService.getToken();
    
    if (token) {
      req = req.clone({
        setHeaders: {
          Authorization: `Bearer ${token}`
        }
      });
    }
    
    return next.handle(req).pipe(
      catchError(error => {
        if (error.status === 401) {
          // Token expired, try refresh
          return this.authService.refreshToken()
            .pipe(
              switchMap(response => {
                const newToken = response.token;
                this.authService.setToken(newToken);
                
                // Retry original request
                req = req.clone({
                  setHeaders: {
                    Authorization: `Bearer ${newToken}`
                  }
                });
                return next.handle(req);
              }),
              catchError(() => {
                this.authService.logout();
                return throwError(error);
              })
            );
        }
        return throwError(error);
      })
    );
  }
}

// Frontend: Proper logout
logout() {
  localStorage.removeItem('token');
  localStorage.removeItem('userId');
  sessionStorage.clear();
  this.router.navigate(['/login']);
}
```

**Outcome:**
- Implemented token refresh mechanism
- Automatic session renewal
- Graceful timeout handling
- Proper cleanup on logout

---

### 13.5 Database Query Performance

**Challenge:**
Some queries were slow:
- N+1 query problems in loan listing
- Missing database indexes
- Complex joins not optimized

**Solution Implemented:**
```java
// Before: N+1 queries
@Query("SELECT l FROM Loan l WHERE l.userId = :userId")
List<Loan> findByUserId(@Param("userId") Long userId);

// After: Eager loading with JOIN FETCH
@Query("SELECT DISTINCT l FROM Loan l " +
       "LEFT JOIN FETCH l.product p " +
       "LEFT JOIN FETCH l.documents d " +
       "WHERE l.userId = :userId")
List<Loan> findByUserId(@Param("userId") Long userId);

// Added indexes in database
CREATE INDEX idx_loan_user_status ON loans(user_id, status);
CREATE INDEX idx_transaction_account_date ON transactions(account_id, created_at);
CREATE INDEX idx_bill_user_status ON bills(user_id, status);

// Query optimization in service
@Transactional(readOnly = true)
public Page<LoanDTO> getUserLoans(Long userId, Pageable pageable) {
    return loanRepository.findByUserId(userId, pageable)
        .map(LoanDTO::fromEntity);
}
```

**Outcome:**
- Reduced query count significantly
- Improved API response times
- Better database performance

---

## 14. Future Enhancements

### 14.1 Functional Enhancements

1. **Real-Time Notifications**
   - Bill due date reminders
   - Loan application status updates
   - Large transaction alerts
   - Account activity notifications
   - Implementation: WebSocket + Push notifications

2. **Advanced Analytics**
   - Predictive spending analysis
   - ML-based recommendations
   - Anomaly detection
   - Financial health score
   - Implementation: Machine learning models

3. **Mobile Application**
   - Native iOS and Android apps
   - Offline capabilities
   - Biometric authentication
   - Push notifications
   - Implementation: React Native or Flutter

4. **Payment Gateway Integration**
   - Third-party payment processor integration
   - Multiple payment methods
   - Invoice generation
   - Payment automation
   - Implementation: Razorpay, Stripe, PayPal

### 14.2 Security Enhancements

1. **Two-Factor Authentication (2FA)**
   - SMS-based OTP
   - Email verification
   - Authenticator app support
   - Backup codes

2. **Fraud Detection**
   - Machine learning models
   - Anomaly detection
   - Transaction risk scoring
   - Real-time blocking

3. **Advanced Encryption**
   - End-to-end encryption
   - Field-level encryption for sensitive data
   - Secure key management
   - Tokenization

4. **Compliance & Audit**
   - PCI DSS compliance
   - GDPR compliance
   - Detailed audit logs
   - Regulatory reporting

### 14.3 Infrastructure Enhancements

1. **Cloud Deployment**
   - AWS/Azure/GCP deployment
   - Docker containerization
   - Kubernetes orchestration
   - Scalable infrastructure
   - Implementation: Docker + K8s

2. **CI/CD Pipeline**
   - Automated testing
   - Continuous integration
   - Automated deployment
   - Blue-green deployment
   - Implementation: Jenkins, GitLab CI, GitHub Actions

3. **Monitoring & Logging**
   - ELK stack implementation
   - Application performance monitoring
   - Error tracking
   - Log aggregation
   - Implementation: ELK, New Relic, Datadog

4. **Database Scaling**
   - Database replication
   - Read replicas
   - Caching layer (Redis)
   - Database sharding
   - Implementation: Redis, Master-slave replication

### 14.4 User Experience Enhancements

1. **Dark Mode**
   - System preference detection
   - Theme toggle
   - Persistent user preference
   - Optimized colors

2. **Internationalization (i18n)**
   - Multiple language support
   - Localization
   - Currency conversion
   - Locale-specific formatting

3. **Accessibility Improvements**
   - Screen reader optimization
   - High contrast mode
   - Keyboard navigation
   - WCAG 2.1 AA compliance

4. **Progressive Web App (PWA)**
   - Offline functionality
   - Service workers
   - App-like experience
   - Installation capability

### 14.5 Business Features

1. **Investment Portal**
   - Mutual fund recommendations
   - Stock trading
   - Investment tracking
   - Portfolio management

2. **Insurance Services**
   - Insurance product offerings
   - Policy management
   - Claims processing
   - Premium payment

3. **Business Accounts**
   - Corporate banking
   - Multi-user access
   - Advanced reporting
   - Bulk operations

4. **API for Third Parties**
   - Open banking APIs
   - Partner integration
   - Developer portal
   - API marketplace

---

## 15. Conclusion

### 15.1 Project Summary

Neo Bank represents a comprehensive, production-grade digital banking application that successfully integrates modern web technologies with banking domain requirements. The application demonstrates:

1. **Technical Excellence**
   - Clean, layered architecture
   - Secure authentication and authorization
   - Comprehensive API design
   - Database optimization
   - Full-stack implementation

2. **Business Value**
   - Centralized banking services
   - User-friendly interface
   - Administrative controls
   - Scalable platform
   - Foundation for future features

3. **Engineering Practices**
   - Robust error handling
   - Extensive testing
   - Security-first approach
   - Code maintainability
   - Documentation

### 15.2 Key Achievements

✅ Complete user registration and authentication system
✅ Secure JWT-based session management
✅ Full account and transaction management
✅ Bill payment functionality
✅ Comprehensive loan application workflow
✅ Budget and expense tracking
✅ Financial insights and analytics
✅ Admin dashboard with loan product management
✅ Role-based access control
✅ RESTful API architecture
✅ Responsive UI design
✅ Comprehensive testing coverage
✅ Security implementation

### 15.3 Technical Highlights

- **Frontend**: Angular 17+ with TypeScript, responsive design
- **Backend**: Spring Boot 2.7+ with Spring Security
- **Database**: MySQL with optimized schemas
- **Security**: JWT authentication, BCrypt encryption, CORS
- **Architecture**: Three-tier layered architecture
- **API**: RESTful design with standardized responses
- **Quality**: Unit tests, integration tests, security validation

### 15.4 Lessons Learned

1. **Role-Based Access Control** requires synchronized implementation across frontend and backend
2. **State Machine Validation** is crucial for complex workflows like loan applications
3. **API Response Standardization** simplifies frontend integration
4. **Token Management** needs refresh mechanisms for better UX
5. **Database Optimization** with proper indexes and eager loading improves performance significantly

### 15.5 Recommendations

**Immediate Priority:**
- Deploy to production infrastructure
- Implement 2FA for enhanced security
- Add real-time notifications
- Set up monitoring and logging

**Short Term (1-3 months):**
- Mobile app development
- Payment gateway integration
- Advanced analytics
- CI/CD pipeline setup

**Long Term (3-6 months):**
- Cloud migration
- Fraud detection system
- Investment features
- API for third parties

### 15.6 Final Thoughts

Neo Bank successfully demonstrates a modern, secure, and scalable digital banking platform. The project showcases practical implementation of full-stack development, security best practices, and real-world problem-solving. It serves as a strong foundation for a production-grade banking application and provides valuable insights for future enhancements.

The combination of Angular frontend with Spring Boot backend, secured with JWT authentication and supported by MySQL database, creates a robust platform that can handle complex banking operations. The modular architecture allows for easy expansion and integration of new features as business requirements evolve.

---

## Appendix

### Development Environment Setup

```bash
# Frontend setup
cd frontend/bank
npm install
npm start  # Starts on http://localhost:4200

# Backend setup
cd banking
mvn clean install
mvn spring-boot:run  # Starts on http://localhost:8080

# Database setup
mysql -u root -p < database-schema.sql
```

### Important Files & Locations

```
Frontend:
- src/app/auth/ - Authentication components
- src/app/account/ - Account management
- src/app/loans/ - Loan components
- src/app/admin/ - Admin dashboard

Backend:
- src/main/java/com/bank/controller/ - REST controllers
- src/main/java/com/bank/service/ - Business logic
- src/main/java/com/bank/repository/ - Data access
- src/main/java/com/bank/entity/ - Domain models
- src/main/java/com/bank/security/ - Security config

Database:
- database-schema.sql - Complete schema
- database-sample-data.sql - Test data
```

---

**Document Version**: 1.0
**Last Updated**: January 2024
**Author**: NEO BANK Development Team
**Status**: Complete

---

END OF DOCUMENTATION

