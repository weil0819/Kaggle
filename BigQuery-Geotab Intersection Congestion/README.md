## BigQuery-Geotab Intersection Congestion
Can you predict wait times at major city intersections?


### Description
We’ve all been there: Stuck at a traffic light, only to be given mere seconds to pass through an intersection, behind a parade of other commuters. Imagine if you could help city planners and governments anticipate traffic hot spots ahead of time and reduce the stop-and-go stress of millions of commuters like you.

Geotab provides a wide variety of aggregate datasets gathered from commercial vehicle telematics devices. Harnessing the insights from this data has the power to improve safety, optimize operations, and identify opportunities for infrastructure challenges.

The dataset for this competition includes aggregate stopped vehicle information and intersection wait times. Your task is to predict congestion, based on an aggregate measure of stopping distance and waiting times, at intersections in 4 major US cities: Atlanta, Boston, Chicago & Philadelphia.


### Evaluation
Score:  
- root mean squared error (RMSE)  

Two Metrics:  
- the total time stopped at an intersection (== wait times)  
- the distance between the intersection and the first place a vehicle stopped while waiting (== stop distances at each intersection)

Six predicted value:  
- TotalTimeStopped_p20  
- TotalTimeStopped_p50 
- TotalTimeStopped_p80 
- DistanceToFirstStop_p20  
- DistanceToFirstStop_p50  
- DistanceToFirstStop_p80


### Data
The data consists of aggregated trip logging metrics from commercial vehicles, such as semi-trucks. The data have been grouped by intersection, month, hour of day, direction driven through the intersection, and whether the day was on a weekend or not.

For each grouping in the test set, you need to make predictions for three different quantiles of two different metrics covering how long it took the group of vehicles to drive through the intersection. Specifically, the 20th, 50th, and 80th percentiles for the total time stopped at an intersection and the distance between the intersection and the first place a vehicle stopped while waiting. You can think of your goal as summarizing the distribution of wait times and stop distances at each intersection.

Each of those six predictions goes on a new row in the submission file. Read the submission `TargetId` fields, such as `1_1`, as the first number being the `RowId` and the second being the `metric id`. You can unpack the submission metric id codes with `submission_metric_map.json`.

The training set includes an optional additional output metric (`TimeFromFirstStop`) in case you find that useful for building your models. It was only excluded from the test set to limit the number of predictions that must be made.


