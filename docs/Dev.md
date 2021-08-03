## Deploy Dev

Since the training process also includes the deployment on dev (endpoint creation), we are just checking the status for the endpoint and evaluate the error. This step also triggers to create the dev template infrastucture on `/assets/deploy-model-dev.yml`

1. get the name of the endpoint on dev environment.
2. get status of endpoint.
3. create function to predict the result and get the predictor (XGBoost)
4. define the predictor and predict the result
5. prediction result, include the error.
6. visualize the error.
7. calculate the RMSE for Dev environment.

[BACK TO WORKSHOP GUIDE :house:](../README.md)

[CONTINUE TO NEXT GUIDE :arrow_right:](Prod.md)

[BACK TO PREVIOUS GUIDE :arrow_left:](Train.md)