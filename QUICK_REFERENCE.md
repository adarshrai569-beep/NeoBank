# Quick Reference Guide - Commands & URLs

## All-in-One Setup Guide

### Prerequisites Check
```bash
# Check Java installed
java -version
# Expected: Java 17+ (openjdk)

# Check Node installed
node -v npm -v
# Expected: v18+ and npm 8+

# Check Maven installed (in STS)
# Path: c:\Users\<user>\.m2\repository
```

---

## Backend Setup (STS)

### Quick Build Command
```
Right-click project → Maven → Clean
Right-click project → Maven → Update Project (Force Update)
Right-click project → Maven → Run As → Maven Build
Goal: clean install
```

### Quick Start Command
```
Right-click BankingApplication.java → Run As → Java Application
```

### Verify Running
```
Open: http://localhost:8080
Expected: Spring Boot is running (JSON response or 404 OK)
```

---

## Frontend Setup (Terminal)

### Quick Setup
```bash
cd "c:\Users\aryan23.TRN\Downloads\NEO BANK\frontend\bank"
npm install
npm start
```

### Verify Running
```
Open: http://localhost:4200
Expected: Login page loads
```

---

## All API Endpoints

### Public Endpoints (No Auth)
```
GET  /api/loans/products                    → List available loan products
```

### Customer Endpoints (Authenticated)
```
POST   /api/loans/apply                     → Apply for loan
GET    /api/loans/my-applications           → View own applications
GET    /api/loans/{id}/emi                  → Calculate EMI
```

### Admin Endpoints (Admin Role Required)
```
GET    /api/loans/admin/applications        → View all applications ✅ NEW
POST   /api/loans/products                  → Create new product
PUT    /api/loans/{id}/approve              → Approve loan ✅ USED NOW
PUT    /api/loans/{id}/reject               → Reject loan ✅ USED NOW
```

---

## Database Queries

### Check Loan Products
```sql
SELECT id, product_name, min_amount, max_amount, annual_interest_rate 
FROM loan_products;
```

### Check Loan Applications
```sql
SELECT id, user_id, loan_product_id, amount, tenure, status, created_at 
FROM loan_applications 
ORDER BY created_at DESC;
```

### Check Pending Applications
```sql
SELECT id, user_id, (SELECT product_name FROM loan_products WHERE id=lp.loan_product_id) as product,
       amount, tenure, status 
FROM loan_applications la
JOIN loan_products lp ON la.loan_product_id = lp.id
WHERE status = 'PENDING';
```

### Update Application Status (Manual Fix - if needed)
```sql
UPDATE loan_applications 
SET status = 'APPROVED' 
WHERE id = 1;
```

---

## File Locations

### Backend Files
```
Banking Project Root:
c:\Users\aryan23.TRN\Downloads\NEO BANK\banking\

Modified Files:
- src/main/java/com/bank/service/LoanApplicationService.java
- src/main/java/com/bank/service/impl/LoanApplicationServiceImpl.java
- src/main/java/com/bank/controller/LoanApplicationController.java
- src/main/java/com/bank/dto/LoanApplicationResponseDTO.java
```

### Frontend Files
```
Frontend Root:
c:\Users\aryan23.TRN\Downloads\NEO BANK\frontend\bank\

Modified Files:
- src/app/admin/admin.component.html
```

### Config Files
```
Backend Config:
- pom.xml (Maven dependencies)
- application.properties (Server config)

Frontend Config:
- package.json (npm dependencies)
- angular.json (Angular config)
```

---

## Troubleshooting Commands

### Backend Won't Start
```bash
# Check if port 8080 is in use
netstat -ano | findstr :8080

# If port busy, kill process or use different port
# In application.properties: server.port=8081

# Clean rebuild
cd banking
mvn clean install -DskipTests

# Run with debug
mvn spring-boot:run -Dspring-boot.run.arguments="--debug"
```

### Frontend Won't Start
```bash
# Clear cache
npm cache clean --force

# Reinstall dependencies
rm -r node_modules
npm install

# Build fresh
ng serve --poll 2000  # Increase if slow

# Try specific port
ng serve --port 4300
```

### Database Issues
```bash
# Check database connection in application.properties
# Format: spring.datasource.url=jdbc:mysql://localhost:3306/banking

# Verify MySQL is running
# If needed: net start MySQL80 (Windows)

# Check user permissions
# User: root, Password: (configured in properties)
```

### CORS Issues
```
# If frontend can't reach backend:
# 1. Check SecurityConfig.java - CORS might be blocked
# 2. Verify backend is running on correct port
# 3. Check network tab in DevTools (F12)
# 4. Look for error: "Access to XMLHttpRequest has been blocked by CORS policy"
```

---

## Testing Commands

### Test Backend API with Curl
```bash
# Get all loan applications (replace TOKEN with actual token)
curl -H "Authorization: Bearer TOKEN" \
     http://localhost:8080/api/loans/admin/applications

# Approve loan
curl -X PUT -H "Authorization: Bearer TOKEN" \
     http://localhost:8080/api/loans/1/approve

# Reject loan
curl -X PUT -H "Authorization: Bearer TOKEN" \
     http://localhost:8080/api/loans/1/reject

# Get loan products
curl http://localhost:8080/api/loans/products
```

