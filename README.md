# yelp-business-performance

## Purpose of project

The purpose of this project is to create a machine learning model that can predict a restauant's star rating based on its features it provides. Currently, yelp success is measured through star ratings which ranges from 1 to 5 stars.

## Business Problem

There are many existing restaurants as well as new restaurants that understand the importance of having a good reputation. In this day in age, online reviews are the main source of reasoning for customers to make their decsions. Yelp is one of the biggest platforms for restaurant reviews in the form of star rating and text comments. A business would like to know what features offered as a restaurant will allow them to have an idea of what star rating they would get or if they would perform well. This would add value because the respective business could see what features they should change and how they can keep their reputation as high as possible. Currently, as businesses can check how well they are doing by going on the app but they are not able to see where they could potentially be based on adding some features. Their current reviews may also be skewed due to number of reviews, surrounding area, and competition. 

## File Structure
<img width="485" alt="image" src="https://user-images.githubusercontent.com/96553992/228005169-37e2eece-5586-4c53-ad68-2c4e34b2ce49.png">


## The Data and Cleaning 
The majority of the data in this project comes from the [Yelp's business, reviews, and users subset data](https://www.kaggle.com/datasets/yelp-dataset/yelp-dataset?datasetId=10100&language=Python&outputs=null) extracted from Kaggle. 
 - The original raw data contains information across diffierent areas in USA and Canada. For this project, the Yelp business table was best suited for creating a model as it contained information pertaining to what attributes the business had.
 - The data was last updated on February 16, 2021
 
 
 The other data source that was used was US Census data filtered by state, income, and total household. Taken from [Census.gov](https://data.census.gov/cedsci/table). This dataset ended up having about 9,045 records.
 
 - A left join in pandas had to be done to merge the business data with the census data through postal code. This allowed for a unique dataset to clean and analyze.
 - After filtering and cleaning the data, the total records of businesses left were 44,582 with a total of 39 columns. Of those 39 columns, 34 of them are attributes and the other 5 are of census income data

 - Examples of important attributes:

   - Open Monday
   - Restaurant delivery
   - WiFi
   - Alcohol served
   - Noise level
   - DrivThru
   - Wheel chair accessible

- Examples of income columns:
   - Total_Estimate_Households_per_Zip
   - Total_Estimate_Married-couple_Family_households
   - Median_Income(dollars)


## Exploratory Data Analysis

Various graphs and attributes were plotted to identify any themes througout the data and what key takeaways can be intepreted before expanding on the machine learning models. Some interesting insights that can be derived from the data are below.

- The distribution of the star ratings of the data is essential to understanding what our data looks like a whole.
 ![image](https://user-images.githubusercontent.com/96553992/226778761-234ce816-4287-4e21-88d4-5c05ac409f37.png)


 

- Out of the most common ethnic foods in the data, Mexican cusine is most prevalent while Korean is least present in the data.
![image](https://user-images.githubusercontent.com/96553992/224855332-723a5e15-232f-472c-82e2-44549af10460.png)

- Average star rating per ethnic food is highest for Korean cusine, followed by Indian.
![image](https://user-images.githubusercontent.com/96553992/224855648-ed11b96e-5dfe-4f71-ac5d-bd748b8b514a.png)

- Based on ethnic foods, restaurant delivery for Italian and Mexican food is the highest in comparative to the other ethnic foods. It can be understood that majority of places deliver.
 ![image](https://user-images.githubusercontent.com/96553992/224856375-455716a2-db28-44a2-b796-4a4b3926734a.png)

- There are ethnic foods in each state but how much and what is the proportion? Below is a graph that shows the distribtion
 ![image](https://user-images.githubusercontent.com/96553992/224856636-ce74a6ba-7e1e-4e7f-9356-101b3f4839c3.png)

- When it comes to being open on a Monday, how do restaurants perform on average in each state? Below is a graph that describes that relationship throughout the data 
 ![image](https://user-images.githubusercontent.com/96553992/224856801-833bc2fe-89d6-4c42-9a5d-f1a5f8bb6592.png)
 - Comparitvely, what is the performacne of restaraunts in each state that are open or not on weekends? Below is graph that describes that relationship
 ![image](https://user-images.githubusercontent.com/96553992/224857035-553bb338-c67c-42e7-b989-142d2706b177.png)

These were just some of the important high level insights of what the data consisits of and what patterns occur. The rest of the code can be seen [here](https://github.com/hbustamante8/yelp-business-performance/blob/main/exploratory_data_analysis.ipynb)


## Machine Learning Models

 ### Preparing the data for machine learning
 After taking the clean data dataset, there was still a few more steps to put the data through different machine learning models. Dropping non-numericla columns as well as taking out 'XMS' and 'HI' state as there were only 1-2 records for each of these and could potentially throw off the model based on using dummy variables. The data was separated into two different sets that can be used for machine learning. One set is dropping the state and city columns ( X_no_city_state,y_no_city_state ) while the other one kept them and dummy variables were made fore the respective columns and filtered for cities with over 50 samples (X_filtered,y_filtered) to keep the data as valuable as possible for machine learning. 
 
 
 ### Models tested
- Linear Regression
  - The first model tested was linear regression for both the data sets. Five fold cross validation was used to validate the performance of the models.The dataset with (X_filterred,y_filtered) performed better in this case slightly. The mean accuracy score was 26.26% compared and standard deviation was .009 between the 5 different accuracy scores.
 
 - XG Boost Model
   - Secondly, this was model was chosen as it is scalable and highly accurate implementation of gradient boosting. Five fold cross validation was used to validate the performance of the models.The dataset with (X_filterred,y_filtered) performed better in this case slightly. The mean accuracy score was 36.16% and standard deviation was .001 between the 5 different accuracy scores. The (X_no_city_state,y_no_city_state) dataset performed at a close 35.96%.

- Neural Network Model
  - Finally, Neural Networks were chose to learn complex and non-linear relationships in the yelp data. Five fold cross validation was used to validate the performance of the models.The dataset with (X_filterred,y_filtered) performed better in this case by a very fine margin. The mean accuracy score was 26.68% and standard deviation was .044 between the 5 different accuracy scores. The (X_no_city_state,y_no_city_state) dataset performed at a close 25.96%.

 ## Tuning the XG Boost Model
 Since the XG Boost Model perfomed the best out of all 3 models tested, I tuned the paramaters of the model to increase the performance. Specifically, I chose the to tune the model for X_filterred,y_filtered since it peformed best out of all models tested. Below are the parameters I tuned within the model through testing different values for each respective parameter.
 
 - List of paramters tuned
     - Learning rate
     - max_depth
     - min_child_weight
     - gamma
     - subsample
     - colsample_bytree
     - reg_alpha
     - reg_lambda
     - n_estimators
     
  After finding the optimal parameters throught the testing, I then ran the XG Boost Model again with these updated values. The accuracy score increased by about 1.5% which is indicated the tuning had a signicant impact. Previously the model was getting an accuracy of about 36% and now the score improved to almost 38%. 
  
  ## Conclusion
  
  
