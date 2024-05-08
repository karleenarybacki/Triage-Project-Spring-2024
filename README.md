# Triage Prediction Models Spring 2024
BE 5740 Group #2 Project



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

### Data Preprocessing
We imputed missing values in key columns based on the mode within subgroups defined by mistriage and KTAS_expert, ensuring filled values are representative of triage contexts. We also removed rows containing Korean characters across all text columns to mitigate biases or errors, resulting in a cleaned dataset for model training, validation, and evaluation.


### Model Evaluation
Each model is trained and evaluated using metrics such as:
- Accuracy
- Precision
- F1 Score
- Sensitivity
- Specificity.

The ROC curve from both scenarios is displayed after each model. 




## Benefits of Smart Triage Software
Our Smart Triage software approach facilitates accurate patient care prioritization and enhances mistriage prediction. Key benefits include:
- Early detection and prioritization of critical conditions, enabling rapid intervention and potentially life-saving measures.
- A decision aid for healthcare providers to accurately prioritize cases.

We demonstrated the feasibility of our Smart Triage software to "Skip the Queue, Save the Day" and bridge the gap between nurse burnout and mistriage. Our algorithm shows the potential of AI-driven triage systems to revolutionize emergency care and possibly integrate into EHR data for more efficient triage.
