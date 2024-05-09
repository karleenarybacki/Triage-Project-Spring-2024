# Smart Triage 🏥
- Roopsha Bandopadhyay, Aditi Kulkarni, Benjamin Lin, Karleena Rybacki, Manasa Vempati
- BE 5740 Group #2 Project

## Background
The emergency department (ED) triage process is crucial for ensuring timely patient care. However, evaluating patients' conditions and vital signs to prioritize those in greatest need can be complex and overwhelming, especially in crowded EDs. To address this, machine learning models can predict triage outcomes based on patient data, optimizing EDs for better resource allocation and timely identification of patients requiring emergency attention.



## Project Overview
This project presents four optimized classification models to enhance ED triage: Support Vector Machine (SVM), Random Forest, Logistic Regression, and k-Nearest Neighbor (kNN). We explored two scenarios: (1) with access to patient vital signs (trained on all features) and (2) without vital signs (trained on a subset of features).


### Reasoning:
- **Support Vector Machine (SVM):** Aims to find the hyperplane that best separates patients into different mistriage levels; creates a multi-dimensional space where each patient's data point is located based on their values for these features. Ultimately, predicts the mistriage level, the urgency of the patient's condition based on the KTAS score, depending on the hyperplane boundary.
- **Random Forest:** Aims to construct multiple decision trees (100) where each tree represents a subset of the data and makes decisions about mistriage from an ensemble approach. Ultimately, the mode of the predicted mistriage levels across all trees is chosen as the final prediction.

- **Logistic Regression:** Aims to model the probability of each mistriage level directly using a logistic function by estimating the relationship between the features and the mistriage level by fitting a sigmoid curve to the data. Ultimately, the model calculates the probability of each mistriage level and assigns the one with the highest probability as the final prediction.

- **k-Nearest Neighbors (kNN):** Aims to predict the KTAS score by calculating the distance between the new input point and every other point in the dataset. The k value of nearest neighbors (5) was then identified based on these distances. Ultimately, the mistriage level is predicted as the majority class among the k closest neighbors.
After evaluating the performance of each model, we selected the best-performing model for our Smart Triage software. This model was chosen based on its accuracy, efficiency, and ability to generalize well to new, unseen data.


## Approach
Our approach involved evaluating the performance of each model and selecting the best-performing model for our Smart Triage software. This model was chosen based on its accuracy, efficiency, and ability to generalize well to new, unseen data.

### _Dataset Overview_
Our data, as reported in [Moon et al.](https://doi.org/10.1371/journal.pone.0216972), was gathered from 2 different emergency departments (EDs), 1 regional and 1 local; both academic urban medical centers. The data entries were collected by emergency nurses and doctors who jointly recorded patients' medical histories and physical examination results. The local ED data was collected by only an emergency nurse who recorded results from patients' physical examinations. The ED that the patient visited was reported in "Group." In each ED, the number of patient visits per hour over 20 randomly-selected days within the study period was calculated and reported as "Patients number per hour." A total of 1,540 medical records were collected, with 676 from the regional ED and 864 from the local ED. The subsequent exclusion criteria included: patients under 15, data entered 30 minutes after initial assessment, patients who canceled care, and insufficient medical records; 1267 eligible patient medical records remained after exclusion.

### _Data Visualization_
The heatmap below visualizes the frequency of each manually curated category of Chief Complaints across various levels of urgency (KTAS scores), showing the distribution of Chief Complaints among the five KTAS categories.
<p align="center">
    <img src="https://github.com/karleenarybacki/Triage-Project-Spring-2024/assets/89222332/573685e1-d23f-4943-ba38-e9bcaf257454" alt="heatmap_chief_complaints" width="734">
</p>


### _Data Preprocessing_
We imputed missing values in three columns based on the mode within the subgroups defined by mistriage and KTAS_expert, and removed rows with Korean characters across all text columns. This resulted in 1,260 data entries ready for model training and evaluation.

### _Model Selection and Implementation_
We implemented four machine learning models in this project: 
1. Support Vector Machine (SVM)
2. Random Forest
3. Logistic Regression
4. k-Nearest Neighbors (kNN)

For specifics on the implementation of each model, please refer to the [code](https://github.com/karleenarybacki/Triage-Project-Spring-2024#:~:text=Triage_Troopers_Code.ipynb) available at the top of this page.

### _Model Evaluation_
Each model was trained and evaluated using metrics such as accuracy, precision, F1 score, sensitivity, and specificity. The ROC curve from both scenarios is displayed after each model.





# Results

## Model Performance 
The model performance is shown in the table below, where the Random Forest model achieved the highest accuracy overall. The table summarizes the key model evaluation metric values for each of the models created and tested, including accuracy, precision, F1 score, sensitivity, and specificity. The models are listed in order of best to worst in terms of accuracy, with the Random Forest model achieving the highest accuracy of 97.11%, followed by the Logistic Regression model with an accuracy of 90.5%, the SVM model with an accuracy of 89.67%, and the kNN model with an accuracy of 85.95%. The models with Vitals taken (trained on all features) performed better than when no vitals were taken. Overall, The Random Forest model outperformed the other models in all metrics, followed closely by the Logistic Regression model. The SVM model performed reasonably well, while the kNN model had the lowest performance overall. 

<p align="center">
    <img width="734" alt="Screenshot 2024-05-08 at 7 41 26 PM" src="https://github.com/karleenarybacki/Triage-Project-Spring-2024/assets/89222332/8ee44e95-a933-4a14-8168-8bf1d5cbcdc4">
</p>




The performance of each model is shown in the ROC curves below among the different models; SVM (A), Random Forest (B), Logistic Regression (C), and kNN (D). The blue curves represent the models with vitals taken (all features), while the red curves represent the models with no vitals taken (selected features). The ROC curves reflect the evaluation metrics, with the Random Forest model exhibiting a perfect ROC curve, indicating a high level of accuracy and potentially suggesting overfitting. The order of the models in terms of accuracy follows the same pattern as in the table, with the Random Forest model achieving the highest accuracy, followed by the Logistic Regression model, the SVM model, and the kNN model. The ROC curves provide a visual representation of the trade-off between the true positive rate and the false positive rate for each model, with the area under the curve indicating the model's ability to distinguish between positive and negative classes.
<p align="center">
    <img width="734" alt="Screenshot 2024-05-08 at 7 39 48 PM" src="https://github.com/karleenarybacki/Triage-Project-Spring-2024/assets/89222332/5ab70866-37f1-4980-9841-458f25a17bee">
</p>



## Benefits of Smart Triage Software
We demonstrated the feasibility of applying machine learning techniques to achieve Smart Triage. "Skip the Queue, Save the Day" and bridge the gap between nurse burnout and mistriage. Our algorithm shows the potential of AI-driven triage systems to revolutionize emergency care and possibly integrate into EHR data for more efficient triage.

<p align="center">
    <img width="400" alt="Screenshot 2024-05-08 at 7 52 13 PM" src="https://github.com/karleenarybacki/Triage-Project-Spring-2024/assets/89222332/8ef3355a-eab4-44ef-9d5b-b84e196ead29">
</p>










