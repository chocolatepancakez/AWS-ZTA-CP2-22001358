# Metric 3: MFA Condition Enforcement Rate

## Objective
To evaluate whether MFA conditions configured in IAM role trust policies were correctly enforced.

---

## Test Scenarios
Role assumption attempts were performed under different MFA conditions.

---

## Test Case 1: Role Assumption Without MFA

**Condition:** MFA not enabled  
**Expected Result:**  
Role assumption is denied.

**Actual Result:**  
Role assumption was denied.

**Outcome:** Pass

---

## Test Case 2: Role Assumption with Expired MFA

**Condition:** MFA age exceeded the set threshold  
**Expected Result:**  
Role assumption is denied.

**Actual Result:**  
Role assumption was denied.

**Outcome:** Pass

---

## Test Case 3: Role Assumption with Valid MFA

**Condition:** MFA present and within allowed time window  
**Expected Result:**  
Role assumption is allowed.

**Actual Result:**  
Role assumption was allowed.

**Outcome:** Pass

---

## Result Summary
All MFA conditions were correctly enforced, confirming effective MFA-based access control.
