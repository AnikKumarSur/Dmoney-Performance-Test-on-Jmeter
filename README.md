# Performance and Functional Testing with JMeter

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
1.  5-minute load test.![image](![5min](https://github.com/user-attachments/assets/d5488f18-c428-49c3-a662-2326d8d6331a)
)
2. **Step 2:** 10-minute load test.
3. **Step 3:** 20-minute load test.


#### **Stress Test Steps:**
- Gradually increase users until the server bottleneck is identified.

#### **Test Reports:**
- `booking-api-test-report.xlsx`
  - **Load Test Report** (Excel Tab 1)
  - **Stress Test Report** (Excel Tab 2)
- Screenshots of test summaries and statistics are included in `README.md`

---

### **Dmoney API (Functional Testing)**
#### **Scenario:**
- 5 agents perform deposits for 10 customers.
- 5 customers send money to another 10 customers.
- 5 customers make payments to 2 merchants.

#### **Steps:**
1. Log in as an admin once and generate a token.
2. Create 3 threads:
   - Agent Deposits (Using `deposit.csv`)
   - Customer Money Transfers (Using `sendMoney.csv`)
   - Customer Payments (Using `payment.csv`)
3. Use a **Random Variable Controller** for dynamic transaction amounts.
4. Set up a **ramp-up time of 120 seconds** per thread.
5. Add assertions to ensure transactions are successful.

📌 **Note:** We are not performing performance testing for Dmoney API.

---

## **Running the Tests**
### **1. Booking API Performance Tests**
Run the test using JMeter in **non-GUI mode** for better performance:
```bash
jmeter -n -t booking.jmx -l results.jtl -e -o Report
```
This will generate an **HTML report** in the `Report` folder.

### **2. Dmoney API Functional Test**
```bash
jmeter -n -t dmoney.jmx -l dmoney.jtl -e -o dmoney-report
```
This will generate an **HTML report** in the `dmoney-report` folder.

---

## **Git Submission Process**
1. **Ensure your repo contains:**
   - `booking.jmx`
   - `dmoney.jmx`
   - `booking-api-test-report.xlsx`
   - `deposit.csv`, `sendMoney.csv`, `payment.csv`
2. **Exclude unnecessary files:**
   - Add `dmoney.jtl` and `Report` folders to `.gitignore`
3. **Push the repository to GitHub:**
   ```bash
   git add .
   git commit -m "Added JMeter test plans and reports"
   git push origin main
   ```
4. **Include screenshots in README.md:**
   - Add request summary and statistics from the HTML reports.

---

## **Screenshots**
### **Booking API Load Test Summary:**
![Load Test Summary](path/to/screenshot1.png)

### **Booking API Stress Test Summary:**
![Stress Test Summary](path/to/screenshot2.png)

### **Dmoney API Functional Test Summary:**
![Dmoney Test Summary](path/to/screenshot3.png)

---

## **Contributors**
- **Your Name** - [GitHub Profile](https://github.com/yourusername)