### Test Frontend Locally
```bash
# Run tests
ng test

# Build for production
ng build --prod

# Check bundle size
ng build --prod --stats-json
webpack-bundle-analyzer dist/bank/stats.json
```

---

## Environment Variables

### Backend (.env or application.properties)
```properties
# Server
server.port=8080
server.servlet.context-path=/

# Database
spring.datasource.url=jdbc:mysql://localhost:3306/banking
spring.datasource.username=root
spring.datasource.password=yourpassword

# JWT Secret (if using JWT)
jwt.secret.key=your-secret-key-here
jwt.expiration.ms=86400000

# Logging
logging.level.root=INFO
logging.level.com.bank=DEBUG
```

### Frontend (environment.ts)
```typescript
export const environment = {
  production: false,
  apiUrl: 'http://localhost:8080/api'
};
```

---

## Performance Monitoring

### Check Backend Performance
```
Monitor in STS:
- Heap Memory Usage
- CPU Usage
- Thread Count
- Request Response Times

If slow:
- Increase heap: -Xmx1024m in VM options
- Add indexes to database tables
- Optimize queries
```

### Check Frontend Performance
```
In Browser DevTools (F12):
1. Performance tab → Record → Do action → Stop
2. Network tab → Check request times
3. Console tab → Check for warnings
4. Memory tab → Check for leaks

Expected times:
- Page load: < 3 seconds
- API call: < 1 second
- Approve/Reject: < 2 seconds
```

---

## Logs Location

### Backend Logs
```
STS Console Output:
- Real-time logs displayed
- Contains startup messages
- Shows SQL queries (if debug enabled)
- Shows API calls and responses
```

### Frontend Logs
```
Browser Console (F12):
- Angular compile info
- HTTP request/response logs
- Component lifecycle logs
- Errors and warnings
```

---

## Common Credentials (for testing)

### Admin Account
```
Email: admin@neobank.com
Password: Admin@123
Role: ADMIN
```

### Customer Account
```
Email: customer@example.com
Password: Customer@123
Role: CUSTOMER
```

### Create New Account
- Use Registration page
- Fill form with unique email
- Password should meet requirements
- Account pending admin approval (approve from admin panel)

---

## Key Endpoints for Admin Workflow

### 1. Get Pending Applications
```
GET http://localhost:8080/api/loans/admin/applications
Header: Authorization: Bearer <admin-token>
Response: List of all applications (pending, approved, rejected)
```

### 2. Approve Application
```
PUT http://localhost:8080/api/loans/1/approve
Header: Authorization: Bearer <admin-token>
Body: {} (empty)
Response: Updated application with status = APPROVED
```

### 3. Reject Application
```
PUT http://localhost:8080/api/loans/1/reject
Header: Authorization: Bearer <admin-token>
Body: {} (empty)
Response: Updated application with status = REJECTED
```

---

## Deployment Checklist Summary

- [ ] Backend compiles: `mvn clean install`
- [ ] Backend runs: `Spring Boot started`
- [ ] Database connected: No errors in logs
- [ ] Frontend installs: `npm install` completes
- [ ] Frontend runs: `ng serve` completes
- [ ] Can login: Both customer and admin
- [ ] Can apply: Create test application
- [ ] Can view: Admin sees applications
- [ ] Can approve: Status changes to APPROVED
- [ ] Can reject: Status changes to REJECTED

---

## Quick Debug Tips

### If Table is Empty
```
1. Did you create loan products? (Admin → Loan Products)
2. Did you apply for loans? (Loans → Apply)
3. Are you logged in as admin?
4. Check backend logs for errors
5. Check browser console (F12) for errors
```

### If Buttons Don't Work
```
1. Is backend running?
2. Check network tab (F12) for failed requests
3. Check response status (should be 200)
4. Verify authorization token is valid
5. Check backend logs for exception
```

### If Status Doesn't Update
```
1. Wait for page refresh (auto-refresh after action)
2. Manually refresh page (F5)
3. Check database directly
4. Check backend logs
5. Restart both frontend and backend
```

---

## Support Resources

### Documentation Files Created
- `LOAN_FIX_SUMMARY.md` - Complete fix overview
- `CODE_CHANGES_REFERENCE.md` - Exact code changes
- `QUICKSTART.md` - Quick setup guide
- `ADMIN_UI_REFERENCE.md` - UI screenshots and behavior
- `VERIFICATION_CHECKLIST.md` - Testing checklist
- `EXPECTED_BEHAVIOR.md` - Before/after comparison
- `QUICK_REFERENCE.md` - This file (all commands)

### External Resources
- Spring Boot Docs: https://spring.io/projects/spring-boot
- Angular Docs: https://angular.io/docs
- MySQL Docs: https://dev.mysql.com/doc/
- Maven Guide: https://maven.apache.org/guides/

---

**Ready to deploy! All commands and references above. Good luck! 🚀**
