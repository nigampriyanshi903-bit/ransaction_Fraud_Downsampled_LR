# Transaction_Fraud_Downsampled_LR
Financial transaction fraud detection using Imbalanced Classification. Implemented downsampling of the majority class to train Logistic Regression, achieving a high Recall of $0.90$ on the original, imbalanced test set, prioritizing minimized False Negatives (missed fraud)

**Goal:** To build a reliable model to detect fraudulent credit card transactions, explicitly handling the extreme class imbalance ($<0.2\%$ fraud) and prioritizing **Recall**.

### Key Methodology
1.  **Preprocessing:** `Time` and `Amount` features were scaled using a **RobustScaler** to mitigate the impact of outliers (the fraud cases).
2.  **Imbalance Handling:** Due to the severe imbalance (492 Fraud vs. 284,315 Legitimate transactions), **Random Downsampling** was applied to the training data, reducing the majority class to a 5:1 ratio against the fraud class.
3.  **Model:** **Logistic Regression** (LR) was trained on the downsampled data and evaluated on the entire, original test set.

### Final Performance Summary (Comparison with Anomaly Detection)

Initial exploration with the Isolation Forest (Unsupervised Anomaly Detection) showed poor performance (Recall: $0.27$). The Supervised LR model, however, delivered strong results:

| Metric (Class 1: Fraud) | Logistic Regression | Key Interpretation |
| :--- | :--- | :--- |
| **Recall** | **$0.90$** | **90% of actual fraud was successfully caught.** This is the primary objective. |
| **False Negatives** | **10** | Only 10 fraud transactions were missed out of 98 in the test set. |
| **Precision** | $0.15$ | Low Precision indicates 487 **False Positives** (legitimate transactions incorrectly flagged). |

**Conclusion:** The high Recall score justifies the model's use in a financial setting, where minimizing **False Negatives** (missed fraud) is the most critical business requirement.
