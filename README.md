# Credit_Risk_Analysis

# Overview

Using the machine learning skills we have acquired we are planning to run several models on the credit card dataset from LendingClub.  Our ultimate goal is to review the performance of each of the models; and ascertain whether any particular model proves to be most effective for identifying risk from a dataset. 

# Resampling our data

After we create our features and target, we split the data into training and testing groups.  

As we see in the below image our classes of data are pretty significantly skewed in favor of Low Risk(good loans), with over 68K instances.  By comparison, we see only a few hundred instances of high risk(bad loans) within the data. 
![Y_Value_Counts](https://github.com/Gkmb2390/Credit_Risk_Analysis/blob/main/Resources/Y%20Value%20Counts.png)

# Naive Oversampling

Our first model that we begin testing is the Naive Random Oversampling.  Using RandomOversampler from sklearn we resample the data X and y training data to have an equivalent number of high and low risk cases.

After reviewing the Accuracy score generated in our next step; we see that the test has a middling 62% accuracy.  Which would indicate that is capabale of detecting roughly 62% of the bad credit cases - which does not inspire a great deal of confidence. 

![OversampleAccuracyResult](https://github.com/Gkmb2390/Credit_Risk_Analysis/blob/main/Resources/Naive%20accuracy.png)

The confusion matrix results echo the expectation from our Accuracy Test.  Only 52 true positives indicates that we only caught 52 bad loan submissions. When reviewing the classification we find the precision for high risk campaigns to be only .01 which is indicates only a 1% chance of a bad loan.  

![ConfusionMatrix](https://github.com/Gkmb2390/Credit_Risk_Analysis/blob/main/Resources/Naive%20confusion%20matrix.png)

In summary, we see that this method of testing does an excellent job of identifying good loans, but a rather poor job of indicating the high risk or bad loans. 

# SMOTE Oversampling

Following a similar process as above we find the results match a great deal to the Naive Oversampling model.  In the image below of the Confusion matrix and the classification report, they deliver virtually identical results as the Naive model.  

![SMOTEAccuracyResult](https://github.com/Gkmb2390/Credit_Risk_Analysis/blob/main/Resources/SMOTE%20report.png)

Ultimately this method of testing proves equally poor as the Naive method with a similar precision score and an equally high f1 score - indicating the signifcant imbalance between precision and sensitivy. 
![SMOTEReport](https://github.com/Gkmb2390/Credit_Risk_Analysis/blob/main/Resources/SMOTE%20report.png)
# Clustered Centroids

After resampling the test and train sets using an undersampling method we find similar results as previous.  The Accuracy score here equates to roughly 53% initially inidicating that undersampling the data would provide a more inaccurate test. 

![Cluster Accuracy]()

Looking over the confusion matrix and classification report, we see fairly similar results with regard to our capacity to interpret high risk/bad loans. We do find a mildly more balanced result when reviewing our 'false' line item.  Indicating the test would have a higher number of false positive bad credit results.  

Again we see a very low precision rate amongst the high risk loans, and a very high precision amongst low risk.  This model, as with the previous models are excellent at discovering low risk loans - which is unfortuantely the opposite of what we are looking to achieve.

![Cluster report]()


# Combiniation Sampling - SMOTEENN

After running the resampling formulas and completeing logistic regression on the data, we can see a similar accuracy result to our first 2 models.  Sitting at roughly 64% we are seeing improvement from the Cluster Undersampling model; which is positive but not what I had expected in terms of change to performance. 

![Combo accuracy]() 

The confusion matrix and classification report are unsuprisingly a happy medium between the two model methodologies. Unfortunately, we find similar results to all previous test indicating that this model will not preform well for our intended functions. 

![Combo report]()

# Ensemble Methods

Our next approach required us to duplicate a bit of our effort in re-splitting our data into test and train groups.  After having completed those same steps again we are asked to utilize the ensemble methodologies to determine if one of those models would prove more efficient at identifying bad loans.

# Balanced Random Forest Technique

Immediately we notice that the accuracy report associated to the Forest technique is significantly higher than our previous models.  At nearly 80% we are looking at a report that maybe able to identify 4 out 5 high risk loans - which is far more promising than we have seen up to this point.

![Balance Accuracy]()

Taking a look into the confusion matrix results, we can see similar results to the oversampling model results with a high number of True Falses, i.e. low risk loans. The classification report provides similar evidence - however we do see a small improvement in the precision of this model up to 3%.

![Balance report]()

# AdaBoost Model

The Adaboost model accuracy report indicates our highest chance of identifying those "high risk" loans with a 92% accuracy result.  

![AdaBoost Accuracy]()

Reviewing our confusion matrix and classification report results, we find very promising identifiers that the AdaBoost method would be most successful in predicting bad loans.  When reviewing the high risk line item, we see the highest precision of all the tests; however that equates to only 5%.  However, the recall rate being the highest amongst any tests indicates that the highest correct identifications amongst all the models. That in combonation with equally high scores amongst the low risk line item would; to me indicate the best option for success in this case. 

![AdaBoost report]()

# Conclusions

While a majority of the testing methods do have merit and useful insight; I am excluding the undersampling methodology given its much poorer results. I would have to wholeheartedly recommend the AdaBoost Model.  

The Oversampling methods provide better than middeling accuracy - they don't provide nearly as high recall rates.  Following those would be the Balanced Forest Model which saw signifcant improvements across the board for our high risk loan line item; however the AdaBoost provides just a slightly better result - and ultimately we are attempting to derive the best model for our needs. 
