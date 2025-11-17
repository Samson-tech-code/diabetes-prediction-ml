
# Diabetes Prediction using Machine Learning

 # Project Overview
This project applies machine learning techniques to predict diabetes risk in patients based on medical and lifestyle data. **Using the Pima Indians Diabetes Database**, I developed and compared three classification models to identify individuals at higher risk, achieving **77.9% accuracy** with Random Forest.

**Key Skills Demonstrated:**

- Data cleaning & preprocessing with missing value imputation
- Exploratory Data Analysis (EDA) with statistical visualizations
- Machine learning model development & hyperparameter tuning
- Feature importance analysis for healthcare insights
- Model evaluation using ROC-AUC, precision, recall, and F1-score

## Objective
- Develop a predictive model to identify individuals at higher risk of diabetes.
- Compare multiple algorithms and select the best-performing model.
- Present results through visualisations and feature importance analysis.

## Dataset
Source: [Pima Indians Diabetes Database](https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database)  

**Dataset Characteristics:**

- **768 patient records** (female patients of Pima Indian heritage, ages 21+)
- **8 predictive features:**

   - **Pregnancies:** Number of times pregnant
   - **Glucose:** Plasma glucose concentration (mg/dL)
   - **Blood Pressure:** Diastolic blood pressure (mm Hg)
   - **Skin Thickness:** Triceps skinfold thickness (mm)
   - **Insulin:** 2-hour serum insulin (mu U/ml)
   - **BMI:** Body mass index (weight in kg/(height in m)²)
   - **Diabetes** Pedigree Function: Genetic diabetes likelihood score
   - **Age:** Patient age (years)


- **Target Variable:** Binary classification

   - 1 = Diabetic
   - 0 = Non-diabetic


- **Class Distribution:**

   - 268 diabetic cases (34.9%)
   - 500 non-diabetic cases (65.1%)

- **Data Quality Challenges:**
   - Missing values encoded as zeros in medical measurements (Glucose, Blood Pressure, BMI, etc.)
   - Class imbalance requiring careful evaluation metrics
   - Real-world healthcare data with natural variability

## Methods
### 1️⃣ Data Preprocessing

**Missing Value Treatment:**
- Identified zero values in essential health indicators (Glucose, Blood Pressure, Skin Thickness, Insulin, BMI)
- Applied **median imputation** to replace zeros with clinically reasonable values
- Preserved data integrity while addressing 48.7% of records with at least one zero value

**Feature Scaling:**
- Applied **StandardScaler** to normalize all numerical features
- Ensured model compatibility across algorithms with different sensitivity to feature scales

**Data Splitting:**
- **Training set:** 80% (614 samples)
- **Test set:** 20% (154 samples)
- Applied **stratification** to maintain class balance

### 2️⃣ Exploratory Data Analysis (EDA)

**Statistical Analysis:**
- Computed descriptive statistics for all features across diabetic vs non-diabetic groups
- Identified significant differences in Glucose (mean: 141 vs 110 mg/dL), BMI (mean: 35.4 vs 30.3), and Age (mean: 37.1 vs 31.2 years)

**Visualisation Techniques:**
- **Correlation heatmap:** Identified Glucose-Diabetes strongest correlation (r=0.47)
- **Distribution plots:** Showed right-skewed distributions for Insulin and Skin Thickness
- **Pair plots:** Revealed non-linear relationships between features
- **Box plots:** Detected outliers in Insulin and Blood Pressure measurements

### 3️⃣ Model Development & Comparison

Trained and evaluated **3 supervised learning algorithms:**

| Model | Accuracy | AUC-ROC | F1-Score | Precision | Recall |
|-------|----------|---------|----------|-----------|--------|
| **Random Forest** ⭐ | **77.9%** | **0.8183** | **0.65** | **0.74** | **0.57** |
| Support Vector Machine | 73.4% | 0.7963 | 0.59 | 0.64 | 0.54 |
| Logistic Regression | 70.1% | 0.8128 | 0.54 | 0.59 | 0.50 |

*Note: Precision, Recall, and F1-Score are for class 1 (diabetic patients)*

**Model Selection Rationale:**
- Random Forest selected as optimal model due to highest accuracy and AUC-ROC
- Best balance between precision (75%) and recall (69%)
- Robust to outliers and non-linear relationships

