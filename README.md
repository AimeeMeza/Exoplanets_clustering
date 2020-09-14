# Project: Exoplanets clustering

## Overview

This project aims to get clusters of the exoplanets downloaded of the NASA API database and see what cluster the Earth enters and compare the similar planets.
Using machine learning methods, i run different models to obtain the best silhouette score and analyze each cluster's exoplanets features.

---

## Technical Requirements

The technical requirements for this project are as follows:

* Get the data in NASA API website:  https://exoplanetarchive.ipac.caltech.edu/cgi-bin/TblView/nph-tblView?app=ExoTbls&config=PSCompPars

*Understand the definitions of every column: https://exoplanetarchive.ipac.caltech.edu/docs/API_PSCompPars_columns.html

*Have python and the libraries that are  at the beginning of the notebook

## Presentation with conclusions: 

https://docs.google.com/presentation/d/1iwrWG_tqWxk3M9sj5Hk_Bc0PFiozNSKz499cAgq4Yf8/edit?usp=sharing

## Process 

* Import the data: 
    * I have to import two different datasets because the first dataset has categorical columns and only has continuous data in the second dataset.
    *I have the same rows that are exoplanets and merge this to datasets
    
* Explore the data and understand the meaning of the columns to keep only the most important

* Data cleaning:
    * Delete columns and rows with many Nan values
    * One hot encoding for some columns
    * Delete columns with a high correlations
    
* Feature engineering for mixed data:
    * We have to upload other data with the columns that have been conserved and add the earth data that i searched with also, the Trappist exoplanets data was removed when we do the data cleaning.
    
    * Divide the data frame in two:
        * Categorical columns: Reduce dimension only to have two representative columns and add to the continuous data
        * Continous data: Normalize the data to the same dimensions
        * Merge this data: First data frame to model
        * Get another data frame, but the continuous data don't have to be normalized because some models don't need it.
        * Merge this data without normalized, and the reduced dimension of the categorical data
        
     * Divide the 2 data frames in 5:
        * df_scaled_train: data with the constant data scaled and PCA dimensions to train models
        * df_normal_train: data without the constant data scaled and with PCA dimensions to train models
        * df_scaled_test: data with the continuous data scaled and PCA dimensions to test models only Earth.
        * df_normal_test: data without the continuous data scaled and with PCA dimensions to test models only Earth.
        * df_normal_all: this for some models that cant predict with one row. 
        
* Run Models:
    * DBSCAN: use train and test without normalized
    * HDBSCAN: all data with Earth without normalized
    * KMEANS: train and test, here we can use normalized data and data without standardized.
    * AGGLOMERATIVE CLUSTERING: all data with Earth
    * Get the silhouette score for all models and keep with the high
    
* Statistics:
    * Group the data frame by the labels of the best model 
    * Analyze with graphs the features more critical.

## Improvements

* Make a hypothesis analysis of each cluster
* Back to beginning the data and try to do a regression for some removed columns.
* Use other techniques to reduce dimensions in the categorical data
* Delete more correlations columns
* Run the models to obtain a better silhouette score. 