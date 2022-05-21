# machine_learning_challenge

Instructions
Preprocess the Data
* Preprocess the dataset prior to fitting the model.
* Perform feature selection and remove unnecessary features.
* Use MinMaxScaler to scale the numerical data.
* Separate the data into training and testing data.
Tune Model Parameters
* Use GridSearch to tune model parameters.
* Tune and compare at least two different classifiers.
Reporting
* Create a README that reports a comparison of each model's performance as well as a summary about your findings and any assumptions you can make based on your model (is your model good enough to predict new exoplanets? Why or why not? What would make your model be better at predicting new exoplanets?).

—————————————————————————————————————

REPORT

For the initial portion of this assignment, I tried the following models to generate the best approach in predicting data from exoplanet_data.csv
- Decision Tree
- Neural Network
- Logistic Regression
- Random Forest
- Support Vector Machine
The final two that I selected to complete this challenge, due to both the high scores scores and practicalities are : Decision Tree and Support Vector Machine, with Decision Tree being the best one so far and hence the model is saved (andriani_decisiontree.sav)

Several things were noted when developing with each model based on the exoplanet data and can be found below:
- Neural Network
	Initial Accuracy was 0.89, however upon tuning it would only return 0.37, and would throw error with Oracle triggering exit. This might indicate overfitting and that the model is not the best one for the dataset
- Logistic Regression (Initial accuracy at 0.86 and the same score after tuning)
- Random Forest (initial accuracy at 0.9 and after tuning was 0.85. Although this model is also promising as the best model for the dataset, it took a long time to execute, and due to the many possible of parameters that we could put in might need longer to complete tuning this model. I have had to run this model on TPU on AWS for some parameter tuning as well.

The best two :
- Support Vector Machine
	initial accuracy 0.84 (f-1 score) and 0.87 after being tuned
	To select important features that will largely affect the model, the top 11 and bottom 11 values, totalling 22 values (after sorting by descending order all the coef_ & X values) the following were selected to be of enough importance :  
0         koi_srad
1             koi_depth
2         koi_fpflag_ss
3         koi_srad_err1
4       koi_period_err1
5       koi_impact_err1
6               koi_teq
7            koi_period
8        koi_steff_err1
9     koi_duration_err1
10     koi_time0bk_err1
11     koi_time0bk_err2
12    koi_duration_err2
13       koi_steff_err2
14         koi_duration
15            koi_slogg
16       koi_slogg_err2
17            koi_steff
18        koi_model_snr
19      koi_period_err2
20        koi_fpflag_co
21        koi_fpflag_nt
Also, with encoding as following: 1 - confirmed, 2 - false positive, 0-candidate
Prediction for the first 22 : [1, 2, 2, 1, 2, 2, 2, 1, 1, 2, 1, 2, 2, 0, 0, 1, 2, 2, 1, 0, 2, 1]
While the real values for the first 22 : [1, 2, 2, 1, 2, 2, 2, 1, 0, 2, 1, 2, 2, 0, 0, 1, 2, 2, 1, 0, 2, 0]
There are missed predictions, but of small number. This is consistent with the model’s score

- Decision Tree : initial score for this one was 0.87, and 0.88 after being tuned
	
	To select important features that will largely affect the model, the top 22 values were selected  :  
['koi_insol_err2',
 'koi_slogg_err2',
 'koi_period_err1',
 'koi_prad',
 'koi_steff_err1',
 'koi_srad_err1',
 'koi_steff_err2',
 'koi_duration_err1',
 'koi_kepmag',
 'koi_time0bk',
 'koi_tce_plnt_num',
 'dec',
 'koi_slogg_err1',
 'koi_duration',
 'koi_period',
 'ra',
 'koi_impact',
 'koi_fpflag_ec',
 'koi_model_snr',
 'koi_fpflag_ss',
 'koi_fpflag_co',
 'koi_fpflag_nt']
Also, with encoding as following: 1 - confirmed, 2 - false positive, 0-candidate
Prediction for the first 22 : [1, 2, 2, 1, 2, 2, 2, 1, 1, 2, 1, 2, 2, 0, 0, 1, 2, 2, 1, 0, 2, 1]
While the real values for the first 22 : [1, 2, 2, 1, 2, 2, 2, 1, 0, 2, 1, 2, 2, 0, 0, 1, 2, 2, 1, 0, 2, 0]
There are missed predictions, but of small number. This is consistent with the model’s score
