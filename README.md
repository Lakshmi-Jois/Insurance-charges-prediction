 📘 README – Insurance Charges Dataset

 📂 Dataset Overview
This dataset contains 1,338 health insurance policy records. It is commonly used for predictive modeling, especially Linear Regression, to predict insurance charges (charges) based on personal attributes, health indicators, and lifestyle factors.

---

 📑 File Information
- File type: CSV
- Rows: 1,338  
- Columns: 7  

---

 🏷️ Column Descriptions

| Column Name | Description |
|-------------|-------------|
| age | Age of the policyholder (years) |
| sex | Gender of the policyholder (male / female) |
| bmi | Body Mass Index of the policyholder |
| children | Number of children/dependents covered by insurance |
| smoker | Smoking status (yes / no) |
| region | Residential region (northeast, southeast, southwest, northwest) |
| charges | Annual medical insurance charges (target variable for regression) |

---

 🔍 Possible Analyses
- Predictive Modeling: Use Linear Regression or other models to predict charges.  
- Correlation Analysis: Study relationships between age, bmi, smoker, and insurance charges.  
- EDA (Exploratory Data Analysis): Visualize distributions of age, BMI, children, and charges.  
- Feature Impact: Analyze how factors like smoking or region affect charges.  

---

 🛠️ Example Usage (Python)
python
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error

 Load dataset
df = pd.read_csv("insurance.csv")

 Encode categorical variables
df = pd.get_dummies(df, columns=['sex','smoker','region'], drop_first=True)

 Features and target
X = df.drop('charges', axis=1)
y = df['charges']

 Train-test split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

 Fit linear regression model
model = LinearRegression()
model.fit(X_train, y_train)

 Predictions
y_pred = model.predict(X_test)

 Evaluation
mse = mean_squared_error(y_test, y_pred)
print(f"Mean Squared Error: {mse}")
