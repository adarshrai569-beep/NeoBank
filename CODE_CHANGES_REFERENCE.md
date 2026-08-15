# Code Changes Reference - Before & After

## Backend Change 1: LoanApplicationService.java

### BEFORE:
```java
public interface LoanApplicationService {
    LoanApplicationResponseDTO apply(LoanApplicationRequestDTO request);
    List<LoanApplicationResponseDTO> getMyApplications();
    LoanApplicationResponseDTO approve(Long id);
    LoanApplicationResponseDTO reject(Long id);
    LoanEMIResponseDTO calculateEMI(Long applicationId);
}
```

### AFTER:
```java
public interface LoanApplicationService {
    LoanApplicationResponseDTO apply(LoanApplicationRequestDTO request);
    List<LoanApplicationResponseDTO> getMyApplications();
    
    // ✅ NEW METHOD
    List<LoanApplicationResponseDTO> getAllApplications();
    
    LoanApplicationResponseDTO approve(Long id);
    LoanApplicationResponseDTO reject(Long id);
    LoanEMIResponseDTO calculateEMI(Long applicationId);
}
```

---

## Backend Change 2: LoanApplicationServiceImpl.java

### ADDED Method:
```java
@Override
public List<LoanApplicationResponseDTO> getAllApplications() {
    checkAdmin();  // Verify admin role
    return applicationRepo.findAll()
            .stream()
            .map(this::mapToDTO)
            .collect(Collectors.toList());
}
```

### UPDATED mapToDTO Method:

**BEFORE:**
```java
private LoanApplicationResponseDTO mapToDTO(LoanApplication app) {
    return LoanApplicationResponseDTO.builder()
            .applicationId(app.getId())
            .productName(app.getLoanProduct().getProductName())
            .amount(app.getAmount())
            .tenure(app.getTenure())
            .status(app.getStatus().name())
            .build();
}
```

**AFTER:**
```java
private LoanApplicationResponseDTO mapToDTO(LoanApplication app) {
    return LoanApplicationResponseDTO.builder()
            .applicationId(app.getId())
            .userId(app.getUserId())  // ✅ NEW
            .productName(app.getLoanProduct().getProductName())
            .amount(app.getAmount())
            .tenure(app.getTenure())
            .status(app.getStatus().name())
            .build();
}
```

---

## Backend Change 3: LoanApplicationController.java

### IMPORT CHANGE:
**BEFORE:**
```java
import org.springframework.web.bind.annotation.*;
```

**AFTER:**
```java
import org.springframework.security.access.prepost.PreAuthorize;
import org.springframework.web.bind.annotation.*;
```

### ADDED Endpoint:
```java
@GetMapping("/admin/applications")
@PreAuthorize("hasAuthority('ROLE_ADMIN')")
public ResponseEntity<?> getAllApplications() {
    return ResponseEntity.ok(loanApplicationService.getAllApplications());
}
```

**Full URL:** `GET http://localhost:8080/api/loans/admin/applications`

---

## Backend Change 4: LoanApplicationResponseDTO.java

### BEFORE:
```java
@Getter
@Builder
public class LoanApplicationResponseDTO {
    private Long applicationId;
    private String productName;
    private BigDecimal amount;
    private Integer tenure;
    private String status;
}
```

### AFTER:
```java
@Getter
@Builder
public class LoanApplicationResponseDTO {
    private Long applicationId;
    private Long userId;  // ✅ NEW - Shows who applied
    private String productName;
    private BigDecimal amount;
    private Integer tenure;
    private String status;
}
```

---

## Frontend Change: admin.component.html

### ADDED Section (append before final closing tags):

```html
  <div *ngIf="activeTab === 'loans'">
    <h3>Loan Applications</h3>
    <table>
      <thead>
        <tr>
          <th>App ID</th>
          <th>User ID</th>
          <th>Product</th>
          <th>Amount</th>
          <th>Tenure</th>
          <th>Status</th>
          <th>Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr *ngFor="let app of loanApplications">
          <td>{{ app.applicationId }}</td>
          <td>{{ app.userId }}</td>
          <td>{{ app.productName }}</td>
          <td>₹{{ app.amount }}</td>
          <td>{{ app.tenure }} months</td>
          <td>{{ app.status }}</td>
          <td>
            <button *ngIf="app.status === 'PENDING'" (click)="approveLoanApp(app.applicationId)">Approve</button>
            <button *ngIf="app.status === 'PENDING'" (click)="rejectLoanApp(app.applicationId)">Reject</button>
            <span *ngIf="app.status !== 'PENDING'">No actions</span>
          </td>
        </tr>
        <tr *ngIf="loanApplications.length === 0">
          <td colspan="7">No loan applications found.</td>
        </tr>
      </tbody>
    </table>
  </div>
```

---

## Component Code Already Exists

**admin.cmponent.ts** - No changes needed! Already has:

```typescript
loanApplications: any[] = [];  // ✅ Already exists
activeTab: 'users' | 'loans' = 'users';  // ✅ Already supports loans tab

loadLoanApplications() {
  this.loanService.getAllApplications()
    .subscribe((data: any) => this.loanApplications = data || []);
}

approveLoanApp(appId: number) {
  this.loanService.approveLoan(appId)
    .subscribe({
      next: () => { alert('✅ Loan approved'); this.loadLoanApplications(); },
      error: (err) => alert('Failed to approve')
    });
}

rejectLoanApp(appId: number) {
  this.loanService.rejectLoan(appId)
    .subscribe({
      next: () => { alert('✅ Loan rejected'); this.loadLoanApplications(); },
      error: (err) => alert('Failed to reject')
    });
}
```

---

## Service Code Already Exists

**loan.service.ts** - No changes needed! Already has:

```typescript
getAllApplications() {
  return this.http.get(`${this.baseUrl}/admin/applications`);
}

approveLoan(id: number) {
  return this.http.put(`${this.baseUrl}/${id}/approve`, {});
}

rejectLoan(id: number) {
  return this.http.put(`${this.baseUrl}/${id}/reject`, {});
}
```

---

## Summary of Changes

### Total Files Modified: 5
- **Backend:** 4 Java files
- **Frontend:** 1 HTML file

### Changes Type:
- ✅ 1 new service interface method
- ✅ 1 new service implementation method
- ✅ 1 new REST endpoint
- ✅ 1 new DTO field
- ✅ 1 UI table section

### Lines Added:
- **Backend:** ~25 lines
- **Frontend:** ~35 lines

### Breaking Changes: NONE
- ✅ All existing APIs remain unchanged
- ✅ Fully backward compatible
- ✅ Only adds new functionality
