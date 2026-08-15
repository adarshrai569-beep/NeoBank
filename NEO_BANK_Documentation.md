# NeoBank Platform Documentation

## Overview
NeoBank is a full-stack digital banking platform with a Spring Boot backend and an Angular frontend. It covers user onboarding, account management, transactions, budgets, bills, rewards, loan workflows, and Sprint 4 insights/admin controls.

## Architecture
- Frontend: Angular SPA (standalone components, route guards, Chart.js for analytics).
- Backend: Spring Boot REST API with Spring Security and JWT authentication.
- Database: MySQL (JPA/Hibernate), existing schema from prior sprints.

## Technology Stack
- Backend: Java 21, Spring Boot 4.x, Spring Data JPA, Spring Security, JWT (jjwt), Lombok.
- Frontend: Angular 17, Chart.js + ng2-charts.
- Build: Maven (backend), npm/Angular CLI (frontend).

## Repository Structure
- backend: `banking/`
  - `src/main/java/com/bank/controller` REST controllers
  - `src/main/java/com/bank/service` business logic
  - `src/main/java/com/bank/repository` data access
  - `src/main/java/com/bank/dto` API DTOs
- frontend: `frontend/bank/`
  - `src/app` components, services, routes
  - `src/styles.css` global theme

## Setup and Run
### Backend
- Build: `mvn clean install`
- Run: `mvn spring-boot:run`
- Base URL: `http://localhost:8080`

### Frontend
- Install: `npm install`
- Run: `npm start`
- Base URL: `http://localhost:4200`

## Authentication and Security
- JWT-based authentication using `Authorization: Bearer <token>`.
- Role-based access control with `ROLE_ADMIN` and `ROLE_CUSTOMER`.
- Admin endpoints are protected with `@PreAuthorize("hasRole('ADMIN')")`.
- Insights endpoint enforces JWT userId matches path userId (403 on mismatch).

## Frontend Routes
- `/login` Login screen.
- `/register` Registration screen.
- `/dashboard` Main user dashboard (AuthGuard).
- `/loans` Loan overview.
- `/loans/apply` Apply for a loan.
- `/loans/my-loans` User loan applications.
- `/loans/repayment-schedule/:loanAccountId` Repayment schedule.
- `/insights` Financial insights dashboard.
- `/admin` Admin control center (AdminAuthGuard).
- `/admin/loan-products` Admin loan product management.

## API Endpoints (Backend)
### Auth
- `POST /api/auth/register`
- `POST /api/auth/login`

### Accounts and Transactions
- `POST /api/accounts` create account
- `GET /api/accounts` list accounts
- `GET /api/accounts/{id}` get account
- `POST /api/accounts/{accountId}/transact` deposit/withdraw
- `POST /api/accounts/transfer` transfer between accounts
- `GET /api/accounts/{accountId}/transactions` transaction history

- `POST /api/transactions` create transaction
- `GET /api/transactions` transaction history

### Users
- `GET /api/users/me` get profile
- `PUT /api/users/profile` update profile fields
- `PUT /api/users/me` update profile (legacy)

### Budgets
- `POST /api/budgets` create budget
- `GET /api/budgets/{month}` get budget summary

### Bills
- `GET /api/bills` list bills
- `POST /api/bills` create bill
- `PATCH /api/bills/{id}/pay` pay bill

### Rewards
- `GET /api/rewards/{userId}` get rewards

### Loans
- `POST /api/loans/apply` apply for loan
- `GET /api/loans/my-applications` list user loan applications
- `GET /api/loans/admin/applications` admin list applications
- `PUT /api/loans/{id}/decision` admin approve/reject
- `GET /api/loans/{id}/emi` EMI calculation
- `GET /api/loans/my-accounts` loan accounts
- `GET /api/loans/{loanAccountId}/repayments` repayment schedule
- `PATCH /api/loans/{loanAccountId}/repayments/{repaymentId}/pay` mark repayment paid

### Loan Products
- `POST /api/loans/products` create product (admin)
- `GET /api/loans/products` list products
- `GET /api/loans/products/{id}` get product

### Sprint 4 Insights
- `GET /api/insights/{userId}` returns totalIncome, totalExpense, savings, trendSummary

### Sprint 4 Admin
- `GET /api/admin/dashboard` platform KPIs
- `GET /api/admin/pending-approvals` pending approvals
- `GET /api/admin/system-health` db status, sessions, uptime
- `GET /api/admin/users` admin user list
- `PATCH /api/admin/users/{id}/status` activate/deactivate
- `GET /api/admin/users/{id}/activity` recent transactions + logins
- Additional admin utilities:
  - `PUT /api/admin/users/{id}/status`
  - `PUT /api/admin/users/{id}/role`
  - `DELETE /api/admin/users/{id}`
  - `PUT /api/admin/users/{id}/approve`
  - `PUT /api/admin/accounts/{id}/freeze`
  - `PUT /api/admin/accounts/{id}/unfreeze`
  - `GET /api/admin/accounts`
  - `GET /api/admin/users/{id}/accounts`

## Sprint 4 Features (Insights + Admin Controls)
- Insights aggregation: income, expense, savings, 6-month trend summary.
- Admin dashboard metrics: users, active users, loans, pending approvals, total transactions, platform savings rate.
- Admin pending approvals list with module filter.
- User activity panel: recent transactions + login events.
- System health endpoint.
- Audit logging: admin write actions logged under the `AUDIT_LOG` logger.

## OpenAPI / Swagger
- UI: `http://localhost:8080/swagger-ui.html`
- JSON: `http://localhost:8080/v3/api-docs`
- Note: in secured office environments, access may return 403 unless backend is restarted after security changes.

## Testing
### Backend
- Unit tests exist for insights and admin dashboard logic.
- Run: `mvn test`

### Frontend
- Run: `ng test`
- E2E: not configured by default.

## Known Environment Notes
- Some environments block direct access to `/v3/api-docs`. If blocked, use a Maven-based OpenAPI export later.

## Document History
- Updated through Sprint 4 implementation (Insights + Admin Controls) as of 2026-06-05.
