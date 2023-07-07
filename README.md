# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 4: Data-backed solutions for combating West Nile Virus in Chicago

<!-- ### **Try Out our B99 vs BBT Classifier Application Streamlit App by clicking the link below.**
### [Brooklyn's Nine Nine and The Big Bang Theory Classifier and Sentiment Analysis](https://project-3-recipe-for-comedy-success-tj0ysfqfwsi.streamlit.app/) -->

<br>

<!-- | **Brooklyn's Nine Nine** | **The Big Bang Theory**  |
| ------------------------ | -----------------------  |
| ![Brooklyn's Nine Nine](https://github.com/khammingfatt/Project-3-Quantifying-TV-Laughter/blob/main/B99_Image.jpg?raw=true)| ![The Big Bang Theory](https://github.com/khammingfatt/Project-3-Quantifying-TV-Laughter/blob/main/BBT_Image.jpg?raw=true) | -->

<br>

## Content Directory:
- [Background](#Background)
- [Data Import & Cleaning](#Data-Import-&-Cleaning)
- [Preprocessing and Feature Engineering](#Preprocessing-and-Feature-Engineering)
- [Exploratory Data Analysis](#Exploratory-Data-Analysis)
- [Modeling](#Modeling)
- [Kaggle Submission](#Kaggle-Submission)
- [Key Insights & Recommendations](#Conclusion)

<br>


## Background
West Nile virus (WNV) is an infectious viral disease transmitted by mosquitoes, which can lead to flu-like symptoms, neurological complications, and potentially fatal illnesses in humans.

In the year 2002, the initial human cases of West Nile virus were reported in the city of Chicago. Subsequently, the City of Chicago and the **Chicago Department of Public Health (CDPH)** took significant measures to establish a comprehensive surveillance and control program. This program has been diligently maintained and remains in operation to this day. Over the course of 12 years, substantial efforts have been invested in combating the spread of West Nile Virus, resulting in the accumulation of a vast amount of data by the **CDPH**. This rich dataset now serves as a valuable resource for making evidence-based decisions.

Reference Website
- [Centre for Disease Control and Prevention](https://www.cdc.gov/about/index.html)
- [Chicago Department of Public Health](https://www.chicago.gov/city/en/depts/cdph.html)

<br>


## Problem Statement
We, **Data Nine-Nine**, have been engaged as a third-party consulting firm by the **Centre for Disease Control and Prevention (CDC)** to collaborate on a comprehensive review of their West Nile virus (WNV) control efforts. Our objective is to

	(1) build machine learning model to predict the presence of WNV; 

	(2) providing valuable insights and recommendations to further enhance their strategies 
<br>

in combatting the West Nile virus outbreak.

<br>

## Project Deliverables
Our project is centered around the following objectives:

1. Conduct comprehensive **research** on the occurrence and prevalence of the West Nile virus in the city of Chicago.
2. Develop and **train a machine learning model** capable of accurately predicting the probability of the presence of the West Nile virus.
3. Share our **insights and recommendations** with the esteemed members of the Centers for Disease Control and Prevention (CDC), including biostatisticians and epidemiologists.
4. Provide a thorough **cost-benefit analysis** to support the CDC members in making informed decisions based on data-driven recommendations for the future.

Project management and planning documentation is done via Github Projects here: https://github.com/users/khammingfatt/projects/1/views/1

<br>

---

## Datasets:
Public health workers in Chicago setup mosquito traps scattered across the city. The captured mosquitos are tested for the presence of West Nile virus.

* [`train.csv`](../assets/train.csv): The "train.csv" dataset comprises information regarding the geographical coordinates of mosquito traps, the count of mosquitos captured in each trap, and the presence or absence of the West Nile Virus. The dataset encompasses data collected during the years 2007, 2009, 2011, and 2013.

* [`test.csv`](../assets/test.csv): The "test.csv" dataset comprises information regarding the geographical coordinates of mosquito traps and the count of mosquitos captured in each trap. The dataset encompasses data collected during the years 2008, 2010, 2012, and 2014. We are to use test.csv to evaluate the results of machine learning.

* [`spray.csv`](../assets/spray.csv): The spray.csv consists of GIS data for City of Chicago spray efforts in 2011 and 2013. 

* [`weather.csv`](../assets/weather.csv): The weather.csv consists of weather condition data collected by National Oceanic and Atmospheric Administration (NOAA) from year 2007 to 2014.

<br>

### Brief Description of Our Data Exploration

 
<!-- ![SHAP Importance of Variables](https://github.com/khammingfatt/Project-3-Quantifying-TV-Laughter/blob/main/SHAP.png?raw=true)
<br> -->

<!-- We went further and break down the important features to classify the two shows separately and here are the details we get. The more positive the coefficient values, the more likely it is classified to Class 1 - Brooklyn's Nine Nine; On the other hand, the more negative the coefficient values, the more likely it is classified to Class 0 - The Big Bang Theory. -->

<br>

<!-- | **Brooklyn's Nine Nine** | **The Big Bang Theory**  |
| ------------------------ | -----------------------  |
| ![Brooklyn's Nine Nine](https://github.com/khammingfatt/Project-3-Quantifying-TV-Laughter/blob/main/Feature%20Importance%20B99.png?raw=true)| ![The Big Bang Theory](https://github.com/khammingfatt/Project-3-Quantifying-TV-Laughter/blob/main/Feature%20Importance%20BBT.png?raw=true) | -->

<br>

## Data Dictionary
| Feature                   | Type    | Dataset                       | Description                                 |   
|---------------------------|---------|-------------------------------|---------------------------------------------|
| year                      | integer | train_merge_df, test_merge_df | Year that the WNV test is performed         |   
| month                     | integer | train_merge_df, test_merge_df | Month that the WNV test is performed        |   
| day                       | integer | train_merge_df, test_merge_df | Day of month that the WNV test is performed |   
| week                      | integer | train_merge_df, test_merge_df | Week that the WNV is performed              |   
| dayofweek                 | integer | train_merge_df, test_merge_df | Day of week that the WNV is performed       |  
| dayofyear                 | integer | train_merge_df, test_merge_df | Day of year that the WNV is performed       |   
| address                   | object  | train_merge_df, test_merge_df | Approximate address of the location of trap. This is used to send to the GeoCoder.  |   
| species                   | object  | train_merge_df, test_merge_df | Species of mosquitos                        |   
| block                     | integer | train_merge_df, test_merge_df | Block number                                |   
| street                    | object  | train_merge_df, test_merge_df | Street name                                 |   
| trap                      | object  | train_merge_df, test_merge_df | Id of the Mosquito trap                         |   
| address_number_and_street | object  | train_merge_df, test_merge_df | Address number and street name              |   
| latitude                  | float   | train_merge_df, test_merge_df | Latitude returned from GeoCoder                   |   
| longitude                 | float   | train_merge_df, test_merge_df | Longitude returned from GeoCoder            |   
| address_accuracy          | integer | train_merge_df, test_merge_df | Accuracy returned from GeoCoder      |   
| wnv_present               | integer | train_merge_df                | Whether West Nile Virus was present in these mosquitos. 1 means WNV is present, and 0 means not present.     |   
| num_mosquitos             | integer | train_merge_df                | Number of mosquitoes caught in this trap |   
| station                   | integer | train_merge_df, test_merge_df | Weather station number                     |   
| stat_1_tmax               | integer | train_merge_df, test_merge_df | Max temperature at Station 1                      |   
| stat_1_tmin               | integer | train_merge_df, test_merge_df | Min temperature at Station 1             |   
| stat_1_tavg               | float   | train_merge_df, test_merge_df | Average temperature at Station 1                |   
| stat_1_precip_total       | float   | train_merge_df, test_merge_df | Total precipitation at Station 1           |   
| day_length_mprec          | float   | train_merge_df, test_merge_df | Day duration in minutes                      |  
| day_length_nearh          | float   | train_merge_df, test_merge_df | Day duration in hours             |   
| sunrise_hours             | float   | train_merge_df, test_merge_df | Sunrise timing in hours                    |   
| sunset_hours              | float   | train_merge_df, test_merge_df | Sunset timing in hours                     |   
| yearweek                  | integer | train_merge_df, test_merge_df | Week number of the year                     |   
| weekpreciptotal           | float   | train_merge_df, test_merge_df | Weekly total precipitation                    |   
| weekavgtemp               | float   | train_merge_df, test_merge_df | Weekly average temperature                       |   
| r_humid                   | integer | train_merge_df, test_merge_df | Relative humidity                        |   
| templag1                  | float   | train_merge_df, test_merge_df | Temperature, lagged by 1 week (brought forward) |   
| templag2                  | float   | train_merge_df, test_merge_df | Temperature, lagged by 21 weeks (brought forward) |   
| templag3                  | float   | train_merge_df, test_merge_df | Temperature, lagged by 3 weeks (brought forward) |   
| templag4                  | float   | train_merge_df, test_merge_df | Temperature, lagged by 4 weeks (brought forward) |   
| rainlag1                  | float   | train_merge_df, test_merge_df | Rainfall, lagged by 1 week  |   
| rainlag2                  | float   | train_merge_df, test_merge_df | Rainfall, lagged by 2 weeks  |   
| rainlag3                  | float   | train_merge_df, test_merge_df | Rainfall, lagged by 3 weeks   |   
| rainlag4                  | float   | train_merge_df, test_merge_df | Rainfall, lagged by 4 weeks            |   
| humidlag1                 | float   | train_merge_df, test_merge_df | Relative humidity, lagged by 1 week  |   
| humidlag2                 | float   | train_merge_df, test_merge_df | Relative humidity, lagged by 2 weeks  |  
| humidlag3                 | float   | train_merge_df, test_merge_df | Relative humidity, lagged by 3 weeks   |   
| humidlag4                 | float   | train_merge_df, test_merge_df | Relative humidity, lagged by 4 weeks     |  
| mixed_tmax                | float   | train_merge_df, test_merge_df | The mean maximum temperature from both weather stations |   
| mixed_tmin                | float   | train_merge_df, test_merge_df | The mean minimum temperature from both weather stations |   
| mixed_precip_total        | float   | train_merge_df, test_merge_df | The mean maximum temperature from both weather stations |   
| mixed_weekpreciptotal     | float   | train_merge_df, test_merge_df | The mean weekly total precipitation from both weather stations |   
| mixed_weekavgtemp         | float   | train_merge_df, test_merge_df | The mean weekly average temperature from both weather stations  |   
| mixed_r_humid             | float   | train_merge_df, test_merge_df | The mean relative humidity from both weather stations |   
| stat_2_tmax               | integer | train_merge_df, test_merge_df | Max temperature at Station 2  |   |
| stat_2_tmin               | integer | train_merge_df, test_merge_df | Min temperature at Station 2   |   
| stat_2_tavg               | float   | train_merge_df, test_merge_df | Average temperature at Station 2    | 
| stat_2_precip_total       | float   | train_merge_df, test_merge_df | Total precipitation at Station 2      |  
| id                        | integer | test_merge_df                 | The ID of the record                        |  
| Date |datetime |spray_df|  Date of the spray|
| Time |object|spray_df| Time of the spray|
| Latitude|float|spray_df| Latitude of the spray|
| Longitude|float|spray_df| Longitude of the spray|



---

<br>
<br>

## Modeling

We followed a rigorous data preprocessing pipeline consisting of three key steps. Firstly, we employed the **One Hot Encoder** technique to convert categorical data into **numerical format**, ensuring compatibility with our models. This transformation allowed us to effectively capture the information contained within the categorical variables.

Next, we applied the **Synthetic Minority Oversampling Technique (SMOTE)** to balance the target class distribution, aiming for a **50:50 ratio**. By oversampling the minority class, we addressed the issue of class imbalance and improved the performance of our models in handling the target variable.

In the final step of data preprocessing, we utilized the **Standard Scaler** method. This process involved transforming all features within the dataset to a **similar scale and distribution**. By doing so, we minimized the potential impact of varying feature magnitudes, allowing our models to better understand the relative importance of different features during the classification process.

Following the data preprocessing stage, the preprocessed dataset was fed into a pipeline of five classification models: **logistic regression, random forest classifier, XGBoost, Adaboost, and Voting Classifier**. These models were carefully chosen based on their respective strengths and suitability for the classification task at hand. The use of multiple models allowed us to leverage their individual capabilities and ensemble them to make more robust predictions.

By employing this systematic approach, we aimed to enhance the quality and reliability of our classification results, enabling us to make informed decisions based on the predictions generated by the ensemble of models.


<br>
<br>

## Summary of Model Perforamance

|  | TPR<sup>1</sup> | TNR<sup>2</sup> | ROC(Train) | ROC(Test) | Kaggle<sup>3</sup> |
|---|---|---|---|---|---|
| **Logistic Regression <br>(Baseline Model)** | 0.7802 | 0.7419 | 0.8670 | 0.8269 | 0.7559 |
| **Random Forest Classifier** | 0.8352 | 0.7069 | 0.8597 | 0.8552 | 0.7334 |
| **XGBoost Classifier** | 0.1319 | 0.9853 | 0.9238 | 0.8733 | 0.7837 |
| **AdaBoost Classifier** | **0.7253** | **0.8124** | **0.8259** | **0.8564** | **0.7680** |
| **Voting Classifier** | 0.6703 | 0.8443 | 0.8987 | 0.8645 | 0.7846 |

<br>
1 - True Positive Rate or Sensitivity.

2 - True Negative Rate or Specificity.  
3 - Public Score on Kaggle.com (AUC)


---

<br>




<!-- ## Key Insights
### Overall 
* Viewers frequently engage in discussions about popular show elements such as Cold Open, Halloween Heist, and potential sequels.
* Topics that garner significant attention from viewers include their favorite characters and least favorite scenes.
* Viewers actively discuss sitcom characters in their comments about the shows. 

### Brooklyn's Nine Nine
* 'Scene' is commonly mentioned in Brooklyn's Nine Nine
* 'Halloween' and 'Heist' is identified as a very popular topic among reddit users
* 'Cold Open' is identified as a unique X-factor of B99

### The Big Bang Theory
* ‘Sheldon’ has very strong impact on viewers in the show
* 'Season' is commonly mentioned in Big Bang Theory
* ‘Young’ is seen on BBT very often due to sequel of Young Sheldon -->



## Key Recommendations
 
	(1) Create memorable and likable characters to enhance viewer engagement.
	(2) Utilize the "Cold Open" narrative technique, which is widely discussed by viewers.
	(3) Incorporate periodic special events within the show to generate anticipation and excitement among viewers. 

<!-- ## Future Work
	(1) Model can be expanded to Multi-Class Classification
	(2) Further collect text inputs from other sources periodically
	(3) To analyse further sentiments, we will no longer limit the number of posts to be even -->

---
<!-- ## Reference
(1) The source of data for comments and posts for Brooklyn's Nine Nine <br>
https://www.reddit.com/r/brooklynninenine/

(2) The source of data for comments and posts for The Big Bang Theory <br> https://www.reddit.com/r/bigbangtheory/

(3) Preferred digital video content by genre in the U.S. as of March 2023
<br> https://www.statista.com/forecasts/997166/preferred-digital-video-content-by-genre-in-the-us#:~:text=%22Comedies%22%20and%20%22Dramas%22,the%20United%20States%2C%20in%202023

(4) Importance of Video Streaming Attributes
<br> https://www.nielsen.com/insights/2020/playback-time-which-consumer-attitudes-will-shape-the-streaming-wars/

(5) Reasons for Subcribing to Additional Paid Video Streaming Services
<br>  https://www.nielsen.com/insights/2020/playback-time-which-consumer-attitudes-will-shape-the-streaming-wars/

(6) Most Attractive Features of Video Streaming Service
<br> https://www.cloudwards.net/streaming-services-statistics/

(7) Top Reasons to Subscribe to a New Streaming Service
<br> https://www.cloudwards.net/streaming-services-statistics/

(8) Streaming Industry Digital Market Share
<br> https://www.similarweb.com/blog/insights/media-entertainment-news/streaming-q1-2023/#:~:text=The%20streaming%20industry%20has%20shown,in%20a%20post%2Dpandemic%20world

(9) Singaporeans Asked if They Would Discontinue Their Current Streaming Services in The Next 6 Months.
<br> https://blackbox.com.sg/everyone/streaming-services-in-singapore -->
