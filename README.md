D(S)treams of Anomalies
==============================

Anomaly detection on real world data sets

Project Organization
------------


    ├── data
    │   └── raw   
    │        │── speed data
    │        │── travel time data
    │        └── nyc taxi data
    │
    ├── notebooks          
    │   └── src.ipynb               


Data
----
The data that we are using here is really simple. We are given a bunch of random data sets that come 
from real world data collection. We're just getting the timestamp and value in each row and our goal is 
to find outliers in this data. The 3 datasets that I looked at were Michigan speed data, travel time data, 
and nyc taxi data. The speed and travel time data was just a bunch of values collected from sensors in a 
study from the Michigan Department of Transportation. The nyc taxi data set is one that has some known 
outliers. These aren't marked in the data set, however, they are just known as events that happen throughout 
the year when there are an unusually large number of taxi users. These events include labor day, nyc marathon, 
Christmas, and others.

Feature Engineering
-------------------
I didn't really have anything to do here for feature engineering. All of the data sets are just a single value
time series that represents one thing. There probably would be something to do in the nyc taxi data set if we
were looking at multiple years. In the readme of the data source it mentions that there are some know outliers. 
These are the events that I talked about above in the explanation of the data. If we really wanted to, we could 
go through and mark these specific events as outliers and then train on this data. We would then be able to use
this model to predict outliers from data in other years

Anomaly Algorithms
----------------------

I used the isolation forest and local outlier factor models to find anomalies. I used the sklearn implementation
of these algorithms. I had some trouble working with the isolation forest model. I wasn't exactly sure how the 
paramaters max_samples and n_estimators influenced the output. I was getting an extremely high percentage of the 
samples classified as outliers when I was running this algorithm. From class, we talked about how this algorithm 
builds a forest of random trees and finds anomalies by recognizing paths that are extraordinarily short. I'm not 
sure exactly how to think about this in one variable, or really how these two paramaters that I was researching 
influenced the model. I had much more luck with the local outlier factor model. I used local outlier factor on 
the nyc taxi dataset and was able to find most of the outliers mentioned in the readme of the data set. This algorithm
looks at the density of clusters and measures the distance of points from a cluster. An anomaly is a point that is
very far from a cluster. 