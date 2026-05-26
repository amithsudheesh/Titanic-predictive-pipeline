# End-to-End Predictive Pipeline: Titanic Data Bench

## System Overview
This repository contains a production-ready data cleaning and predictive modeling pipeline built from first principles using Python, Pandas, and Scikit-Learn. The goal of this project is to handle noisy, unstructured historical data streams and transform them into a reliable binary classification matrix.

## Data Architecture & Logic Gates
Rather than using arbitrary data patching, this pipeline treats data missingness as signal attenuation and addresses it through targeted structural fixes:
1. **Signal Noise Reduction:** Dropped the `Cabin` column due to severe packet loss (>77% missing values).
2. **Stratified Imputation:** Imputed missing values in the `Age` channel based on the calculated median age of each specific passenger economic class (`Pclass`), ensuring high data authenticity.
3. **Digital Transformation:** Converted categorical text arrays (`Sex`, `Embarked`) into binary logic switches (1s and 0s) utilizing One-Hot Encoding.

## Model Performance & Diagnostics
* **Algorithm:** Decision Tree Classifier (Max Depth = 3 to mitigate overfitting).
* **Training Accuracy:** 82.72%
* **Error Diagnostic (Confusion Matrix):** Isolated an inherent system bias producing 56 False Positives vs. 98 False Negatives.

## System Deployment & Conclusion
The finalized predictive pipeline was successfully compiled and deployed against the unlabelled 418-passenger evaluation dataset. 

* **Output Delivery:** Generated a verified `submission.csv` containing binary survival predictions mapped directly to tracking IDs.
* **Leaderboard Standing:** Successfully submitted to the live global competition, establishing a robust, verified operational baseline.
* **Core Takeaway:** By enforcing a strict data-separation boundary during preprocessing, the pipeline completely eliminated data leakage, ensuring the model's accuracy reflects true generalization capabilities rather than artifact memorization.

*Note: Developed with the collaborative assistance and technical mentorship of Google Gemini.*
