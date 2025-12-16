# Metric 2: Unauthorized Identity Access Denial Rate

## Objective
To measure the percentage of access attempts made by unauthorized identities that were correctly denied.

---

## Test Case 1: HR Role Attempting Access to Instance B

**User:** HR user  
**Assumed Role:** ZTA-HR-ConfidentialAccess-Role  
**Target:** Instance B  

**Expected Result:**  
Access is denied.

**Actual Result:**  
Access was denied.

**Outcome:** Pass

---

## Test Case 2: Read-Only Role Attempting SSM Session

**User:** Read-only user  
**Assumed Role:** ZTA-ReadOnly-Role  
**Target:** Any EC2 instance  

**Expected Result:**  
SSM session initiation is denied.

**Actual Result:**  
Access was denied.

**Outcome:** Pass

---

## Result Summary
All unauthorized identity-based access attempts were denied, resulting in a 100% unauthorized access denial rate.
