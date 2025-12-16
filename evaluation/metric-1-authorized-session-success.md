# Metric 1: Authorized Session Success Rate

## Objective
To measure the percentage of legitimate and authorized SSM session attempts that were successfully established.

---

## Test Scenario
Authorized users attempted to access EC2 instances using AWS Systems Manager Session Manager with the correct IAM role assumption.

---

## Test Case 1: HR Role Access to Instance A

**User:** HR user  
**Assumed Role:** ZTA-HR-ConfidentialAccess-Role  
**Target:** Instance A  
**Access Method:** SSM Session Manager  

**Expected Result:**  
SSM session is successfully established.

**Actual Result:**  
SSM session was successfully established.

**Outcome:** Pass

---

## Test Case 2: Admin Role Access to Instance B

**User:** Admin user  
**Assumed Role:** EC2-Admin-Role  
**Target:** Instance B  
**Access Method:** SSM Session Manager  

**Expected Result:**  
SSM session is successfully established.

**Actual Result:**  
SSM session was successfully established.

**Outcome:** Pass

---

## Result Summary
Most authorized session attempts were successful, contributing to the authorized session success rate of 93.3% reported in Chapter 4.
