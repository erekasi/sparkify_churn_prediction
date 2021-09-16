# Sparkify Churn Prediction
Exploratory data analysis to gain customer insights and churn prediction for a fictitious music streaming company named Sparkify, applying Spark SQL and Spark MLlib.

 ### Table of contents

[1) Project motivation](#Motivation)

[2) Project description](#Description)

[3) Files in the repository](#Files)

[4) Url of the related blogpost](#BlogpostUrl)

---

 ### 1) Project motivation<a name="Motivation"></a>
The current project is created to complete the capstone project requirement of the Data Scientist nanodegree program of Udacity.<br>
The key goal of the proejct is to predict churn for the users of a fictitious usic streaming company, utilizing the data provided by Udacity and Spark.<br>

---

### 2) Project description<a name="Description"></a>

#### Data source
Three versions of the dataset were made available to complete the project:
    - 12GB full dataset, recommended to be processed in a cloud cluster deployed on AWS, in free tier
    - a medium-sized subset, recommended to be processed in a cloud cluster deployed on IBM Watson, in free tier
    - 128MB subset, primarily for exploratory analysis purposes.
The 128MB subset was finally used to complete the project.

The dataset consists of the following main features:<br>

#### Libraries used
    - Numpy
    - Pandas
    - Matplotlib
    - Datetime
    - Spark SQL (pyspark.sql)
    - Spark ml (pyspark.ml)

#### Tasks performed
The project consists of 5 phases:<br>
1. **Set up Spark environment:**<br>
I created a Spark session and a SparkContext as the framework in which the analysis could be conducted.<br>

2. **Load and clean data:**<br>
I loaded the data into a Spark dataframe. I cleaned the data in terms of missing data (identifying null, nan and "" blank values). I only dropped records which contained missing values for the userID as those could not be utilized for user level churn prediction. However, nan and null values were present systematically, marking three different types of records in the dataset: music listenig events, registration events, and other administrative events. Accordingly, I did not drop records which belonged to any of these events.<br>

3. **Data exploration:**<br>
I defined “churn” as an event when a user reaches the page “Cancellation Confirmation”. I grouped data according to the churn behavior of users and plotted aggregate values accordingly. I found that there were 23% churners.<br>

4. **Feature engineering:**<br>
I applied further transformations such as creating dummies from categorical variables, dropping one from each categorical values, counting certain music listening event values and calculating minimum, maximum and average values for event and session length, and calculating the proportion a user visited a particular page (compared to her all page visits).<br>

5. **Data modeling:**<br>
I used Spark ml to develop and evaluate models. Logistic Regression and Random Forest models were created. I applied grid search and cross-validation to tune the hyperparameters of the model. F1 score was applied to decide which one of the models performs best in line with having a very imbalanced dataset with respect to the label. From a business perspective though recall would the most critical metric.
<br>

#### Summary of the results
The exploratory data analysis revealed some insights about who might churn with a higher probability: males, people from the state of Michigan and from the metropolitan areas of Philadelphia-Camden-Wilmington and New York-New Jersey-Philadelphia, and Linux users.
While the exploratory data analysis suggested that users who have tried the fee-paying version tend to churn less the model results did not confirm the hypothesis.<br>
The models applied to predict churn performed poorly in general. Only the two-thirds of churners were find with even the best performing model (recall of 66% for the Logistic Regression model for the second run). However, the pyspark code prepared is applicable for analysis in a larger dataset that could highly improve the model results.<br>
Based on the random forest model, the most important features for churn prediction proved the following:
- visit_frequency
- event_length_min
- session_length_max
- proportion of visiting the page Save Settings etc.
<br>

#### Resources
- Spark data types: https://spark.apache.org/docs/latest/sql-ref-datatypes.html
- Window functions in Spark SQL: https://databricks.com/blog/2015/07/15/introducing-window-functions-in-spark-sql.html
- Churn prediction model selection best practices: https://journalofbigdata.springeropen.com/articles/10.1186/s40537-019-0191-6
- Metrics selection recommendations: https://towardsdatascience.com/multi-class-metrics-made-simple-part-ii-the-f1-score-ebe8b2c2ca1<br>
 
 ---

### 3) Files in the repository<a name="Files"></a>
There are 2 files in this repository:<br>
- README.md: the current document
- Sparkify (31).ipynb: the Jupyter Notebook file that contains all the scripts applied for this project.

The data was provided by the educational institution, Udacity and it was prohibited to share publicly. Consequentially, it cannot be added to the current GitHub repository either. <br>

---

### 4) Url of the related blogpost<a name="BlogpostUrl"></a>
https://medium.com/@eszterrr/do-paying-users-stay-longer-86737ead01b1