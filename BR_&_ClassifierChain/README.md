# Multi-label classification using Binary Relevance and Classifier Chain from scratch.

__Input:__ Multilabel Yeast Dataset having 103 features and 14 target class


## Following Tasks are performed:
1. Loading dataset and splitting to training & testing
2. Implement the Binary Relevance Algorithm & Model Evaluation
3. Implement the Binary Relevance Algorithm with Under-Sampling
4. Compare the Performance of Different Binary Relevance Approaches
5. Implement the Classifier Chains Algorithm
6. Evaluate the Performance of the Classifier Chains Algorithm

## Refelection of Performance:

Taking both the multi-label classification techniques into consideration following conclusions can be made:

__1. Binary Relevance__

__Accuracy Score__
* Binary Relevance classifier without undersampling produces the best 80% accuracy (Using Logistic Regression)  which is greater than any other undersampling model.
* We just under-sample a majority class if the gap between majority and minority is too big. This result in loss of accuracy due reduction in training samples and hence the overall accuracy.

__F1 Score__
* Without undersampling, the binary relevance classifier has lower F1 scores resulting in high bias that leads to high accuracy and poor recall values. 
* But after undersampling the gap between majority and minority class gets reduced which results in better F1 score.

Without Undersampling

|  | Logistic Regression | Decision Tree | Random Forest |
| -------|---------------------|---------------|---------------|
| __Accuracy Score__ | 0.80 | 0.65 | 0.77 |
| __F1 Score(macro avg)__ | 0.34 | 0.39 | 0.33 |

__2. Classifier Chain__

* Classifier chain works better than Binary Relevance because it takes label dependency into consideration. But if the output of the very first model comes wrong then the subsequent model output will be impacted badly.

* This approach has more complexity than binary relevance because it requires the previous target labels as input for the next predictions.

* However it can be seen that there is no substantial difference between the model accuracy which is quite unexpected.

|  | Logistic Regression |
| -------|---------------|
| __Accuracy Score__ | 0.8044 |
| __F1 Score(macro avg)__ | 0.3468 |


* A comparison graph showing accuracies of both algorithms.

![image](https://user-images.githubusercontent.com/26432753/76269230-b28e1c00-6268-11ea-852e-c53fde03c128.png)

