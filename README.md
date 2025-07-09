\# 🏥 Healthcare Insurance Premium Predictor — ML-Powered Risk-Based Quotation System



This project is a machine learning pipeline and Streamlit web app designed to predict the \*\*annual healthcare insurance premium\*\* for individuals based on demographic and health-related risk factors. The system uses an age-based segmentation approach with two distinct models to improve accuracy and handle data imbalance.



---



\## 💡 What This Project Does



An insurance client requested a system that could predict a customer's annual premium based on available input features such as age, income, gender, and (for certain cases) a genetical risk score. The solution includes data analysis, model segmentation, and deployment in an interactive web interface.



---



\## 🔍 How It Works



1\. \*\*Data Acquisition \& Exploration\*\*  

&nbsp;  The input data was provided in Excel format. It was cleaned, analyzed, and visualized using Python libraries such as pandas, seaborn, and matplotlib.



2\. \*\*Initial Model Training\*\*  

&nbsp;  Several regression models were trained — including Linear Regression, Ridge, Lasso, and XGBoost. XGBoost initially produced the best R² score.



3\. \*\*Error Analysis\*\*  

&nbsp;  Residuals were calculated (as the difference between predicted and actual premiums), and percentage error was analyzed. It was found that the majority of large errors (above 10%) were concentrated among individuals aged 25 or below.



4\. \*\*Age-Based Data Segmentation\*\*  

&nbsp;  The dataset was split into two parts:

&nbsp;  - `healthcare\_premium\_young` → individuals aged ≤ 25

&nbsp;  - `healthcare\_premium\_rest` → individuals aged > 25



5\. \*\*Feature Enrichment\*\*  

&nbsp;  For the younger segment, an updated dataset was received containing an additional feature: `genetical\_risk\_score`. This feature was only available for the ≤ 25 group.



6\. \*\*Final Modeling Strategy\*\*  

&nbsp;  - For the \*\*younger group\*\*, Linear Regression was used after including `genetical\_risk\_score`, yielding a strong R² of ~98%.

&nbsp;  - For the \*\*older group\*\*, XGBoost remained the best-performing model.



7\. \*\*Model Saving\*\*  

&nbsp;  Both models and their respective scalers were serialized using `joblib` and stored in the `artifacts/` directory.



8\. \*\*Interactive Deployment\*\*  

&nbsp;  A Streamlit app was created to serve predictions. Based on the entered age, the appropriate model is selected and used to compute the predicted premium.



---



\## 🖥️ Try It Yourself



To run the app locally:



1\. \*\*Install dependencies\*\*



```bash

pip install -r requirements.txt

```



2\. \*\*Launch the app\*\*



```bash

streamlit run app/main.py

```



3\. \*\*Input feature values\*\* such as age, income, gender, and genetical risk score (if applicable) to receive a predicted premium value.



---



\## 🚧 Notes



\- The younger dataset includes an extra feature (`genetical\_risk\_score`) which is not present in the older dataset.

\- A unified schema was ensured by assigning a value of 0 to this feature for the older group.

\- This project demonstrates the use of \*\*segmented modeling\*\*, \*\*feature-based enrichment\*\*, and \*\*modular deployment\*\* for real-world ML workflows.

\- Deployment to \*\*Streamlit Cloud\*\* is planned following GitHub integration.



---



\## 📁 Repo Structure



\- `notebooks/` → All data exploration, modeling, and error analysis workflows

\- `data/` → Original and segmented Excel datasets

\- `app/` → Streamlit app, helper functions, and model artifacts

\- `requirements.txt` → All required libraries for running the app

\- `.gitignore` → Clean project setup with ignored caches and temp files



---

```



