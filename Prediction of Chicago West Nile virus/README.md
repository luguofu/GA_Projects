# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 4: West Nile Virus Prediction

### Background

West Nile virus (WNV) is the leading cause of mosquito-borne disease in the continental United States. It is most commonly spread to people by the bite of an infected mosquito. Cases of WNV occur during mosquito season, which starts in the summer and continues through fall. There are no vaccinesto prevent or medications to treat WNV in people. By the end of 2002, Illinois (Chicago's state) had counted more human cases (884) and deaths (64) than any other state in the United States. [`CDC Website`](https://www.cdc.gov/westnile/index.html)

One of the methods which the Chicago Department of Public Health (CDPH) deploy to protect residents against West Nile virus is by spraying pesticides to kill adult mosquitoes. In addition to spraying, each year CDPH conducts a comprehensive mosquito surveillance program, which includes placing larvacide incatch basins to limit the number of mosquitoes that can carry the virus, and trapping mosquitoes throughout the city and testing them for West Nile virus for studies. [`Chicago Government Website`](https://www.chicago.gov/city/en/depts/cdph/provdrs/healthy_communities/news/2020/august/city-to-spray-insecticide-thursday-to-kill-mosquitoes0.html)



### Problem Statement

As pesticides are expensive to deploy throughout the city, CDPH has contracted our data scientist team to leverage their data to develop a classification model that could predict the presence of WNV. With this model, CDPH hopes to create a effective and efficient strategy of deploying targeted spraying of pesticides in Chicago


### Datasets

The following four datasets were provided and can be downloaded from  [`Kaggle data`](https://www.kaggle.com/c/predict-west-nile-virus/data):

- Weather records (2,944 rows) from 2007-05-01 to 2014-10-31
- Spray records (14,835 rows) for 2011 and 2013
- Training records (10,506 rows) for year 2007,2009,2011,2013
- Testing records (116,293 rows) for year 2008,2010,2012,2014 (this will be used for kaggle submission)

### Data Dictionary

|Feature|Type|Dataset|Description|
|---|---|---|---|
|Id            |int      |train.csv/test.csv |ID number of the record
|Date           |datetime      |train.csv/test.csv |date the WNV test is performed
|Address      |datetime |train.csv/test.csv| approximate trap address; sent to GeoCoder
|Species         |str      |train.csv/test.csv| mosquito species in trap
|Block         |str      |train.csv/test.csv| block number of address
|Street        |str      |train.csv/test.csv| street of address
|Trap          |str    |train.csv/test.csv| ID number of the trap
|AddressNumberAndStreet|str|train.csv/test.csv| approximate address retrieved from GeoCoder
|Latitude            |float|train.csv/test.csv| latitude retrieved from GeoCoder
|Longitude            |float|train.csv/test.csv| longitude retrieved from GeoCoder
|AddressAccuracy      |int|train.csv/test.csv| accuracy of information returned from GeoCoder
|NumMosquitos        |int      |train.csv/test.csv| number of mosquitoes in a sample
|WnvPresent           |int      |train.csv/test.csv| whether or not WNV is present in a sample (1 = present; 0 = absent)
|Date |datetime |spray.csv| date of spray
|Time         |datetime      |spray.csv| time of spray
|Latitude|float|spray.csv| latitude of spray
|Longitude        |float|spray.csv| longitude of spray
|Station  |int|weather.csv| weather station (1 or 2)
|Date     |datetime|weather.csv| date of measurement
|Tmax     |int|weather.csv| maximum daily temperature (F)
|Tmin     |int|weather.csv| minimum daily temperature (F)
|Tavg  |int|weather.csv| average daily temperature (F)
|Depart     |int|weather.csv| departure from normal temperature (F)
|Dewpoint    |int|weather.csv| average dewpoint (F)
|WetBulb  |int|weather.csv| average wet bulb
|Heat     |int|weather.csv| heating degree days
|Cool  |int|weather.csv| cooling degree days
|Sunrise     |int|weather.csv| time of sunrise (calculated)
|Sunset     |int|weather.csv| time of sunset (calculated)
|CodeSum     |str|weather.csv| code of weather phenomena 
|Depth     |int|weather.csv| unknown
|Water1  |int|weather.csv| unknown
|SnowFall     |int|weather.csv| snowfall (inch)
|PrecipTotal     |str|intweather.csv| total daily rainfall (inch)
|StnPressure     |int|weather.csv| average atmospheric pressure (inch Hg)
|SeaLevel     |int|weather.csv| average sea level pressure (inch Hg)
|ResultSpeed  |float|weather.csv| resultant wind speed (mph)
|ResultDir     |int|weather.csv| resultant wind direction (degrees)
|AvgSpeed     |int|weather.csv| average wind speed (mph)

### Summary of Analysis

During the initial EDA analysis, we noted and took actions for the following:

1. Weather Dataset:
	- There are some null values in both weather stations. We make use of the other weather station to impute null values as both stations are in 	 Chicago city and thus should have rather similar weather conditions that will not vary drastically. For the rest of the null values, we impute using the next day weather condition.
	- Removing features that are not required, highly correlated or with too many null values. Creating additional features such as relative humidity and weekly averages for the various weather conditions. [`Factors affecting breeding mosquitoes`](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4342965/)

2. Training Dataset:
	- Create 1 week and 2 week average lagging weather conditions as  it takes 7-10 days for an egg to develop into an adult mosquito. [`Life Cycle of Culex Species Mosquitoes`](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4342965/)
	- Removed duplicates in the training data
	- Converting the species to % of WNVPresent/total mosquitoes in each species as some species has higher probability of having WNV (not all types of mosquitoes carry WNV).
	- As some months has higher number of mosquitoes due to seasonlity, we mapped the month to the % of number of mosquitoes/ total mosquitoes.
	- Merged train data with weather data to obtain the weather conditions.
	- Create clusters using latitude and longitude and dropped all location features
	- Create dummy variables for trap and clusters
	- Unbalanced classification dataset which we will account for when fitting the model
	

As the variables are of different scale, we use minmaxscaler to standardise all the variables. We created the following 2 models for evaluations:

1. Logistic Regression: To account for unbalance dataset, we used SMOTE before fitting the model. We used gridsearch to select the best hyperparameters

2. RandomForest Classifier: To account for unbalance dataset, we used 'balance' weightage which uses the values of y to automatically adjust
    weights inversely proportional to class frequencies in the input data. We used gridsearch to select the best hyperparameters.
	

### Conclusion

As this is data classification set is highly unbalanced, we should not be using accuracy to evaluate model. Thus, we select RandomForestClassifier as it has the higher test_auc score,recall and fscore.

Based on the train accuracy vs test accuracy(accuracy variance), we can see that logistic regression is slightly overfitted and thus will not generalised well as compared to the RandomForestClassifier which has almost the same train and test accuracy. We also placed higher emphasised on recall as there are higher cost of not identifying WNV present (hospitalisation and social cost of citizens being affected by WNV) than wrongly identifying WNV present (cost of additional spraying of pesticides) in the area.

### Business Case

Cost Benefit Analysis with and without predictive model:

|Type|Total Cost|Total Benefit|Net Cost/(benefit)|
|---|---|---|---|
|Without Model            |US$501,830     |US$263,151 |US$238,679
|With Model          |US$146,999     |US$231,573 |(US$84,574)
|Net Savings          |    ||US$323,253

Without Model Assumption:

**Cost**: Spray pesticides for the whole of Chicago every month for 5 months from April to October as they are the peak season for mosquitoes.

**Benefit**: Taking the largest WNV cases in Chicago, it is 225 cases in 2002. We multiply the number of cases with the average treatment and implicit cost per person. We assume no cases if the whole chicago is sprayed.

[`Cost of Pesticides`](https://www.centralmosquitocontrol.com%2F-%2Fmedia%2Ffiles%2Fcentralmosquitocontrol-na%2Fus%2Fresources-lit%2520files%2Fzenivex%2520cost%2520comparison%2520fact%2520sheet.pdf&usg=AOvVaw2oqR8C3sxugwE2lvyIq-I1)

[`Recommended spray frequency`](https://www.callnorthwest.com/2019/05/how-long-does-a-mosquito-treatment-last/)

[`Mosquitoe Season`](https://www.callnorthwest.com/2019/05/how-long-does-a-mosquito-treatment-last/)

[`Average treatment and implicit cost per person`](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3322011/)

[`Largest WNV cases in Chicago`](https://www.chicago.gov/content/dam/city/depts/cdph/statistics_and_reports/CDInfo_2013_JULY_WNV.pdf)

With Model Assumption:

**Cost**: Cost of spraying pesticides at predicted area + treatment cost of WNV cases for areas the model missed out

**Benefit**: We assume that the reduction in cases is by the percentage of correctly predicted area with WNV present.(recall) 

From the calculation, the total saving is estimated to be around US$323,253 by using prediction model to spray selective areas in Chicago. We can also see from the graph that if we spray selective areas with predictive model, the total benefit outweights the costs, and makes it worthwhile to conduct the spray exercise.

#### Links:
1. [`Google Co-lab`](https://colab.research.google.com/drive/1DqYGpvpRRNNQPLh0-kXvD7RBpym8bC8d?usp=sharing#scrollTo=ca1c6d86)
2. [`Trello for Project Management`](https://trello.com/b/bnei7fte/project-space)
