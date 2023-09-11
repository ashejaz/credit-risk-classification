# Module 12 Report Template

## Overview of the Analysis

The purpose of this project was to create a machine learning model to effectively classify loans as either healthy (labelled `0`) or high-risk (labelled `1`).

Lending data was imported from a CSV file with 'loan_status' being set as the y variable and the X data consisting of variables including loan size, interest rate, borrower income, debt to income, number of accounts, derogatory marks and total debt.

Overall, the dataset contained 77,536 rows of which 96.8% of which were healthy loans.

### Method

The data was split into training and testing datasets before a logistic regression model was created using the sci-kit learn library in Python.

The model was fit onto the training data and then used on the testing data to make predictions on the risk-level of the loans.

The RandomOverSampler from the imbalanced-learn library was then used to resample the training data to ensure an equal number of datapoints for both healthy and high-risk loans. A second linear regression model was trained using this resampled data and used to make predictions. The performance metrics of both models were then gathered and compared to determine the impact of data resampling on the effectivness of the regression model and whether any of the models could be recommended for use in risk classification.

## Results

* Machine Learning Model 1 (Original Data):
  * The balanced accuracy score was 94.4%, indicating that the model performs well in classifying both healthy and high-risk loans, taking into account the class imbalance in the dataset.
  * For healthy loans (`0`), precision, accuracy and recall all had a perfect value of 1.00 indicating the the model performs exceptionally well at classifying healthy loans.
  * For high-risk loans (`1`), the precision value was lower at 0.87 suggesting that when the model predicts a loan as high-risk, it is correct 87% of the time. The recall value is 0.89 indicating that 89% of high-risk loans were correctly identified. The f1 score for high-risk loans therefore sits at 0.88. Though it indicates that the model performs well at classifying high-risk loans, there is still room for improvement.
![Screenshot 2023-09-11 at 15 25 11](https://github.com/ashejaz/credit-risk-classification/assets/127614970/c8fc04d2-3d25-4fcf-b682-650ff25fbc2e)
  * The confusion matrix demonstrates that while only 0.43% of healthy loans were incorrectly classified (false positives), 10.72% of high-risk loans were incorrectly classified (false negatives). This supports the assertion that the model's classification of high risk loans could be improved.
    ![Screenshot 2023-09-11 at 16 27 37](https://github.com/ashejaz/credit-risk-classification/assets/127614970/3fce0879-55e8-41bd-8dbb-fa3c5d78ba76)
 
    

* Machine Learning Model 2 (Resampled Data):
  * The balanced accuracy score with the model trained on resampled data increased to 99.6% suggesting near-perfect classification of both healthy and high-risk loans.
  * For healthy loans (`0`), precision, accuracy and recall all retained their value of 1.00 suggesting highly accurate classification of healthy loans.
  * For high-risk loans (`1`), precision remained the same at 87%, though recall increased from 0.89 to 1.00 resulting in an improved f1-score of 0.93 compared to 0.88 with the previous model. This is a significant improvement in correct classification of high-risk loans.
![Screenshot 2023-09-11 at 15 39 41](https://github.com/ashejaz/credit-risk-classification/assets/127614970/d59bacf3-eb7f-430e-868f-f2f7a0d354a0)
  * From the confusion matrix we can calculate that the % of healthy loans being incorrectly classified (false negatives) has increased slightly from 0.43% to 0.49% which is not a significant increase. However, the % of high-risk loans being incorrectly classified (false positives) has dropped significantly from 10.72% previously to just 0.32% by using resampled data to train the model.
    ![Screenshot 2023-09-11 at 16 27 49](https://github.com/ashejaz/credit-risk-classification/assets/127614970/aad08bdf-0dfb-44ac-9bac-669531dc71f5)



## Summary

Overall, model 2 which was trained on resampled data performs better than model 1 as indicated by the improvement in balanced accuracy and f1 scores. Specifically, the model is significantly better at classifying high-risk loans, with the % of false positives reducing greatly.

Before recommending a model for this purpose it is important to consider the problem we are trying to solve. Model 2 is the better choice for accurately identifying high-risk loans, though it does result in a very slight decrease in performance for healthy loans displayed by the greater number of false negatives. Since typically high-risk loans would be the target of classification models, model 2 would be recommended for its highly accurate overall performance. However, I believe further improvement may still need to be possible to reduce the number of false negative results as an incorrect classification of a healthy loan as high-risk would likely have a negative personal effect on individuals applying for financial support.
