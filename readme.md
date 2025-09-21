# 🚗 Salifort Motors Employee Turnover Prediction

## 📝 Project Overview

This project aims to predict employee turnover at Salifort Motors. By analyzing a dataset of employee information, we build and evaluate machine learning models to identify the key factors contributing to employees leaving the company. The insights gained from this analysis are used to provide actionable recommendations to the leadership team to help reduce turnover and improve employee retention.

## 🏭🚀 Business Understanding

Salifort Motors has been experiencing a significant increase in employee turnover, which can lead to increased recruitment costs, loss of institutional knowledge, and decreased morale. The primary business problem is to understand the drivers of this turnover and to develop a predictive model that can identify employees who are at risk of leaving. This will enable the company to proactively implement retention strategies.

## 📊 Data Understanding

The data for this project is contained in the `HR_capstone_dataset.csv` file. It consists of 14,999 samples and 10 columns, including employee `satisfaction levels`, `last evaluations`, `number of projects`, `average monthly hours`, `time spent at the company`, `work accidents`, `promotions in the last 5 years`, `department`, `salary`, and whether they `left` the company.

Initial data exploration involved examining the data types, checking for missing values, and calculating descriptive statistics for the numerical features. Visualizations such as histograms, box plots, and heatmaps were used to understand the distributions of and relationships between different variables:

- Sample of features behavior among left and retained employees:
    <p align="center">
    <img src="images\output1.png" width="600"/>
    </p>
- Leaving is more likely among employees with low **and** high `satisfaction_level`. Same behavior is seen for few other features like `number_project`, `average_monthly_hours`, `time_spent_company`.
    <p align="center">
    <img src="images\output2.png" width="500"/>
    </p>
    <p align="center">
    <img src="images\output3.png" width="500"/>
    </p>
    <p align="center">
    <img src="images\output4.png" width="500"/>
    </p>
    <p align="center">
    <img src="images\output5.png" width="500"/>
    </p>
- Correlation matrix helps *feature selection* for building a model:
    <p align="center">
    <img src="images\output7.png" width="400"/>
    </p>    
## ⚙️ Modeling and Evaluation

XGBoost Classifier was selected as the machine learning model for this project. The data was also split into training and testing sets. Then the model was trained on `X-train, y_train` and was evaluated using various metrics to determine its performance.

Hyperparameter tuning was performed using `GridSearchCV` to find the optimal parameters for both models. The models were evaluated based on the following metrics, and the *champion model* was selected based on its superior performance:

- **`Recall`:** The proportion of actual positives that were identified correctly.
- **`Precision`:** The proportion of positive identifications that were actually correct.
- **`F1`-Score:** A weighted average of precision and recall.
- **`Accuracy`:** The proportion of correctly classified instances.

**Remark.** `Recall` is more important than `Precision` in this case. Because we want to minimize the number of false negatives (employees who are at risk of leaving but are predicted as not at risk).

## 💡 Conclusion

> An executive summary of the project is presented in this directory: `Executive summary.pptx`.

Testing the model on `X-test, y_test` proved a great performance with:
- `Recall`: $\quad\;\frac{TP}{TP + FN} = \frac{369}{369 + 29} = 92.7 \;\%$
- `Precision`: $\frac{TP}{TP + FN} = \frac{369}{369 + 6} \;= 98.4 \;\%$
<p align="center">
<img src="images\output_ConfusionMatrix.png" width="400"/>
</p> 

The analysis revealed that `satisfaction_level`, `time_spent_company`, and `number_projects` are the most significant predictors of employee turnover. 
<p align="center">
<img src="images\output_Feature_Importance.png" width="600"/>
</p>  

Based on these findings, the following recommendations are proposed:

- **Improve Employee Satisfaction:** Implement programs to boost employee morale and satisfaction, such as regular feedback sessions, recognition programs, and a better work-life balance.
- **Career Development:** Provide clear career paths and opportunities for growth within the company to retain employees for a longer tenure.
- **Project Management:** Ensure a fair distribution of projects and workload to prevent burnout.

Future steps for this project could include:

- **Collecting More Data:** Gathering more data, such as employee demographics and qualitative feedback, could improve model accuracy.
- **Exploring More Data:** Since the model has performed extremely well, there might be a risk of overfitting. Therefore, it is important to collect more data to ensure the model's generalizability.

- **Deployment:** Deploying the model as a web application to provide real-time predictions and insights to the HR department.
