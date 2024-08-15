# Credit Risk Analysis

Credit risk analysis is a critical process in the financial industry, aimed at evaluating the likelihood that a borrower will default on their debt obligations. This analysis helps lenders and financial institutions make informed decisions about extending credit and managing risk. The dataset is found:  


# Methodology



## Data exploration

The data includes 9 columns about detailed customers' information <br>
| Age | Ed | Employ | Address | Income | Debtinc | Creddebt | Otherddebt | Default
|  --------  |  -------  |  --------  |  -------  |--------  |  -------  | -------  | -------  | -------  |
 | 41 | 3 | 17 | 12 | 176 | 9.3 | 11.359392 | 5.008608 | 1.0
 | 27 | 1 | 10 | 6 | 31 | 17.3 |  1.362202 | 4.000798  |    0.0
 | 40 | 1 | 15 | 14 | 55 | 5.5  | 0.856075 | 2.168925   |   0.0
 | ... | ... | ...| ... | ... | ...  | ... | ...   |   ...
## Correlation analysis

Visualize the data in **Line chart** and  **Heatmap** to indicate the correlations between variables in the dataset, which can identify the **key relationships** and patterns:

- The Heatmap shows the significant correlations bewteen these variables:
	
	- Age and Income 
	- Income and Creddebt (Credit to debt)

<img width="801" alt="image" src="https://github.com/user-attachments/assets/d9715377-ab92-4ba9-aa15-a51007537519">

# Take a deeper analysis in two relationships that are mentioned in the heatmap 
- Age and Income: The older individuals tend to have higher incomes.
	> We can take actionable recommendation on targeting customer segments. For example, focus on customers in the age group 40-55.
 
<img width="1000" alt="image" src="https://github.com/user-attachments/assets/8b2cdfac-d10a-44b6-95d1-91e7d43994cc">

## Model building

### 1. Logistic regression
|default | precision  |  recall | f1-score  | support | 
|  --------  |  -------  |  --------  |  -------  | -------  |
0.0 |  0.88   |   0.94   |   0.91     |  161
 1.0| 0.76  |    0.59   |   0.67     |   49
accuracy |  |    |  0.86    |  210
macro avg | 0.82   |   0.77    |  0.79     |  210
weighted avg| 0.86   |   0.86  |    0.86     |  210
- Model Performance Insights: <br>

`Accuracy`: 0.86 (86%) indicates that the model correctly predicts the outcome for 86% of the instances. This is a good overall performance.

- Class-Specific Performance: <br>

   `Class 0 (Non-Defaulters)`
  
	-	Precision: 0.88 (88%) means that when the model predicts a non-defaulter, it is correct 88% of the time.
	- Recall: 0.94 (94%) indicates that the model correctly identifies 94% of the actual non-defaulters.
	-	F1-Score: 0.91 (91%) is a balance between precision and recall, showing strong performance for non-defaulters. 
	
	 `Class 1 (Defaulters)`
  
	- Precision: 0.76 (76%) means that when the model predicts a defaulter, it is correct 76% of the time
	- Recall: 0.59 (59%) indicates that the model correctly identifies 59% of the actual defaulters.
	 -	F1-Score: 0.67 (67%) shows a moderate balance between precision and recall for defaulters.

	`Macro and Weighted Averages` 
	- Macro Avg: Averages the metrics for both classes without considering class imbalance. It shows a balanced view of the model's performance across both classes.
	- Weighted Avg: Averages the metrics for both classes, weighted by the number of instances in each class. It reflects the overall performance considering class imbalance.
	
	`ROC-AUC Score`
	- ROC-AUC Score: 0.87 (87%) indicates that the model has a good ability to distinguish between defaulters and non-defaulters. 

### 2. ROC Curve

<img width="923" alt="image" src="https://github.com/user-attachments/assets/7c010415-f0dd-477d-ad29-8780a817aabf">

## Improvement 

•  `Class Imbalance`: The dataset has more non-defaulters (161) than defaulters (49). This imbalance can affect the model's performance, particularly for the minority class (defaulters).  <br>
•  `High Precision for Non-Defaulters`: The model is very good at predicting non-defaulters correctly, which is reflected in the high precision and recall for class 0. <br>
•  `Moderate Performance for Defaulters`: The model's recall for defaulters is lower (0.59), meaning it misses 41% of actual defaulters. This could be a concern if identifying defaulters is critical.
#### Actions to Improve Model Performance
Address Class Imbalance:

•  `Resampling Techniques`: Use techniques like SMOTE (Synthetic Minority Over-sampling Technique) or undersampling to balance the classes.  <br>
• `Class Weights`: Adjust the class weights in the model to give more importance to the minority class (defaulters).


## Recommendation and Next steps

•  Policy Adjustment: Implement policies that encourage borrowers to maintain a higher credit to debt ratio. This can be achieved by offering better interest rates or incentives for those who manage their credit well.<br>
•  Marketing Strategy: Focus marketing efforts on segments with higher credit to debt ratios, as they are less likely to default.<br>
•  Loyalty Programs: Implement loyalty programs that reward long-term customers who consistently manage their credit well.



