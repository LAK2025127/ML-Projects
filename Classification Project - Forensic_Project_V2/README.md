# 🚨 Fraud Detection Project

## 📌 Overview
This project focuses on detecting **fraudulent transactions** within procurement expense reports.  
The goal is to **support accounting and audit teams** in identifying suspicious activities while minimizing false positives to ensure genuine transactions are not flagged unnecessarily.

We designed a **hybrid approach**:
- **Rule-based detection**: predefined conditions to flag high-risk transactions.
- **Machine Learning models**: trained on labeled data to capture subtle fraud patterns.

---

## 🗂 Project Structure & Steps
1. **Synthetic Dataset Creation**  
   - Generated using Python (`faker`, `numpy`, `random`).  
   - Included organizational hierarchy (departments, approvers, employees).  
   - Ensured realistic transaction timing (9 AM – 9 PM).  

2. **Fraud Definition & Risk Levels**  
   - Nine fraud types were defined (see tables below).  
   - Each fraud type was assigned a **risk score** and **potential implication**.

3. **Rule-based Flagging**  
   - Applied predefined conditions (e.g., duplicate invoices, suspicious keywords, late-night transactions).  
   - Multi-flagging allowed, meaning one transaction can trigger multiple fraud conditions.  
   - Risk levels assigned as:  
     - `0 = Low`  
     - `1 = Medium`  
     - `2 = High`  
     - `3+ = Critical`

4. **Machine Learning Models**  
   - Tested several models; **Decision Tree Classifier** performed best.  
   - Evaluated using **recall** (fraud capture effectiveness) and **precision** (false positive minimization).  
   - ML struggled due to small, imbalanced dataset and overlap between fraud & genuine patterns.  
   - Highlighted the need for **larger real-world datasets** and more complex models.

---

## 📊 Dataset Summary
- **Total Transactions:** 1109  
- **Genuine Transactions:** 1085  
- **Fraud Injected:** 24 (≈ 2.16% of total)  

### Fraud Types Injected
| ID | Fraud Type                          | Count |
|----|--------------------------------------|-------|
| 1  | Duplicate Invoice                   | 6     |
| 2  | Amount Just Below Threshold         | 2     |
| 3  | Round Suspicious Amount             | 4     |
| 4  | Same Vendor, Many Employees         | 4     |
| 5  | Suspicious Keywords in Description  | 3     |
| 6  | Late-Night Transactions             | 1     |
| 7  | Approver not in Authorization List  | 1     |
| 8  | Laid-off Employee Making Transaction| 1     |
| 9  | Vendor with High Amount             | 2     |

---

## ⚖️ Fraud Patterns, Risks & Implications
| ID | Fraud Type                          | Pattern                                                                 | Potential Implication                                                | Risk Level |
|----|--------------------------------------|-------------------------------------------------------------------------|----------------------------------------------------------------------|------------|
| 1  | Duplicate Invoice                   | Same invoice number, vendor, amount, close timestamp, same employee     | Double payment / submission error                                    | High       |
| 2  | Amount Just Below Threshold         | Splitting expenses to avoid approval                                    | Bypass approval controls                                             | Medium     |
| 3  | Round Suspicious Amount             | Rounded/divisible amounts (e.g., 900, 1000, 1050)                       | Possible fabricated figures                                          | Medium     |
| 4  | Same Vendor, Many Employees         | One vendor used by multiple employees across departments                | Collusion or ghost vendor risk                                       | High       |
| 5  | Suspicious Keywords in Description  | Keywords: "gift", "cash", "urgent"                                      | Potential bribery / personal misuse                                  | High       |
| 6  | Late-Night Transactions             | Logged between 11 PM – 6 AM                                             | Bypass reviews / override controls                                   | Medium     |
| 7  | Invalid Approver                    | Approved by personnel outside authorization list                        | Breach of internal control / authority matrix                        | High       |
| 8  | Laid-off Employee Transaction       | Transactions logged after offboarding                                   | Unauthorized access / ghost activity                                 | High       |
| 9  | Vendor with High Amount             | Invoice ≥ 2.5× vendor average                                           | Error, anomaly, or procurement irregularity                          | High       |

---

## ⚙️ Rule-Based Results
- **Transactions Flagged:** 228 (≈ 20%)  
- **Actual Frauds Captured:** 24 (100% recall)  
- **False Positives:** High (many genuine flagged as fraud)  

### Rule-Based Risk Levels
| Risk Level | Count |
|------------|-------|
| Medium     | 219   |
| High       | 8     |
| Critical   | 1     |

> ⚠️ **Trade-off:** Rule-based approach catches all frauds but over-flags genuine transactions. Suitable in high-risk environments but resource-intensive.

---

## 🤖 Machine Learning Results
- **Best Model:** Decision Tree Classifier  
- **Recall:** 50% (missed half of frauds)  
- **Precision:** 23% (flagged many genuine transactions as fraud)  

> Insight: ML models need **larger, real-world labeled datasets** and additional features to improve performance. Fraud patterns are designed to mimic genuine ones, making the problem inherently challenging.

### Confusion Matrix
<img width="719" height="589" alt="image" src="https://github.com/user-attachments/assets/1701f961-6de6-4a5e-82b5-15af26bca25c" />

### CLassification Report
<img width="754" height="357" alt="image" src="https://github.com/user-attachments/assets/17a49caf-d155-4f39-b63a-28e2bfbec9d5" />
---

## 📈 Optional: Power BI Integration
- Replicated the **rule-based logic** in Power BI using **M language**.  
- Created dashboards to visualize fraud risk levels and flagged transactions.  
- Easier for **business users** unfamiliar with Python to interact with results.

<img width="1052" height="607" alt="image" src="https://github.com/user-attachments/assets/1b6bfa10-9cc0-4042-9aab-d0a6111086e1" />

---

## 🗃️ Data Dictionary
| Column Name      | Type     | Description                                   |
|------------------|----------|-----------------------------------------------|
| transaction_id   | Integer  | Unique transaction ID                         |
| transaction_date | Datetime | Date & time of transaction                    |
| employee_id      | Integer  | Unique employee ID                            |
| vendor_name      | Text     | Vendor name                                   |
| invoice_number   | Text     | Invoice number                                |
| payment_methods  | Text     | Payment method                                |
| amount           | Float    | Transaction amount                            |
| fraud            | Integer  | Fraud flag (1 = Fraud, 0 = Genuine)           |
| fraud_type       | Text     | Fraud type (if fraudulent)                    |
| department       | Text     | Employee department                          |
| approver         | Text     | Approver name                                |
| location         | Text     | Vendor location                              |
| description      | Text     | Transaction details                          |

---

## 📌 Conclusion
- **Rule-based approach:** Strong at catching fraud but noisy (false positives).  
- **ML approach:** Promising, but requires **bigger, cleaner, labeled data** and more sophisticated models.  
- **Key takeaway:** Fraud detection requires a **hybrid approach** — automation + human judgment — to balance efficiency with accuracy.  
---

## 🔮 Next Steps
- Experiment with **ensemble ML models** (Random Forest, XGBoost, etc.).  
- Use **SMOTE** or similar techniques to handle imbalanced data.  
- Gather **real-world data** to improve generalizability.  
- Enhance **Power BI dashboard** for business-friendly fraud monitoring.  

---

## 🏷️ Tags
`#FraudDetection` `#DataAnalytics` `#Audit` `#Accounting` `#MachineLearning`
