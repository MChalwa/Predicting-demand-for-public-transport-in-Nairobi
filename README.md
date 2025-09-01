### Public Transport Demand Prediction in Nairobi
#### Project Overview
This project aims to analyze public transport data in Nairobi and build regression models to predict public transport demand, using Mean Absolute Error (MAE) as the evaluation metric.
The goal is to identify the best-performing model for predicting people's movement based on the provided dataset.

### Data
The project uses two datasets:

- train_revised.csv: Contains historical public transport ride data, including ride details, payment information, and seat numbers (used to derive demand).
- test_questions.csv: Contains similar ride details but without payment and seat information, used for making predictions.
  
### Methodology
The project followed these key steps:

- Data Loading and Initial Inspection.
The train_revised.csv and test_questions.csv files were loaded into pandas DataFrames. Initial inspection of the data types and structure was performed.

- Data Preprocessing and Feature Engineering.
The travel_date column was converted to datetime objects.
New features were extracted from travel_date and travel_time, including day_of_week, month, hour, and minute.
A route feature was created by combining travel_from and travel_to.
Missing values in both datasets were checked (no missing values were found in the relevant columns).

### Exploratory Data Analysis (EDA)

Distributions of key features like day_of_week, month, hour, travel_from (top 10), and travel_to were visualized using count plots.
The relationship between time-based features (hour, day_of_week, month) and demand was analyzed and visualized using line plots.
The top 10 most frequent routes by demand were identified and visualized using a bar plot.
Key insights from the EDA included the peak demand during morning rush hours, seasonality in demand with a peak in December, and the dominance of certain routes like Kisii-Nairobi.
Aggregate Demand: The training data, which was initially at the seat level, was aggregated to the ride level by grouping by ride-specific features and counting the number of seats (seat_number) to represent the demand for each ride.

### Feature Engineering

Categorical features (travel_from, travel_to, car_type, and route) were one-hot encoded in both the aggregated training data (train_demand) and the test data (test).
Columns were aligned between the training and test feature sets to ensure consistency for model input.
The data was split into features (X_train, X_test) and the target variable (y_train).

### Model Selection and Training

Several regression models were selected and trained on the X_train and y_train data:

- Linear Regression
- Ridge Regression
- Lasso Regression
- Elastic Net
- Decision Tree Regressor
- Random Forest Regressor
- Gradient Boosting Regressor
- Hist Gradient Boosting Regressor
- XGBoost Regressor
  
### Prediction
Predictions were made on the X_test data using each of the trained models.

### Evaluation
The performance of each model was evaluated using Mean Absolute Error (MAE) on the training data. The MAE scores were calculated and stored.

Model Comparison: The MAE scores of all models were compared to identify the best-performing model (the one with the lowest MAE). A bar plot was generated to visualize the MAE comparison.

### Results
The evaluation on the training data showed the following MAE scores:

- Linear Regression: 4.7230
- Ridge: 4.7236
- Lasso: 6.0775
- Elastic Net: 6.0623
- Decision Tree: 1.4266
- Random Forest: 2.0695
- Gradient Boosting: 3.9515
- Hist Gradient Boosting: 3.3268
- XGBoost: 2.8239


Based on the MAE on the training data, the Decision Tree model performed the best with the lowest MAE score.

### Conclusion
The project successfully implemented a workflow for predicting public transport demand using various regression models.
The Decision Tree model showed promising results on the training data.