**Hyperparameter Tuning:**
- Applied **GridSearchCV** with 5-fold cross-validation
- Optimised Random Forest parameters: `n_estimators: 200`, `max_depth: 10

### 4️⃣ Feature Importance Analysis

Random Forest feature importance ranking:

| Rank | Feature | Importance Score | Clinical Significance |
|------|---------|------------------|----------------------|
| 1 | **Glucose** | 0.28 (28%) | Primary diabetes indicator |
| 2 | **BMI** | 0.18 (18%) | Strong obesity-diabetes link |
| 3 | **Age** | 0.14 (15%) | Diabetes risk increases with age |
| 4 | Diabetes Pedigree Function | 0.12 (12%) | Genetic predisposition factor |
| 5 | Blood Pressure | 0.10 (10%) | Cardiovascular comorbidity |
| 6 | Pregnancies | 0.08 (8%) | Gestational diabetes history |
| 7 | Insulin | 0.06 (6%) | Metabolic dysfunction indicator |
| 8 | Skin Thickness | 0.04 (4%) | Weakest individual predictor |

**Clinical Interpretation:**
- Top 3 features (Glucose, BMI, Age) account for **60.7%** of predictive power
- Aligns with medical literature on diabetes risk factors

### 5️⃣  Model Evaluation

**Performance Metrics Explanation:**

- **Accuracy (77.9%):** Overall correct predictions across both classes
- **AUC-ROC (0.82):** Strong discriminatory power (0.8-0.9 = excellent)
- **Precision (74%):** When model predicts diabetes, it's correct 74% of the time
- **Recall (57%):** Model identifies 57% of actual diabetic cases
- **F1-Score (0.65):** Balanced measure of precision and recall

## 🏆 Results Summary
### Key Findings

**Random Forest (Best Performer):**
- ✅ Highest overall accuracy (77.9%)
- ✅ Highest AUC-ROC (0.8183) indicating excellent discriminatory power
- ✅ Best precision (74%) - minimizes false positive diagnoses
- ✅ Balanced performance across both classes

**Support Vector Machine:**
- Good accuracy (73.4%) but lower than Random Forest
- Competitive AUC (0.7963)
- Moderate recall (54%) - missed more diabetic cases

**Logistic Regression:**
- Lowest accuracy (70.1%) but surprisingly high AUC (0.8128)
- **Lowest recall (50%)** - missed half of diabetic cases
- Simple, interpretable baseline model

### Confusion Matrices

**Random Forest (Best Model):**
```
                Predicted
              Non-Diabetic  Diabetic
Actual   
Non-Diabetic      89          11
Diabetic          23          31
```

- True Negatives: 89
- False Positives: 11 (11% of non-diabetic flagged incorrectly)
- False Negatives: 23 (43% of diabetic cases missed) 
- True Positives: 31

**Support Vector Machine:**
```
                Predicted
              Non-Diabetic  Diabetic
Actual   
Non-Diabetic      84          16
Diabetic          25          29
```

**Logistic Regression:**
```
                Predicted
              Non-Diabetic  Diabetic
Actual   
Non-Diabetic      81          19
Diabetic          27          27
```

### Clinical Interpretation

**Strengths:**
- Random Forest correctly identified 31 out of 54 diabetic patients (57% recall)
- Low false positive rate (11%) reduces unnecessary follow-up tests
- High precision (74%) means most positive predictions are correct

**Limitations:**
- Specific to Pima Indian female population; generalizability to other demographics uncertain
- Relatively small sample size (768 records, 154 test samples)
- 23 diabetic patients were missed (false negatives) - this is clinically concerning
- Recall could be improved through:
  - Class imbalance handling (SMOTE)
  - Threshold adjustment for sensitivity
  - Ensemble stacking methods

**Recommendation:**
- Random Forest is the optimal model for this dataset
- Consider adjusting decision threshold to improve recall (catch more diabetic cases)
- Further validation needed on external datasets before clinical deployment


## Key Visualisation
![ROC Curve](images/roc_curve.png)  
*Random Forest achieved the highest AUC (0.82), demonstrating superior classification ability.*

![Feature Importance](images/feature_importance_rf.png)  
*Glucose, BMI, and Age as the top 3 predictors.*

##  Model Confusion Matrices
Below are the confusion matrices for the top models tested:

**Random Forest (Best Performing Model)**  
![Confusion Matrix - Random Forest](images/confusion_matrix_rf.png)

**Support Vector Machine (SVM)**  
![Confusion Matrix - SVM](images/confusion_matrix_svm.png)

**Logistic Regression**  
![Confusion Matrix - Logistic Regression](images/confusion_matrix_logistic.png)


### Tools & How to Run**
##  Tools & Technologies

**Programming Language:**
- Python 3.8+

**Core Libraries:**
- **Data Manipulation:** Pandas, NumPy
- **Machine Learning:** Scikit-learn
- **Visualisation:** Matplotlib, Seaborn

**Development Environment:**
- Jupyter Notebook / Google Colab

## How to Run this project
### Prerequisites
- Python 3.8 or higher
- Jupyter Notebook or Google Colab

### Installation Steps

**1. Clone the Repository**
```bash
git clone https://github.com/Samson-tech-code/diabetes-prediction-ml.git
cd diabetes-prediction-ml


