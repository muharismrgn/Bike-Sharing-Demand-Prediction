# Bike Sharing Demand Prediction

The bike sharing system is an innovation in bike rental that automates the entire process, from member registration, bike rental, to bike return. Through this system, users can easily rent bikes from a specific location and return them to another.

Apart from interesting real-world applications of bike-sharing systems, the characteristics of data generated by these systems make them attractive for research. Unlike other transport services such as buses or subways, the duration of travel, departure, and arrival position is explicitly recorded in these systems. This feature turns the bike-sharing system into a virtual sensor network that can be used for sensing mobility in the city. Hence, it is expected that the most important events in the city could be detected by monitoring these data.

**`PROBLEM STATEMENT`**

The main stakeholders in this issue are bike sharing service providers, especially the data analysis team and the executive team in this organization play an important role. The main problem is "How to predict bike demand at a given time?", considering factors such as weather, day, and time. This problem needs to be solved because accurate predictions of bike demand can help service providers develop business strategies to meet customer expectations and demand levels. To address the above problem statement, specific questions need to be answered, such as:

1. How to predict demand for bike at certain times of the day, such as on weekdays/weekends or during certain hours?
2. How does weather influence demand, considering factors such as season, windspeed, temperature, or humidity?

**`GOALS`**

Based on the above-mentioned problem, the objective is to build a predictive model capable of predicting the rental demand quantity by considering these factors (independent variables) with the least possible error.

**`ANALYTIC APPROACH`**

The proposed analytical approach involves the use of supervised machine learning methods, specifically regression. The model will be trained using historical data to provide more accurate predictions. This solution will provide insights to the executive team for strategic decision-making, enabling more efficient resource allocation and robust business strategy development.

**`METRIC EVALUATION`**

Errors in predicting bike-sharing usage can lead to specific and measurable consequences, especially concerning pricing. This situation has measurable implications for financial impact, including:

1. **Loss of Potential Profits**: Underpredicting demand may result in limited availability of bicycles, leading to a loss of potential profits. For example, in the scenario of a 15-minute single ride bike rental for a casual user on a classic bike, the cost would be $1 + ($0.05 * 15) = $1.75. Now, let's consider a situation where 100 bikes are available for rent, but the actual demand turns out to be 150 bikes at any given hour. In this case, the potential profit lost in that hour would be (150 - 100) * $1.75 = $87.5. Obviously, in a day, the potential loss would be much greater than that. 
    
2. **Financial Losses**: Overpredicting demand can lead to oversupply and, consequently, financial loss. If, for example, 500 bicycles are prepared for rental on one day, but there is only demand for 250 bicycles during that day, then if the operating cost (e.g., maintenance) is $0.55 per bike per day, the operating cost loss is (500- 250) * -$0.55 = -$137.5.

Evaluation metrics measure how close predictions are to the actual values, providing an indication of the model's error. Evaluation metrics give an overview of how well the model can provide accurate predictions. In the context of bike-sharing usage prediction error, the following evaluation metrics can be used to measure the accuracy of the model for predicting demand:

| Metric Evaluation | Description |
|-|-|
| Mean Absolute Error (MAE) | MAE measures the average absolute difference between the predicted and actual values of bike demand. A lower MAE value indicates a better prediction. |
| Mean Absolute Percentage Error (MAPE) | MAPE will measure the average absolute difference between the predicted value and the actual value of bicycle demand as a percentage. This gives an idea of how accurate the prediction is as a percentage of the actual value. A lower MAPE indicates a better prediction.|
| R-Squared (Coefficient of Determination) | R-Squared measures the extent to which the model can explain the variability in the target variable (e.g., actual demand). A higher R2 value indicates that the model is better at predicting variability. |

**`PROJECT LIMITATION`**

Project limitations involve a focus on weather, day, and time as the main predictors, without considering other factors that may influence bike demand.

**`MODELING PROCESS`**

- Based on the two experiments (without target transform and with target transform) conducted, 3 best models were selected for tuning including Catboost Regressor, XGBoost Regressor, and Support Vector Regressor. 

- Catboost Regressor is still the best model after tuning and is used as the final model. With tuning parameters 'iterations': 1500, 'learning_rate': 0.07, 'depth': 8 obtained average performance results with MAE: 22.75, R2: 95.57%, and MAPE: 22.81%. 

- When predicting the testing data (unseen data) the performance results become better with MAE: 21.82, R2: 95.95%, MAPE: 22.81%. This indicates that the final model is good for predicting unseen data or stable for predicting other similar data.

**`MODEL LIMITATION`**

- The small range of values (1-50) is less reliable because the average error is quite large with 44% of the actual demand (data). However, we can justify this by looking at the MAE, where the average MAE in this range is about 5 points.

- It can be concluded that this model may be less suitable for predicting small values, but it can reliably predict better on a larger scale of values. In addition, the model may also be less accurate for the range of predicted values outside the training data (1-970).

- This model is also less reliable for predicting casual members because the MAPE is quite large 41.43% even though we can see from the MAE value which is relatively quite small, which is around 8.

**`RECOMENDATION`**

- Since the model has limitations in predicting small values, consider fine-tuning the model specifically for the range where the demand is low (1-50). This can involve additional feature engineering, adjusting hyperparameters, or using a different modeling approach tailored to small demand values.

- Review the model evaluation metrics and ensure that the metrics used match the business objectives and demand characteristics of the bicycle. Consider using metrics such as MAPE (Mean Absolute Percentage Error) to predict a large range of values especially greater than 100 and MAE to predict a small range of values (1-50).

- In-depth analysis to understand the causes of large underestimates or overestimates. Review whether there are external factors not included in the model, changes in user behavior, or policy changes that could affect demand patterns.

**`DEPLOY`**
link url : https://bikesharingprediction.streamlit.app/
![image](https://github.com/muharismrgn/Bike-Sharing-Demand-Prediction/assets/143411521/7f238be3-0ef7-40d5-a67d-1c3a04a20e0d)
