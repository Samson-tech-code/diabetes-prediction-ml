
# Diabetes Prediction using Machine Learning

 # 📌 Project Overview
This project applies machine learning techniques to predict the likelihood of diabetes in patients based on medical and lifestyle data.  
It demonstrates skills in **data cleaning**, **exploratory data analysis (EDA)**, **feature engineering**, and **model evaluation** using real-world healthcare data.


## Objective
- Develop a predictive model to identify individuals at higher risk of diabetes.
- Compare multiple algorithms and select the best-performing model.
- Present results through visualisations and feature importance analysis.

## Dataset
Dataset: [Pima Indians Diabetes Database](https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database)  
Contains 768 observations with predictive attributes (e.g., Glucose, BMI, Age, Blood Pressure) + target label.

## Methods
1. **Data Preprocessing**
   - Addressed missing values and zero entries in essential health indicators.
   - Scaled numerical features to ensure model compatibility.
2. **EDA & Visualisation**
   - Identified associations between features and diabetes outcome.
   - Demonstrated key trends using histograms, pair plots, and distribution charts.
3. **Model Development**
   - Performed Logistic Regression, Decision Tree, Random Forest, and Support Vector Machine (SVM).
   - Used **AUC-ROC** and **F1-score** to compare models.
4. **Feature Selection**
   - Employed feature importance analysis to determine the most relevant predictors.
   - Reduced less significant features to improve model efficiency and interpretability.
5. **Evaluation**
   -  Random Forest was determined as the best model.

## Results
- Random Forest achieved **77.9% accuracy** and **AUC-ROC: 0.8191**
- Feature importance analysis revealed Glucose, BMI, and Age as top predictors

## Key Visualisation
![ROC Curve](images/roc_curve.png)  
*Random Forest achieved the highest area under the curve.*

![Feature Importance](images/feature_importance_rf.png)  
*Most influential features driving predictions.*

##  Model Confusion Matrices
Below are the confusion matrices for the top models tested:

**Random Forest (Best Performing Model)**  
![Confusion Matrix - Random Forest](images/confusion_matrix_rf.png)

**Support Vector Machine (SVM)**  
![Confusion Matrix - SVM](images/confusion_matrix_svm.png)

**Logistic Regression**  
![Confusion Matrix - Logistic Regression](images/confusion_matrix_logistic.png)


## Tools & Libraries
- **Languages:** Python 
- **Libraries:** Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn  
- **Environment:** Google Colab / Jupyter Notebook

## How to Run
1. Clone the repository:
```bash
git clone https://github.com/yourusername/diabetes-prediction-ml.git
pip install pandas numpy scikit-learn matplotlib seaborn
