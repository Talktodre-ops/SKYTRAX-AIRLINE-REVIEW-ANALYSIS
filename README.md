# SKYTRAX AIRLINE REVIEW ANALYSIS
 Customer Booking Prediction for British Airways

 # Customer Booking Prediction for British Airways

## 📌 Project Overview
This project aims to predict whether a customer will complete a booking for British Airways using historical customer behavior and flight data. The goal is to identify key drivers of bookings and provide actionable insights to improve revenue and customer targeting strategies.

---

## 🗃️ Dataset
- **Size**: 50,000 entries with 14 original features (expanded to 42 after preprocessing).
- **Key Features**:
  - `num_passengers`, `purchase_lead`, `flight_duration`, `route`, `booking_origin`, etc.
  - Target Variable: `booking_complete` (binary: 0 = Not Booked, 1 = Booked).
- **Class Distribution**: 
  - **85%**: Not Booked (Class 0)
  - **15%**: Booked (Class 1)

---

## 🛠️ Methodology
### 1. Data Preprocessing
- **Handling Imbalance**: Techniques like `class_weight="balanced"` and `BalancedBaggingClassifier`.
- **Feature Engineering**: 
  - Created `last_minute_booking` (bookings ≤ 7 days before departure).
  - Encoded categorical variables (`sales_channel`, `trip_type`, `flight_day`).

### 2. Model Training
- **Algorithm**: Random Forest (baseline) + Balanced Bagging Classifier.
- **Hyperparameter Tuning**: Grid search for optimal `n_estimators`, `max_depth`, etc.
- **Evaluation Metrics**: Accuracy, Precision, Recall, F1-Score, and ROC-AUC.

---

## 📊 Results
### Key Metrics (Random Forest):
| Metric      | Class 0 (Not Booked) | Class 1 (Booked) | Overall     |
|-------------|----------------------|------------------|-------------|
| **Accuracy**| -                    | -                | **84.19%**  |
| **Precision**| 0.87                | 0.44             | -           |
| **Recall**  | 0.95                 | **0.20**         | -           |
| **ROC-AUC** | -                    | -                | **0.777**   |

### Classification Report:
           precision    recall  f1-score   support
       0       0.87      0.95      0.91      8504
       1       0.44      0.20      0.28      1496



---

## 🚨 Challenges
1. **Severe Class Imbalance**: 85% of customers did not complete bookings.
2. **Low Recall for Bookings**: The model misses **80% of actual bookings** (critical for revenue).
3. **Precision-Recall Trade-off**: High precision for non-bookings but low precision for bookings.

---

## 💡 Recommendations
1. **Target High-Intent Customers**:
   - Focus on features like `purchase_lead` (short lead times) and `flight_duration` (long-haul flights).
2. **Campaign Optimization**:
   - Use insights from feature importance to design personalized offers (e.g., discounts for early bookings).
3. **Model Improvements**:
   - Combine SMOTE oversampling with ensemble methods to boost recall.
   - Adjust classification thresholds to prioritize capturing bookings.

---

## 📈 Feature Importance
Top predictors of bookings:
1. **`purchase_lead`** (Time between booking and departure)
2. **`flight_duration`** (Longer flights correlate with bookings)
3. **`last_minute_booking`** (Critical for urgent travelers)

![Feature Importance Plot](feature_importance.png)

---

## 🚀 How to Run
1. **Install Dependencies**:
   ```bash
   pip install pandas scikit-learn imbalanced-learn matplotlib seaborn

   jupyter notebook british_airways_booking_analysis.ipynb

   📂 Files
british_airways_booking_analysis.ipynb: Jupyter notebook with full analysis.

data/booking_data.csv: Preprocessed dataset.

report/presentation_template.pptx: Summary slide template.

Note: For detailed code and visualizations, refer to the Jupyter Notebook.


This README provides a clear, concise summary for stakeholders and technical audiences, emphasizing actionable insights and next steps. Let me know if you need further refinements! 🚀
