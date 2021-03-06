# Flu-Shot-Learning
This dataset comes from the Driven Data competition "Flu Shot Learning: Predict H1N1 and Seasonal Flu Vaccines".

Business Data and Understanding

I propose that National Center for Immunization and Respiratory Diseases (NCIRD) along with the National Center for Health Statistics (NCHS) and Centers for Disease Control and Prevention (CDC) evaluate past immunization survey data from 2009 to determine which persons matching specified demographics will be likely to receive vaccines in the upcoming year. If this model based on existing data can be modeled to a certain level of confidence, the model would be able to assist in alleviating costs due to overproducing or underproducing the influenza and H1N1 vaccines in the future. Additionally, knowing the likelihood of an individual to refuse an H1N1 or seasonal flu vaccine would allow for these national organizations to create literature that can be distributed to people who may be misinformed about the vaccines’ risk association.

The target variable for this evaluation is whether a person will voluntarily receive an influenza or H1N1 vaccine based on past data randomly collected from households in the United States. This was collected by random-digit-dialing of telephones in these US households. There will be two target variables, one for the H1N1 vaccine and one for the Seasonal Flu vaccine. The target variables are clearly defined and binary already, which will aid in ease of preprocessing. This will be a supervised learning experience, as the data set at hand is complete. 

Data Preparation

The data that is available to solve this problem is concise and appropriate to the business problem. Both testing and training data is available in feature vector format. This will allow for modeling to be applied in a way that will be beneficial without an excessive amount of formatting changes. Not much needs to be done to this dataset before it is processed, though preprocessing steps will be applied. 
The evaluated data includes answers to a survey that was administered over the phone. Responses include H1N1 concerns; H1N1 knowledge; behavioral patterns such as antiviral medication use, social avoidance, wearing a face mask, attending large gatherings, going outside the home, or touching the face; whether a doctor has recommended receiving an H1N1 vaccine or seasonal flu vaccine; whether the subject had an existing chronic medical condition; whether there is regular close contact with a child under the age of six months; whether the subject is a healthcare worker; whether the subject has healthcare insurance; opinion questions about the perceived effectiveness of H1N1 and flu vaccines, perceived risk and perceived likelihood to become sick from the vaccines; along with demographic information such as the subject’s age, education level, race, sex, income, marital status, whether the subject rents or owns a home, employment status, geographical region, number of adults in the household, number of children in the household, what industry they are employed in, and their occupation.

In the data preparation stage, I evaluated the available data to look for any null values that will prevent the model from being evaluated properly. I replaced null values with mode values where appropriate. Additionally, I identified outlier data that could skew results and eliminated them from the dataset for analysis.
Since the population that was given the survey was completely randomized and scattered across the United States, the data that we are able to collect and the outcomes that we are able to predict should be accurately representative of the larger population in the United States, in theory. 

Modeling

The goal for creating a model based on this data is to determine the likelihood of a person meeting certain demographic criterion to receive an H1N1 or seasonal influenza vaccine. 
This will be a supervised learning experience, as the data set at hand is complete. The survey questions that resulted in the dataset have responses that are either binary (yes or no) or they are numeric qualitative categorical variables, though there are demographic responses that are nonnumeric. 

The values for each of the fields are largely categorical data. This means that, though the entries are numerical, the information conveyed by those values are coded qualitative variables, not quantitative. The numerical data for these fields are representative of a corresponding response on the survey, not a mathematical value.

I attempted multiple modeling techniques to achieve the best results possible. I applied logistic regression, gradient boosting classifier, decision tree, optimized decision tree, random forest, optimized random forest, k-nearest neighbors, and ensemble modeling. This analysis was done using Python in Google Colaboratory. It was my assumption that the best model will be created by ensemble modeling, in which it will be attempted to use multiple models to create a more accurate, more exhaustive model. The existing models that will be chosen to become part of the ensemble model will be determined based on their individual success rates as they relate to the AUC.

Once the models have been created using the training data set, I will apply the model to the test data set. This will allow me to evaluate the effectiveness of each model as they compare to one another.

Evaluation and Deployment

