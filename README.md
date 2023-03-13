# yelp-business-performance

## Purpose of project

The purpose of this project is to create a machine learning model that can predict a restauant's star rating based on its features it provides. Currently, yelp success is measured through star ratings which ranges from 1 to 5 stars.


## The Data
The data in this project comes from the [Yelp's business, reviews, and users subset data](https://www.kaggle.com/datasets/yelp-dataset/yelp-dataset?datasetId=10100&language=Python&outputs=null) extracted from Kaggle. 
 - The original raw data contains information across diffierent areas in USA and Canada. For this project, the Yelp business table was best suited for creating a model as it contained information pertaining to what attributes the business had.
  The data was last updated on February 16, 2021
 - After filtering and cleaning the data, the total records of businesses left were 44,482 with a total of 34 columns that consist of attributes. 

 - Examples of important attributes:

   - Open Monday
   - Restaurant delivery
   - WiFi
   - Alcohol served
   - Noise level
   - DrivThru
   - Wheel chair accessible


## Exploratory Data Analysis

Various graphs and attributes were plotted to identify any themes througout the data and what key takeaways can be intepreted before expanding on the machine learning models. Some interesting insights that can be derived from the data are below.

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