**2. Install Dependencies**
```bash
pip install -r requirements.txt
```

Or install manually:
```bash
pip install pandas numpy scikit-learn matplotlib seaborn jupyter
```

**3. Launch Jupyter Notebook**
```bash
jupyter notebook
```

**4. Run the Analysis**
- Open `diabetes_prediction.ipynb`
- Run all cells sequentially (Kernel → Restart & Run All)

### Alternative: Google Colab
1. Open [Google Colab](https://colab.research.google.com/)
2. File → Open notebook → GitHub tab
3. Enter: `Samson-tech-code/diabetes-prediction-ml`
4. Select `diabetes_prediction.ipynb`
5. Run all cells

---
````

### Project Structure
```
diabetes-prediction-ml/
│
├── diabetes_prediction.ipynb    # Main Jupyter notebook with full analysis
├── data/
│   └── diabetes.csv             # Pima Indians Diabetes dataset (768 records)
├── images/                      # Visualisation outputs
│   ├── roc_curve.png           # ROC curve comparison for all models
│   ├── feature_importance_rf.png # Random Forest feature importance bar chart
│   ├── confusion_matrix_rf.png  # Random Forest confusion matrix heatmap
│   ├── confusion_matrix_svm.png # SVM confusion matrix heatmap
│   └── confusion_matrix_logistic.png # Logistic Regression confusion matrix
├── requirements.txt             # Python package dependencies
├── README.md                    # Project documentation (this file)
└── LICENSE                      # MIT License
```

### **Learning & Future**
````markdown
## Learning Outcomes

Through this project, I developed expertise in:

### Technical Skills
✅ **Data Preprocessing:** Handling missing values, outlier detection, feature scaling  
✅ **Exploratory Data Analysis:** Statistical analysis, correlation analysis  
✅ **Machine Learning:** Model training, comparison, hyperparameter tuning  
✅ **Model Evaluation:** ROC-AUC, confusion matrices, cross-validation  
✅ **Python Programming:** Pandas, NumPy, Scikit-learn implementation  

### Domain Knowledge
✅ **Healthcare Analytics:** Understanding clinical diabetes risk factors  
✅ **Medical Data:** Addressing measurement errors and missing values  

---

## 🔮 Future Improvements

### Short-Term
- [ ] Implement **SMOTE** to address class imbalance
- [ ] Add **XGBoost and LightGBM** models
- [ ] Integrate **SHAP** for advanced interpretability
- [ ] Perform nested cross-validation
- [ ] Create interactive visualizations using Plotly

### Long-Term
- [ ] Deploy as **Flask/Streamlit web application**
- [ ] Validate on external diabetes datasets
- [ ] Incorporate temporal data for longitudinal prediction
- [ ] Partner with healthcare professionals for clinical validation

---


### **Contact**
````markdown
## 📧 Contact & Connect

**Samson Olanrewaju**  
MSc Applied Data Science | University of Essex  
Aspiring Data Analyst | Machine Learning Enthusiast

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0077B5?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/samson-olanrewaju-40b545194)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-181717?style=for-the-badge&logo=github)](https://github.com/Samson-tech-code)
[![Email](https://img.shields.io/badge/Email-Contact-D14836?style=for-the-badge&logo=gmail)](mailto:Samson1@live.ie)

**Open to opportunities in:**
- Data Analyst roles
- Business Intelligence positions  
- Healthcare analytics
- Entry-level Data Science positions

---

## 🙏 Acknowledgments

- **UCI Machine Learning Repository** for the Pima Indians Diabetes Database
- **Scikit-learn community** for excellent documentation
- **University of Essex** MSc Applied Data Science program
