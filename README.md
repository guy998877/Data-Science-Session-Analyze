#User Engagement Prediction Project

![image](https://github.com/user-attachments/assets/3570a7e2-18ee-4012-88b6-b1382ab89968)


## Project Overview

This project aims to predict user disengagement in a web-based Citizen Science platform. By analyzing user activity data, we seek to identify patterns that lead to users leaving a session. The ultimate goal is to enhance user retention by providing timely interventions when a user is likely to disengage.

## Dataset

The dataset consists of user HITs (contributions) to the platform, where each row contains:
- `user_id`: Unique identifier for each user.
- `timestamp`: The time when the user made a contribution.
- Additional features generated through feature engineering.

### Feature Engineering

Several features were engineered to better capture user behavior:

1. **Time Since Last HIT (`time_since_last_hit`)**: Time in seconds since the user's last activity.
2. **Activity in Last 5, 10, and 15 Minutes (`activity_last_5_min`, `activity_last_10_min`, `activity_last_15_min`)**: Number of activities performed by the user within the last 5, 10, and 15 minutes.
3. **Session Duration (`session_duration`)**: Duration of the user's current session.
4. **Hour of Day (`hour_of_day`)**: The hour when the activity occurred.
5. **Time of Day (`time_of_day`)**: Categorized into 'Night', 'Morning', 'Afternoon', 'Evening'.
6. **Previous Sessions (`previous_sessions`)**: Count of previous sessions the user has participated in.
7. **Previous Disengagements (`previous_disengagements`)**: Count of times the user has disengaged before.
8. **Weekday (`weekday`)**: The day of the week when the activity occurred.
9. **Is Weekend (`is_weekend`)**: Indicator for whether the activity occurred on a weekend.
10. **Inter-Session Time Gap (`inter_session_gap`)**: Time gap between the current HIT and the next HIT.

## Modeling

Three models were trained and compared to predict user disengagement:

1. **Random Forest**: A baseline model using an ensemble of decision trees.
2. **XGBoost without Hyperparameter Tuning**: A gradient boosting model trained with default settings.
3. **Tuned XGBoost**: The XGBoost model with hyperparameters tuned using Bayesian optimization with Optuna.

### Model Comparison

The models were evaluated using the Precision-Recall curve, with the following results:
- **Random Forest**: AP = 0.9182
- **XGBoost (No Tuning)**: AP = 0.9353
- **Tuned XGBoost**: AP = 0.9445

The Tuned XGBoost model demonstrated the best performance, making it the recommended model for deployment.

### Prerequisites

Ensure you have the following Python packages installed:
- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `xgboost`
- `sklearn`
- `optuna`
- `joblib`
- `shap`

### Running the Models

1. **Load Data**: Prepare your dataset in the same format used in this project.
2. **Feature Engineering**: Apply the feature engineering steps outlined in the project.
3. **Train Models**: Train the Random Forest and XGBoost models, and apply hyperparameter tuning using Optuna.
4. **Evaluate Models**: Use the Precision-Recall curve and SHAP values to evaluate model performance and feature importance.
5. **Deploy the Best Model**: The Tuned XGBoost model is recommended for deployment.

## Conclusion

This project successfully identified key predictors of user disengagement and developed a robust model for predicting when users are likely to leave a session. The insights gained can be used to improve user retention strategies on the Citizen Science platform.

## Contact

For any questions or issues, please contact me guyzagor@gmail.com
