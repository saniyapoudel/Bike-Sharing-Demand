 Bike Sharing Demand Prediction Using Regression

1. Dataset and Problem

The Bike Sharing Demand dataset contains information about bike rentals along with weather, date, time, and working-day information. The main objective of this project is to predict the number of bike rentals (`count`) using regression techniques. The dataset contains features such as season, holiday, workingday, weather, temperature, humidity, windspeed, and datetime.

2. Data Preprocessing and Cleaning

The dataset was first loaded and inspected to understand its structure, data types, missing values, and duplicate records. The `datetime` column was converted into the proper datetime format. Duplicate records were removed, and invalid or negative target values were checked and removed. Numerical missing values were handled using median imputation, while categorical missing values were handled using the most frequent value.

The `casual` and `registered` columns were excluded from model training because they directly contribute to the target `count` and would cause target leakage.

3. Feature Engineering

The `datetime` column was transformed into useful features:

* Year
* Month
* Day
* Hour
* Weekday

Additional features such as `is_weekend` and `rush_hour` were created. These features help the model understand daily and weekly rental patterns. For example, rental demand can change significantly during commuting hours and on weekends.

4. Encoding and Scaling

Categorical features were converted into numerical form using One-Hot Encoding. Numerical features such as temperature, humidity, and windspeed were processed using imputation and StandardScaler. A preprocessing pipeline was used so that the same transformations are automatically applied during both training and prediction.

Since the dataset does not contain natural-language text, traditional text vectorization such as TF-IDF was not required.

5. Model Training and Experimentation

Multiple regression algorithms were experimented with:

Ridge Regression
Random Forest Regressor
Gradient Boosting Regressor

The models were trained using the processed training data. A time-based train/test split was used so that earlier observations were used for training and later observations were used for testing.

6. Model Evaluation

The models were evaluated using:

MAE (Mean Absolute Error)
RMSE (Root Mean Squared Error)
R² Score
RMSLE (Root Mean Squared Logarithmic Error)

MAE and RMSE measure prediction error, while R² measures how well the model explains the variation in bike demand. RMSLE is useful for demand prediction because it gives importance to relative differences between predicted and actual rental counts.

7. Model Saving

The final trained model, including its preprocessing pipeline, was saved using Joblib as:

`bike_sharing_regression_model.pkl`

Saving the complete pipeline ensures that the same preprocessing steps are applied when new data is entered into the prediction system.

 8. Working Prototype / GUI

A Gradio-based graphical user interface was developed as the working prototype. Users can enter season, holiday, working-day, weather, temperature, humidity, windspeed, date, hour, and weekday information. The saved `.pkl` model processes these inputs and produces a predicted number of bike rentals.

9. Key Findings

The analysis shows that bike rental demand is influenced by time, season, weather conditions, temperature, humidity, and working-day patterns. Hour and date-related features are particularly useful because rental demand changes throughout the day and across different days. The regression models provide a way to estimate demand from these factors and demonstrate how machine learning can be applied to bike-sharing demand forecasting.

Conclusion

This project completed the complete regression workflow from data loading and exploration to preprocessing, feature engineering, model training, evaluation, model saving, and GUI-based prediction. The resulting system can accept new bike-sharing conditions and provide an estimated rental demand using the trained regression model.
