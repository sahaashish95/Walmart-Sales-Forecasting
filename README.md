# Walmart-Sales-Forecasting
This is a walmart sales forecasting problem. This is one of my case study .In this case study our task is to predict sales for walmart stores .I take this problem from kaggle .and our final score for this problem is under top 10% of kaggle score .

Walmart problem introduction</br>
1.I take this problem from kaggle .This is time series  problem . in this problem, we have provided with historical sales data for 45 Walmart stores located in different regions. Each store contains many departments, and we have to predict  the sales for each department in each store.</br>
2. This data is collected regarding the type of customers and their preference regarding purchasing or buying of products ,sales rate at weekdays or weekends. All the types of Sales data is taken as input and we need to predict output of sales.</br>
3. This data is of supervised learning problem.in this output of sales is dependent on different input features of sales like store number ,department number, is_holiday, year ,months etc.the best feature is  that weekend holidays, months, store number etc. which involve the time series also.</br>
4.As this problem is time series problem, At a particular day sales will be different from another day ,so the model will be use as time series model like arena model, facebook prophet model or we can also use xgboost ,regressor, LGBM model etc.</br>
5. This model will help in prediction of sales at particular day of year so that they can keep their products according to sales.</br>
Dataset Introduction:</br>
In this problem we have given 3 csv file for training and one for testing.
Training CSV file introduction:
Stores.csv
This file contains anonymized information about the 45 stores, indicating the  type of store and size of the store.
Train.csv
This is the historical training data, which covers date from 2010-02-05 to 2012-11-01.In this file we have following features columns:
1.	Store - the store number
2.	Dept - the department number
3.	Date - the week
4.	Weekly_Sales -  sales for the given department in the given store
5.	IsHoliday - whether the week is a special holiday week
Features.csv
This file contains additional data related to the store, department, and regional activity for the given dates. It contains the following fields:
1.	Store - the store number
2.	Date - the week
3.	Temperature - average temperature in the region
4.	Fuel_Price - cost of fuel in the region
5.	MarkDown1-5 - anonymized data related to promotional markdowns that Walmart is running. MarkDown data is only available after Nov 2011, and is not available for all stores all the time. Any missing value is marked with an NA.
6.	CPI - the consumer price index
7.	Unemployment - the unemployment rate
8.	IsHoliday - whether the week is a special holiday week
We also have given some special holidays.we have given holiday name and their date :
Super Bowl: 12-Feb-10, 11-Feb-11, 10-Feb-12, 8-Feb-13
Labor Day: 10-Sep-10, 9-Sep-11, 7-Sep-12, 6-Sep-13
Thanksgiving: 26-Nov-10, 25-Nov-11, 23-Nov-12, 29-Nov-13
Christmas: 31-Dec-10, 30-Dec-11, 28-Dec-12, 27-Dec-13
Test datasets introduction:
Test.csv
This file is identical to train.csv, in this file we have given only three columns store, department, and date in this file.and we need to predict the sale .

Evaluation of problem:
This Problem is evaluated on the weighted mean absolute error (WMAE):
                  WMAE= 1 ∑ wi ∑ i = 1nwi |yi−y^i|
where
n is the number of rows
y^i is the predicted sales
yi is the actual sales
wi are weights. w = 5 if the week is a holiday week, 1 otherwise

________________________________________
Research-Papers/Solutions/Architectures/Kernels
*** Mention the urls of existing research-papers/solutions/kernels on your problem statement and in your own words write a detailed summary for each one of them. If needed you can include images or explain with your own diagrams. it is mandatory to write a brief description about that paper. Without understanding of the resource please don’t mention it**
1.	Visualization
a.	The above kernel is referred for visualization .
b.	 The visualization techniques like box plots, bar graphs, help us to find which column have maximum importance in modelling. These visualization techniques are well played key role in setting patterns of data
c.	For example : After plotting bar graph like monthly sales vs department , monthly sales vs store etc.  we found that month, store, department columns are very important features for modelling
d.	 Data cleaning part of the case study has prominent role. Referring the above Kernel is a great asset.

2.	Feature Engineering
https://www.kaggle.com/nitinx/storesales-randomforest-light-gbm-stacking
•	 The above kernel gave basic understanding regarding steps for feature engineering of   data .        
•	  I get some idea from this kernel like extracting year, month column from date. creating separate columns for holidays ,creating week by using date columns etc.
•	 I also get some important features from date like last 52 days sale ,mean sale, min sale ,max sale etc.
3.	Modelling
•	As we know this is time series problem ,below I mention some models.
•	I found that GBM model, light_GBM model, XGB regressor, random forest are good model for getting good accuracy in this problem
•	I used these algorithm because there parameter has been best fit for our data and giving best score that’s why I used this algorithm
4.	https://facebook.github.io/prophet/
https://www.youtube.com/watch?v=DpOwWuRoWro
•	The above link is referred as research paper and reference video for time series model.
•	This is facebook prophet model which made by Facebook for solving specially time series problem .This model will be helpful for getting good accuracy
•	According to model requirement we need only 2 columns of our data frame for training i.e. Date column and  sale columns .we need to rename the columns name.we need to change date column name into ‘ds’ and sale column in to ‘y’. 
•	Using ds and y columns ,we need to fit these two column in prophet model for training after that we can use our model for testing purpose
5. https://www.kaggle.com/simonstochholm/walmart-sales-forecast-gammel
1. The techniques of hyper parameter tuning is thought in classroom videos. 
2. The reference of the hyper parameter tuning is taken from assignments of supervised learning. 
3. The structure regarding the cs1 is taken from the kaggle kernel. 
4. The hyper parameter tuning structure used in case study had been inspired from the structure of kaggle kernel mentioned above. 
5. Getting of the best parameters is required for the giving best accuracy score.
First Cut Approach
*** Explain in steps about how you want to approach this problem and the initial experiments that you want to do. (MINIMUM 200 words) ***
1.Data Cleaning:
In this section the main function is to fill the gaps with mean or median value of the feature.This only applicable for non time series data. 

2.Feature Engineering:
Feature Engineering techniques like one hot encoding is applied to data columns of categorical values. It is applied for values such as IsHoliday, IsSuperbowl, IsLaborday etc.

3.DataVisualization: The data that got from feature engineering is visualized in this section. Visualizing the data gives best knowledge of the data that had been working with.
Data Visualization techniques like heatmap, bar charts, pie charts etc were used for the data visualization.

4.Machine Learning Models: In this section the machine learning models were introduced to data. The data used is a categorical data for that discere machine learning models
were used to train the data. Major machine learning models used were logistic regression, decision tree, random forest, xgboost algorithm etc.

5.Hyperparameter tuing: Different parameters were is used for the hyperparameter tuning. The model that gives best metric score for a set of parameters were noted to
train the data and apply for predictions.

6.Traing and prection on the model: With best hyperparameters and algorithm that noted in hyperparameter tuning is used to train the model and predict the values on the test data to 
give best metric score on unknow data.

Data Introduction

We are provided with historical sales data for 45 Walmart stores located in different regions. Each store contains a number of departments, and  tasked with predicting the department-wide sales for each store.

The main metric is weighted mean absolute error (WMAE)
WMAE= 1 ∑ wi ∑ i = 1nwi |yi−y^i|
where
n is the number of rows
y^i is the predicted sales
yi is the actual sales
wi are weights. w = 5 if the week is a holiday week, 1 otherwise

