# Starbucks Capstone Challenge

### Table of Contents

1. [Project Overview](#overview)
2. [Project Components](#components)
3. [Installation](#installation)
4. [File Descriptions](#files)
5. [Instructions](#instructions)
6. [Results](#results)
7. [Licensing, Authors, and Acknowledgements](#licensing)

## Project Overview<a name="overview"></a>

The Starbucks project is coming out from customer marketing domain. Traditional marketing analytics or scoreboards are essential for evaluating the success or failure of organization’s past marketing activities. But today's marketers or organizations can leverage advanced marketing techniques like predictive modeling for customer behavior, predictive lead scoring, and all sorts of strategies based on predictive analytics insights. 

Various Cases for Predictive Marketing Analytics are:
•	Detailed Lead Scoring
•	Lead Segmentation for Campaign Nurturing
•	Targeted Content Distribution
•	Lifetime Value Prediction
•	Churn Rate Prediction
•	Upselling and Cross-Selling Readiness
•	Understanding Product Fit
•	Optimization of Marketing Campaigns

In this Project, we would deal with the case of ‘Optimization of Marketing Campaigns’. Predictive techniques can make an organization marketing investment much more efficient and helps in regularly validating results. Connecting customer information to the operational data provides valuable insight into customer behavior and the health of your overall business. 

Refer below links in order to have better understanding of the impact of predictive analytics for better marketing performance.

1.	[Predictive Analytics: What it is and why it matters](https://www.sas.com/en_us/insights/analytics/predictive-analytics.html)
2.	[Marketing Analytics for Data-Rich Environments](https://www.rhsmith.umd.edu/files/Documents/Departments/Marketing/wedel-kannan-jm-2016-final.pdf)
3.	[How to Use Predictive Analytics for Better Marketing Performance](https://www.singlegrain.com/digital-marketing-analytics/how-to-use-predictive-analytics-for-better-marketing-performance/)

In this project, we would go through the predictive modeling technique for customer behavior through Starbucks dataset example. Starbucks provided simulated data that mimics customer behavior on the Starbucks rewards mobile app. Once every few days, Starbucks sends out an offer to users of the mobile app. An offer can be merely an advertisement for a drink or an actual offer such as a discount or BOGO (buy one get one free). Some users might not receive any offer during certain weeks. Not all users receive the same offer, and this data set is a simplified version of the real Starbucks app because the underlying simulator only has one product whereas Starbucks actually sells dozens of products. 

In this project, Starbucks wants to connect offer data, customer data and transaction data (operational data) to gain insights about customer behavior and overall effectiveness of offers as a value for business. 


**With the above key statement in mind, below is the main objective or problem motivation or problem statement:**

>**_Build a model that predicts whether a customer would respond to an offer or not._**

Above problem is a binary classification problem and could be solved by using supervised machine learning classification algorithms like Logistic Regression, Random Forest, Adaboost, Gradient Boosting. The brief outline of the solution of this problem is that the Starbucks different datasets (offer, demographic & transript) would be combined after data pre-processing (cleaning & transformation) and feature engineering to form a combined dataset. The appropriate and correct combined data would be fed into various machine learning classification models which would find the hidden traits of the customer behavior which plays an important role in influencing the customer to either respond to an offer or not. The trained classification models would classify the customers into target classes (1 if a customer would respond or 0 if a customer would not respond). The performance of the models would be compared based on appropriate performance metric (discussed in below section) for this project. The best performing classification model would be selected based on performance metric & training time and would be refined further by fine tuning the hyperparameters of the best estimator of the selected model.

Below are few case studies from customer marketing domain:

1.	[How we use trees to predict customer behavior: random forests in action](https://www.profusion.com/how-we-use-trees-to-predict-customer-behaviour-random-forests-in-action/)
2.	[Evaluation of Classification and Ensemble Algorithms for Bank Customer Marketing Response Prediction](https://www.researchgate.net/publication/315456960_Evaluation_of_Classification_and_Ensemble_Algorithms_for_Bank_Customer_Marketing_Response_Prediction_Journal_Article)
3.	["How Social Media Insights Turned Around Lexus' Holiday Campaigns" by Infegy](https://content.infegy.com/using-social-media-insights-to-turn-around-lexus-ad-campaigns)
4.	[Machine-Learning Techniques for Customer Retention: A Comparative Study](https://thesai.org/Downloads/Volume9No2/Paper_38-Machine_Learning_Techniques_for_Customer_Retention.pdf)



## Project Components<a name="components"></a>

The entire analysis would contain below steps:

1. Analyse each of the portfolio, profile and transaction data.
2. Clean and transform each of the portfolio, profile and transaction data.
3. Combine portfolio, profile and transaction data.
4. Select a performance metric to analyse performance of the model and to compare different models.
5. Compute the performance of a baseline model against which performance of other different models would be compared.
6. Select best performing model based on the metric and training time.
7. Calculate the feature importances given by best estimator of the trained model.
8. Compute the performance of best model on test set and visualize the performance via confusion matrix plot.

## Installation<a name="installation"></a>

 - The code should run with no issues using Python versions 3.*.
 - No extra besides the built-in libraries from Anaconda needed to run this project
 - Data Processing & Machine Learning Libraries: NumPy, SciPy, Pandas, Sciki-Learn
 - Data Visualization: Matplotlib, Seaborn

## File Descriptions<a name="files"></a>

The data is contained in three files:

* portfolio.json - containing offer ids and meta data about each offer (duration, type, etc.)
* profile.json - demographic data for each customer
* transcript.json - records for transactions, offers received, offers viewed, and offers completed

Here is the schema and explanation of each variable in the files:

**portfolio.json**
* id (string) - offer id
* offer_type (string) - type of offer ie BOGO, discount, informational
* difficulty (int) - minimum required spend to complete an offer
* reward (int) - reward given for completing an offer
* duration (int) - time for offer to be open, in days
* channels (list of strings)

**profile.json**
* age (int) - age of the customer 
* became_member_on (int) - date when customer created an app account
* gender (str) - gender of the customer (note some entries contain 'O' for other rather than M or F)
* id (str) - customer id
* income (float) - customer's income

**transcript.json**
* event (str) - record description (ie transaction, offer received, offer viewed, etc.)
* person (str) - customer id
* time (int) - time in hours since start of test. The data begins at time t=0
* value - (dict of strings) - either an offer id or transaction amount depending on the record

## Instructions<a name="instructions"></a>

1. The entire anlaysis is contained within the jupyter notebook.
2. All 3 .json files should be located in data folder as combined data would be created from these 3 files located in data folder.


## Results<a name="results"></a>

* Offer_id 'fafdcd668e3743c1bb461111dcafc2a4' is the most successful offer and corresponds to 'discount' offer with minimum spend of 10 dollars within 10 days of receiving of the offer and having reward of 2 dollars. Offer_id '3f207df678b143eea3cee63160fa8bed' is the least successful offer and corresponds to informational offer with no minimum spend required having no reward.

* All our trained classifier produce better f1_score than the baseline model's f1_score of 0.6996. RandomForestClassifier and GradientBoostingClassifier got nearly equal f1_score(approx. 0.92) but RandomForestClassifier took very less time to train than the GradientBoostingClassifier. Therefore, best performing classifier algorithm among the above 4 classifiers was RandomForestClassifier.

* The hyperparameters of the trained RandomForestClassifier was further fine tuned using GridSearchCV and our model got improved and produced a better f1_score of 0.9319 with cross-validation.

* Our best estimator produced f1_score of 0.9336 on test data, which is quite good.

* Top 10 features which influence whether the customer will respond to an offer or not after viewing the offer are: 'total_amount', 'membership_tenure' , 'social', 'difficulty', 'duration', 'reward', '2018', '2016', 'income_30ths' and 'age_50s'.

* [Project Notebook: Starbucks Capstone Challenge](https://nbviewer.jupyter.org/github/gauravansal/Starbucks-Capstone-Challenge/blob/master/Starbucks_Capstone_notebook.ipynb)
* [Blog Post: Whom will respond to Starbucks Offers?](https://medium.com/@ansal.gaurav/whom-will-respond-to-starbucks-offers-84f98eded283)

## Licensing, Authors, and Acknowledgements<a name="licensing"></a>

<a name="license"></a>
### License
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

<a name="acknowledgement"></a>
### Acknowledgements

This project was completed as part of the [Udacity Machine Learning Engineer Nanodegree](https://www.udacity.com/course/machine-learning-engineer-nanodegree--nd009t). The dataset used in this project contains simulated data that mimics customer behavior on the Starbucks rewards mobile app. [Starbucks® Rewards program: Starbucks Coffee Company](https://www.starbucks.com/rewards/).