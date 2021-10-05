# Predicting Injuries vs No Injuries in traffic crashes within Chicago


**Author**: Samuel Rahwa


September 24, 2021


## Overview


I have been tasked to work for the City of Chicago, as a consultant, to help decide how should they use tax dollars should to reduce injuries from traffic crashes. I need to provide advice to City Council on how to prevent injuries for their residents to increase safety.


## Business Problem


We often hear statistics about many injuries being due to human error, but is this accurate? Rather than pass out blame, we must focus efforts on reducing the likelihood of injuries from crashes. Could we predict the contributory causes of injuries vs no injuries from a car accident, given information about the car, the people in the car, the road conditions and the various other data points.


## Data


This project uses the Traffic Crashes - Crashes dataset, which can be found in `Final_Chicago_Traffic_Crashes_Cleaned.csv` in the data folder for this repo. The description of the column names are listed below and determined by the reporting officer(s) from Chicago Police Department. Here is the link to the full dataset: [Traffic Crashes - Crashes](https://data.cityofchicago.org/Transportation/Traffic-Crashes-Crashes/85ca-t3if)  

From the Traffic Crashes dataset, I used the following features:

* Posted Speed Limit
    - Posted speed limit
* TRAFFIC_CONTROL_DEVICE 
    - Traffic control device present at crash location
* DEVICE_CONDITION 
    - Condition of traffic control device     
* WEATHER_CONDITION 
    - Weather condition at time of crash     
* LIGHTING_CONDITION 
    - Light condition at time of crash
* FIRST_CRASH_TYPE 
    - Type of first collision in crash       
* TRAFFICWAY_TYPE 
    - Trafficway type
* ALIGNMENT         
    - Street alignment at crash location     
* ROADWAY_SURFACE_COND    
    - Road surface condition
* ROAD_DEFECT   
    - Road defects          
* REPORT_TYPE
    - Administrative report type 
* CRASH_TYPE
    - A general severity classification for the crash
* DAMAGE 
    - A field observation of estimated damage                  
* PRIM_CONTRIBUTORY_CAUSE  
    - Most significant factor in causing the crash
* SEC_CONTRIBUTORY_CAUSE   
    - Second most significant factor in causing the crash
* STREET_NO         
    - Street address number of crash location      
* STREET_DIRECTION  
    - Street address direction (N,E,S,W) of crash location       
* STREET_NAME 
    - Street address name of crash location             
* BEAT_OF_OCCURRENCE 
    - Chicago Police Department Beat ID
* NUM_UNITS
    - Each unit represents a mode of traffic with an independent trajectory.
* CRASH_HOUR     
    - The hour of the day         
* CRASH_DAY_OF_WEEK   	
    - The day of the week
* CRASH_MONTH   
    - The month component of CRASH_DATE.           
* LOCATION  
    - The crash location


## Methods


* Data Exploration using Pandas Profling

* Data Cleaning
    - Feature Engineering
    - Removing Columns with 60 % or more missing data
    
* Standard Scaling and OneHotEncoding

* Metrics Used:
    - Precision:
        - How precise/accurate your model is out of those predicted positive, how many of them are actual
          positive
    - Recall:
        - Calculates how many of the Actual Positives our model capture through labeling it as Positive
          (True Positive)
    - F1 Score:
        - Used if we need to seek a balance between Precision/Recall AND if there is an uneven class
          distribution
          
* Running Multiple Supervised Machine Learning Models
    - Logistic Regression
    - Kneighbors Classifier
    - Decision Tree Classifier
    - Bagging Classifier
    - Random Forest Classifier
    - AdaBoost Classifier
    - Gradient Boosting Classifier
    - XGB Classifier
    - Support Vector Classification
    
* GridSearchCV
    - Hyper Tuning Final Two Models
    
* Data Visulization

* Feature Importance


## Results


** F1 is the metric of measurement for our models **

    - Used if we need to seek a balance between Precision/Recall AND if there is an uneven class
    distribution

** XGB Boost **

    - XGBoost makes a decision without looking ahead to see if it is the absolute best choice in long term
    
    - Vanilla Model Results:
        - Injury, F1 → 72%
        - No Injury, F1 → 91 %
        
    - Hyper Tuned Model Results:
        - Injury, F1 → 66 %
        - No Injury, F1 → 90 %
        
** Random Forest **

    - The model considers only a small subset of features rather than all of the features of the model
    
    - Vanilla Model Results:
        - Injury, F1 → 63 %
        - No Injury, F1 → 89 %
        
    - Hyper Tuned Model Results:
        - Injury, F1 → 52 %
        - No Injury, F1 → 89 %


## Conclusions


**Improved XBG Boost Model Predicted these Top 3 Factors in Predicting Injuries vs No Injuries**

> 1.) NUM_Units

>> Number of units involved in the crash. A unit can be a motor vehicle, a pedestrian, a bicyclist, or another non-passenger roadway user. Each unit represents a mode of traffic with an independent trajectory.

> 2.) CRASH_HOUR

>> The hour of the day component

> 3.) POSTED_SPEED_LIMIT

>> Posted speed limit, as determined by reporting officer


**Improved Random Forest Model Predicted these Top 3 Factors in Predicting Injuries vs No Injuries**


> 1.) NUM_UNITS

>> Number of units involved in the crash. A unit can be a motor vehicle, a pedestrian, a bicyclist, or another non-passenger roadway user. Each unit represents a mode of traffic with an independent trajectory.

> 2.) POSTED_SPEED_LIMIT

>> Posted speed limit, as determined by reporting officer 

> 3.) BEAT_OF_OCCURRENCE

>> Chicago Police Department Beat ID. Boundaries available [here](https://data.cityofchicago.org/Public-Safety/Boundaries-Police-Beats-current-/aerh-rz74) 


***


## Next Steps: 


**How could the prediction on injuries vs no injuries in Chicago Traffic Crashes be improved with more time and resources?**


> I could include the Vehicle Data and to Driver/Passenger Data to the Traffic Crashes

> Find a solution why oversampling the minority class (INJURY AND / OR TOW DUE TO CRASH) led to producing zero’s across the Test/Train Split 

> Increase time spent feature engineering, instead of a reliance on OneHotEncoder to simplify the process

> Prepare more time for modeling due to lack of computational capabilities 


***

## For More Information

Please review my full technical analysis in [Jupyter Notebook](https://github.com/SamuelRahwa/Multiclass-Classification-Chicago-Traffic-Crashes/blob/main/Modeling/Hyper-Tuned%20Models.ipynb) or my nontechnical analysis in [presentation](https://github.com/SamuelRahwa/Multiclass-Classification-Chicago-Traffic-Crashes/blob/main/Predicting%20Injuries%20vs%20No%20Injuries%20in%20Chicago%20Traffic%20Crashes%20Presentation%20.pdf).

For any additional questions, please contact **Samuel Rahwa at samuelaaronrahwa@gmail.com**

## Repository Structure

```
├── Data                                        <- Both sourced externally and generated from code
├── Models                                      <- Narrative documentation of analysis in Jupyter notebook
├── Images                                      <- Both sourced externally and generated from code
├── Chicago Traffic Crashes Presentation.pdf    <- PDF version of project presentation
└── README.md                                   <- The top-level README for reviewers of this project
```
