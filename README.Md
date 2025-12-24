# Flight Delay Prediction Using Cluster-Specific Ensemble Models and LSTM

## Course Information
**Course:** DASC-5380-W01 – Data Analytics  
**University:** Texas A&M University – Corpus Christi  

**Students:**  
- Prathyusha Pentam  
- Sri Surya Pravallika Ajjarapu  

---

## Project Overview
Flight delays cause inconvenience and additional costs for passengers, airlines, and airports.  
This project focuses on predicting whether a flight will be **delayed by more than 15 minutes at arrival** using only **pre-departure information**, making the prediction useful in real-time before takeoff.

We compare:
- Classical machine learning models
- A **Cluster-Specific Ensemble (CSE)** using k-means and Random Forests
- A simple **LSTM neural network** as a deep-learning baseline

---

## Dataset
- **Source:** Kaggle – Flight Delay Prediction Dataset
- **Time Period:** 2018–2022
- **Target Variable:**  
  - `ArrDel15 = 1` → Arrival delayed by more than 15 minutes  
  - `ArrDel15 = 0` → On-time arrival

### Pre-Departure Features Used
- Month
- Day of week
- Scheduled departure time (minutes since midnight)
- Flight distance
- Origin airport
- Destination airport
- Marketing airline code

---

## Data Preprocessing
- Missing numeric values filled with median
- Missing categorical values filled with most frequent category
- Numeric features standardized
- Categorical features one-hot encoded
- Stratified **80% training / 20% testing split**
- Class imbalance handled using `class_weight = balanced`

---

## Models Implemented

### Global Baseline Models
- Logistic Regression
- Random Forest
- Support Vector Machine (SVM)

---

### Cluster-Specific Ensemble (CSE)
- K-means clustering (K = 4) using:
  - Month
  - Day of week
  - Departure time
  - Distance
- A separate Random Forest trained for each cluster
- Test samples assigned to a cluster before prediction

---

### LSTM Model
- One LSTM layer (32 units)
- Dense hidden layer (16 units)
- Sigmoid output for binary classification
- Used as a deep-learning baseline

---

## Evaluation Metrics
- Accuracy
- Precision
- Recall
- F1 Score
- ROC–AUC
- Confusion Matrices (for key models)

---

## Results Summary
- **Random Forest** performed best among global models
- **Cluster-Specific Ensemble** achieved performance similar to Random Forest
- **LSTM** showed high accuracy but very low recall and F1 due to class imbalance
- Clustering on time and distance alone did not significantly outperform a strong global model

---

## Files in This Repository
- Jupyter Notebook – model implementation and experiments
- Presentation (`Presentation_DAFi (1).pptx`)
- README.md – project documentation

---

## Conclusion
This project demonstrates that tree-based models like Random Forest are effective for flight delay prediction using tabular, pre-departure data.  
Cluster-specific models can match global performance, while simple LSTM models are not well-suited for this imbalanced tabular dataset without richer temporal features.

---

## Future Work
- Incorporate weather, holidays, and airport congestion data
- Try alternative clustering strategies
- Use gradient boosting models
- Explore advanced sequence models with richer temporal features