The most successful model in this process will be evaluated by comparing the area under the curve (AUC/ROC) of each model. The Area Under the Curve (AUC) refers to the area under the Receiver Operating Characteristic (ROC) curve. The Receiver Operating Characteristic (ROC) curve is a popular tool used with binary classifiers. It is very similar to the precision/recall curve. Still, instead of plotting precision versus recall, the ROC curve plots the true positive rate (another name for recall) against the false positive rate (FPR). This evaluation will be performed in Python as well as through DrivenData’s competitive platform, as the test data I will be working with does not have the actual values given.

Typically, accuracy is used as a method of measurement for how well a model is fit. However, what is actually achieved when an AUC is performed over accuracy is something that will strongly discourage people going for models that are representative, but not discriminative, as this will only actually select for models that achieve false positive and true positive rates that are significantly above random chance, which is not guaranteed for accuracy. Essentially, what this means is that the AUC will provide a more usable measure for model prediction efficiency.

So that the model performance can be evaluated accurately, we split our dataset into training and test datasets. The models will be trained with the training data and then evaluated by comparing the predictions for the test set to the actual results. For this scenario, I split the dataset into 80% training and 20% test data. Two different training and test data sets were split. I created one training and test set that identified the target variable as ‘h1n1_vaccine’ and I created one training and test set that identified the target variable as ‘seasonal_vaccine’. Feature scaling was applied to these training and test datasets. Feature scaling normalizes the data so that modeling is easily calculable and in order to standardize the range of functionality of the input dataset.

I utilized Lasso (L1-Regularization) for feature selection. This method determines the most important variables to include in analysis and zeros out the coefficients for the less important features in a way that avoids overfitting. This allows for a more robust model. This was performed on both the H1N1 and Seasonal Flu datasets separately.
For both the H1N1 and the Seasonal Flu Vaccines, I would propose using Random Forest with Cross Validation as it has the best performance. However, Random Forest in itself can use up quite a bit of resources upon implementation. For this reason, I believe the close second to choose is Gradient Boosting Classifier. This model had a very similar performance to Random Forest with CV but does not take nearly as long to run. As you can see here, the Gradient Boosting Classifier, Logistic Regression, Random Forest, and Random Forest with CV have very similar performances for both H1N1 and Seasonal Flu.

The problem that this modeling is attempting to solve is a matter of cost. It can be expensive to mass produce vaccines and having an accurate predictor for the number of vaccines that are needed can be beneficial to the National Center for Immunization and Respiratory Diseases (NCIRD), National Center for Health Statistics (NCHS), and Centers for Disease Control and Prevention (CDC) to curtail these expenses. 

Additionally, another application of the findings based on this model could allow these national centers to reach out to people who may be misinformed about the risks and dangers associated with the H1N1 and seasonal flu vaccines. This model could provide a targeted audience to which reference material and educational literature can be distributed.

While gathering this information and creating models can help to identify people who are likely to receive the H1N1 and seasonal flu vaccines, knowing this information will not necessarily solve the problem of overproduction or underproduction of these vaccines. While the information can lead to an educated conclusion, other factors that are not included in the survey may potentially impact someone’s inclination to receive a vaccine. For example, this data was collected in 2009. From 2020 to present day, the world has undergone the COVID-19 pandemic. This will undoubtedly have a great impact on a person’s proclivity to receive an H1N1 or seasonal flu vaccine, especially since the matter of a COVID-19 vaccine is such a hotly-debated topic in our time. 


References

DrivenData. (n.d.). Flu Shot Learning: Predict H1N1 and Seasonal Flu Vaccines. DrivenData. Retrieved January 17, 2021, from https://www.drivendata.org/competitions/66/flu-shot-learning/data/

Jin Huang, & Ling, C. X. (2005). Using AUC and accuracy in evaluating learning algorithms. IEEE Transactions on Knowledge and Data Engineering, 17(3), 299–310. https://doi.org/10.1109/tkde.2005.50

ROC Curve in Machine Learning. (2020, July 26). Data Science | Machine Learning | Python | C++ | Coding | Programming | JavaScript. https://thecleverprogrammer.com/2020/07/26/roc-curve-in-machine-learning/#:~:text=ROC%20Curve%20in%20Machine%20Learning%20The%20Receiver%20Operating

