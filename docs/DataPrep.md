## Data Preparation

From here, the instruction will only tell it to you the concept. The full instruction will be on your jupyter notebook.

This case, we are going to use NYC taxi dataset, to predict how much should a passenger pay for their trip (y = total amount) which is regression problem. We are going to use XGBoost (Xtreme Gradient Boosting) Algorithm


1. Download the data from data source.
2. check the sample data

### Data Manipulation
3. in data manipulation, we convert the data into seconds for start trip and end trip.
4. check the data after data manipulation.
5. use `describe` function to get statistics insight.
6. since there are outliers, we are just using rule based to remove it.

### Data Visualization
7. see the correlation between duration in minutes and distancee
8. check correlation between duration and total amount that the passenger should pay.

As you see there are strong correlation between these variables, which is quite suitable to be used as a feature on ML.

### Data Splitting and saving
9. Use scikit learn to split training, validation, and testing data. (ratio: 80%:19%:1%)
10. Generate csv file for all of the data types (train, val, test)
11. upload all csv file to S3

[BACK TO WORKSHOP GUIDE :house:](../README.md)

[CONTINUE TO NEXT GUIDE :arrow_right:](Build.md)

[BACK TO PREVIOUS GUIDE :arrow_left:](PrepareInfra.md)