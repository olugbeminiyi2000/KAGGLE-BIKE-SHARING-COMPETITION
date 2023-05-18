# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### NAME HERE
OBOLO EMMANUEL OLUWAPELUMI
## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
TODO: Add your explanation
I never realized any difference but was asked to check if any of my predictions where negative, because Kaggle would reject any submission that has any single negative value in the column count of the submission.csv file and also you cannot add any column to the file you can only submit a submission file with only the datetime column and count column any added or subtracted column would be rejected.

### What was the top ranked model that performed?
TODO: Add your explanation
My top ranked model was the WeightedEnsemble_L3 with a root mean squared error evaluation metric of -139.662040
## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
TODO: Add your explanation
My exploratory data analysis found the followings:
-There were outliers in the casual and registered column because their mean were significantly far from their medians, the standard deviation was very and and using the histogram we found that the distribution was left skewed indicating the presence of extreme small values for both columns and they were needed to be taken care of but luckily we had to drop them because they were never present in our test data. although it would have been a very good column to be used to train our models which could have made it do better because their correlation to our target were very high.

-also some columns such as season the distrubtion was uniform and the data points were evenly distributed indicating it as a categorical feature so feature engineering had to be performed on it called changing data types, also the weather column was ot uniform but the bins where gradually droping down and it's data points were also centered around 3 discrete values like season column indicating it has a categorical data and confirming it from the kaggle website that they were both categorical dtypes 

-temp, atemp, humidity columns had like a normal distribution indicating that the mean and median are not significantly different from each other and no presence of outliers and the mean ca be used as a point of central tendency

-finally the holiday column showing us the number of days that were holidays as 1 and no holiday as 0
### How much better did your model preform after adding additional features and why do you think that is?
TODO: Add your explanation
Our model improved better by adding new feature by using the datetime column after converting it into actual date time and it seems that the datetime was necessary to actually predict good models one the instruction was to predict the total count of bikes rented during each our per day so the datetime would play an important role in our model in performing, because for each day, month, year and hour the count of bicycles rented would definitely differ, but a short note was left on my jupyter note book was to train another using the year, month, day, and hour part of the datetime and drop the season categorical data type because it has a high collinear value with the month column causing multicollinearity and make our model perform poorly, and just set our autoglon auto ml to the default value which I tried giving me a rmse value <= -35.456, and our score increased to 0.47447
## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
TODO: Add your explanation
I did not get a very significant change using the hyperparameter although it improved a little, and the hyperparmeters were to much to select the right ones to get better results. aand I do not know if I applied them correctly, but from the fit_summary it seems only the Neural network hyparameter was the only one not functioning well
### If you were given more time with this dataset, where do you think you would spend more time?
TODO: Add your explanation
I would use the last training_run I didn't implement and try to find better hyperparameters to fine tune it properly, by using a method I learnt to fisrt overfit your model to first fit your training example then finally use hyperparameters that help reduce overfitting next which is used when building neural networks, and see how it works then continue optimizing it, but I would like to request for the test casual and registered data because the secret of a good model is the data used in training and those two columns would definitely improve one's model due to their collinearity to the target which shows they are the most immportant feature of that dataset.
### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
|model|hpo1|hpo2|hpo3|score|
|--|--|--|--|--|
|initial|{'max_base_models': 25}|{'max_base_models_per_type': 5}|{'save_bag_folds': True}|1.32680|
|add_features|{'max_base_models': 25}|{'max_base_models_per_type': 5}|{'save_bag_folds': True}|0.48621|
|hpo|{'max_base_models': 25}|{'max_base_models_per_type': 5}|{'save_bag_folds': True}|0.47584|

### Create a line plot showing the top model score for the three (or more) training runs during the project.

TODO: Replace the image below with your own.

![model_train_score.png](KAGGLE-BIKE-SHARING-COMPETITION/project/model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

TODO: Replace the image below with your own.

![model_test_score.png](KAGGLE-BIKE-SHARING-COMPETITION/project/model_test_score.png)

## Summary
TODO: Add your explanation
Machine Learning Concepts:
-Domain: Bikes & Car sharing companies like uber, lyft, door-dash.
-Data: This data was provided by Hadi Fanaee Tork using data from capital bike share, which provides me with hourly rental data spanning for two years, training set contains first 19 days of each month, while test set starts from the 20th day to the end.
-Model: Using an Auto Ml tool to select best model that could help us achieve our desired goal, using the right hyperparameters, algorithm and the right evaluation metric

ML Life Cycle:
-Product:
 -Problem: To predict the total counts of bikes rented during each hour covered by the test set
 -Objective: To help businesses prepare for spikes in the services but also improve customer experience
-Data:
 -Got data from kaggle by installing kaggle module, getting my username and API key, and wrting the command to get the zipfile
 -Unzip the file to get the train, test, and submission csv files
 -Perform EDA using python modules called pandas to create a gold standard
 -Found insights and potential pitfalls in the data
 -Performed some forms of Data Transformations
-Engineering:
 -Build the model using Autogluon an AutoML framework
 -Tested the model
 -Evaluated it using some specified metric based on the task, optimized the model in all ways.
 -Model not yet deployed
-Results:
 -No results gotten since it has not yet interacted with the reak world or environment
 
Model Deployment Workflow:
-Got the splitted data already into train and test datasets
-Prepared the data well by doing some feature selection, EDA, and some transformations
-Trained it with an AutoMl framework
-Evaluated the Model
-Then tuned the model for better results