# Dmoney Performance Testing on JMeter

## Project Overview
This repository contains JMeter test plans for performance and functional testing of two APIs:
1. **Booking API** (Performance Testing)
2. **Dmoney API** (Functional Testing)

---

## Prerequisites
- Install [Apache JMeter 17 LTS](https://jmeter.apache.org/download_jmeter.cgi)
- Install [java 17.0.12 2024-07-16 LTS](https://www.oracle.com/java/technologies/javase-downloads.html)
- Clone this repository using:
  ```bash
  git clone https://github.com/yourusername/repositoryname.git
  ```
- Place `deposit.csv`, `sendMoney.csv`, and `payment.csv` files in the root directory.

---

## File Structure
```
├── booking.jmx  # JMeter test plan for Booking API
├── dmoney.jmx   # JMeter test plan for Dmoney API
├── resources/
│   ├── deposit.csv
│   ├── sendMoney.csv
│   ├── payment.csv
├── booking-api-test-report.xlsx
├── .gitignore
├── README.md
```

---

## **Test Scenarios**
### **Booking API (Performance Testing)**
#### **Scenario:**
- 120,000 users over 12 hours log in, create a booking, and search for it.

#### **Load Test Steps:**
1. **Step 1:** 5-minute load test.
2. **Step 2:** 10-minute load test.
3. **Step 3:** 20-minute load test.

📌 **Gaussian Random Timer** (Deviation: 2000ms, Constant delay: 500ms)
#### **Load Test Summary**
1.  5-minute load test Summary Report.![5min](https://github.com/user-attachments/assets/e3ea5a21-df6d-4008-a3fd-0fa002242a31)
2.  10-minute load test Summary Report.![6min](https://github.com/user-attachments/assets/132035a4-361d-49ee-88db-f2051b8ca57e)
3.  20-minute load test Summary Report.![20min](https://github.com/user-attachments/assets/e2379f81-d775-41ec-91a3-62178175405d)




#### **Stress Test Steps:**
- Gradually increase users until the server bottleneck is identified.
1.  Stress Testing Html Report.![image](https://github.com/user-attachments/assets/2220d322-0788-4521-b0f1-4d826752ebf1)

2.  ![stress first](https://github.com/user-attachments/assets/891ba2a6-7340-40b4-a553-fc960e0e74f3)


#### **Test Reports:**
- [Load And Stress Report](https://docs.google.com/spreadsheets/d/1CI1PiXehG9sPqBYysJ4wEJBCzUpf7rC26YP0Vd9fqiQ/edit?usp=sharing)
  


---

### **Dmoney API (Functional Testing)**
## Scenario Overview

This test simulates various financial transactions in the Dmoney API using JMeter to evaluate performance under concurrent load.

## API Documentation
- **User:** [http://dmoney.roadtocareer.net/api-docs/user/](http://dmoney.roadtocareer.net/api-docs/user/)
- **Transactions:** [http://dmoney.roadtocareer.net/api-docs/transaction/](http://dmoney.roadtocareer.net/api-docs/transaction/)

## Test Scenario
- 5 agents perform deposits for 10 customers.
- 5 customers send money to another 10 customers.
- 5 customers make payments to 2 merchants.

## Implementation Steps

### Authentication
1. Log in as an admin and generate a token.
2. Use this token across all threads for secure transactions.

### Test Configuration
1. **Create 3 Thread Groups:**
   - Agent Transactions (Deposit)
   - Customer Transactions (Send Money)
   - Merchant Transactions (Payment)
2. **Use CSV Data Set Config for dynamic user data:**
   - `deposit.csv` → Agent & Customer account details
   - `sendMoney.csv` → Sender & Receiver customer details
   - `payment.csv` → Customer & Merchant details

## Functional Test Results
1.  Summary Report for dmoney.![dmonneyfirst](https://github.com/user-attachments/assets/a5824107-d833-4ecc-94b5-235406d75d55)

1.  Html Report for dmoney.![statics Report](https://github.com/user-attachments/assets/91db0291-39ce-4a1c-9dcc-a64d25826f11)


