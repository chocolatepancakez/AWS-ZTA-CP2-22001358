# Metric 4: Internet Egress Block Rate

## Objective
To verify that EC2 instances are unable to access the public internet due to the absence of Internet and NAT gateways.

---

## Test Scenario
Outbound network requests were initiated from EC2 instances to public IP addresses.

---

## Test Case 1: ICMP Ping to Public IP

**Target:** 8.8.8.8  
**Expected Result:**  
Outbound traffic is blocked.

**Actual Result:**  
100% packet loss observed.

**Outcome:** Pass

---

## Test Case 2: HTTP Request to Public Endpoint

**Target:** Public HTTP endpoint  
**Expected Result:**  
Connection attempt fails.

**Actual Result:**  
Request timed out.

**Outcome:** Pass

---

## Result Summary
All outbound internet access attempts failed, confirming a 100% internet egress block rate.
