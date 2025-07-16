________________________________________
# 🕵️‍♂️ Forensic Fraud Detection Prototype — Hybrid Rule-Based & ML Approach
## 📌 Overview
This project demonstrates a prototype forensic fraud detection system that simulates how forensic teams can combine rule-based flags with machine learning to identify fraudulent transactions — even when fraud patterns are simple or subtle.
The project uses synthetic data designed to mimic real-world spending transactions with realistic fraud injection logic. It illustrates how traditional manual flags and automated ML classification can work together to catch fraud and minimize false positives.
________________________________________
## 🎯 Project Goal
The aim is to:
* Detect transactions likely to be fraudulent using domain-informed rules.
* Reduce false positives from rule-based detection by filtering them with a trained ML model.
* Explore the limits and challenges of using supervised ML for forensic tasks where fraud is rare, subtle, and overlaps heavily with legitimate patterns.
________________________________________
## 🔍 Project Approach
### ✅ Phase 1 — Simple Fraud, Simple Detection
1.	Synthetic training data was generated with simple fraud patterns (e.g., duplicate invoices, suspicious amounts).
2.	Basic rule-based flags labeled these transactions as Fraud or Legitimate.
3.	Data was preprocessed and visualized (e.g., PCA to check overlap between classes).
4.	Multiple ML models were trained:
	- K-Nearest Neighbors (KNN)
	- Decision Tree Classifier 
  - Random Forest Classifier

### Injected simple fraud patterns
| Fraud Type                           | Fraud Description                                                      |
|--------------------------------------|----------------------------------------------------------------------- |
| Duplicate invoices                   | Identical copies of original invoice                                   |
| Round suspicious amount              | Values that are near perfect (e.g., 10,000; 15,000)                    |
| Amount just below threshold          | Value is just below threshold                                          |
| Same Vendor used by multiple employees | A vendor used by more than 2 unique employees                        |
| Suspicious Keyword in description    | Keywords such as “gift”, “cash”, “urgent”                              |
| Vendor with high amount              | Vendor that has amount 2 or more times than its average                |
| Missing PO                           | Transaction that is missing invoice number                             |


### Key insight:
Because fraud patterns were simple, CART models tended to overfit — perfectly memorizing training data but not generalizing well. KNN and Logistic Regression could not separate fraud due to heavy overlap and class imbalance.
________________________________________
### ✅ Phase 2 — Adding Subtle Fraud, Tuning the Model
To simulate real-world complexity:
1.	A new dataset was generated with subtle fraud patterns added — e.g., small variations in amounts, unusual timings, or vague expense descriptions.
2.	Top features were extracted using feature importance.
3.	CART and Random Forest models were hyperparameter tuned to reduce overfitting.
4.	PCA was used to check whether fraud patterns clustered more clearly.

### Injected subtle fraud patterns
| Fraud Type                      | Fraud Description                                                      |
|---------------------------------|-------------------------------------------------------------------     |
| Slightly unusual amount         | Amount that is 1.7 to 1.99 times that of vendor’s average amount       |
| Unusual timing patterns         | Logging on transaction after work hour (11 p.m. to 6 a.m.)             |
| Vague Description               | Description that is incomplete or vaguely described                    |
| Invalid Approver                | Transaction approved by invalid personnel                              |
| Transaction logged by invalid employee | Transaction logged by laid-off employee after off-boarding date |

### Key insight:
Even with tuning and subtle patterns, the model’s recall performed moderately (≈68%) but showed that ML alone cannot perfectly catch subtle frauds in class imbalanced scenarios.
________________________________________
### ✅ Phase 3 — Hybrid Approach
To mimic real-world forensic practice:
1.	A final synthetic dataset was generated with both simple and subtle fraud.
2.	A rule-based detection function flagged suspicious transactions using conditions like:
-	Slightly unusual amounts
-	Out-of-hours spending
-	Vague or missing invoice numbers
-	Duplicate invoices
-	Suspicious round amounts
-	Use of laid-off employees or invalid approvers
3.	The rule-based filter flagged 98% of transactions — resulting in many false positives.
4.	The flagged transactions were then passed to the trained ML model to filter out obvious legitimate cases.
*	The model correctly reclassified about 40% of flagged transactions as actual fraud.
*	Remaining false negatives highlight the realistic challenge of subtle fraud detection.
________________________________________
### 📈 Selected Model Final Results 
Tune Decision Tree Classifier was used as prototype ML model
* Metric	Value
* Train Accuracy (DTC)	~0.98
* Test Accuracy (DTC)	~0.97
* Cross-Validation Score	~0.98
* Recall (Fraud class)	~0.68
* False Positives (Rule only)	High (~98% flagged as fraud)
* False Positives (Hybrid)	Reduced — filtered by ML
________________________________________
### ⚡️ Key Takeaways
*	Simple frauds are easy to memorize but do not teach the model to generalize subtle variations.
*	Subtle frauds need more features, better domain knowledge, or unsupervised/anomaly detection.
*	Rules alone produce high recall but also high false positives — operationally expensive.
*	A hybrid approach (rules + ML filter) is more practical — flag suspicious activity broadly, then filter false positives automatically.
________________________________________
### 🏆 Why This Matters
This project is a realistic prototype of how forensic audit and fraud detection teams can apply hybrid detection pipelines to:
*	Automate checks,
*	Reduce manual review workload,
*	Provide explainable flags to investigators,
*	Combine business rules with predictive patterns.
________________________________________
### ⚙️ Tools & Tech
*	Python (pandas, numpy, sklearn)
*	Scikit-Learn Pipelines
*	Matplotlib, Seaborn (EDA & PCA)
*	Faker (synthetic data generation)
________________________________________
### 📂 Next Steps (To revisit again)
*	Improve feature engineering (e.g., time series patterns, employee-vendor network analysis).
*	Test anomaly detection and unsupervised clustering.
*	Integrate cost-sensitive learning to handle class imbalance more robustly.
*	Package the rule engine as a reusable module.
________________________________________

