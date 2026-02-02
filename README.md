# CoGo Bikeshare Demand and Usage Analysis


<img width="1020" height="565" alt="Screenshot 2026-02-01 at 10 45 14 PM" src="https://github.com/user-attachments/assets/7f6bad10-aeb4-4305-a7b3-0cf0174a392e" />

## Overview
This project analyzes CoGo bikeshare trip data from Columbus, Ohio, combined with NOAA daily weather data, to understand and predict bikeshare demand, trip duration, and rider behavior. Using supervised machine learning techniques, the project aims to identify key factors influencing ridership and provide actionable insights for city planners and transportation stakeholders.

## Problem Statement
The City of Columbus seeks to better understand factors affecting bikeshare demand and membership for the CoGo program. This project builds predictive models to:
- Estimate daily bike demand under varying weather and temporal conditions
- Predict expected trip duration based on rider and trip characteristics
- Classify rider behavior to support marketing and operational decisions

## Data Description
- **Bikeshare Data**: CoGo trip-level data from 2022–2024  
- **Weather Data**: NOAA daily weather data for Columbus, OH  
- **Size**: ~182,000 trips with 13+ core features  
- **Granularity**: Individual trip records, aggregated where required  

### Key Feature Groups
- **Trip Information**: start/end time, trip duration  
- **Station & Geography**: start/end stations, latitude/longitude, region of Columbus  
- **Weather (NOAA)**: min/max/avg temperature, precipitation, snowfall  
- **Rider Attributes**: bike type, member vs. casual rider  
- **Temporal Features**: day of week, weekend indicator, season  

## Feature Engineering
- Trip duration calculation and outlier handling
- Distance estimation between stations (proxy using coordinates)
- Weather alignment by ride date
- Binary indicators for rain, snow, weekend
- Seasonal and regional dummy variables
- Round-trip identification

## Research Questions
1. **Bike Demand Prediction**  
   *At a given day, location, and weather condition, what is the expected demand for bicycles?*  
   - Target: `ride_count` (numerical)

2. **Trip Duration Prediction**  
   *Based on station, rider type, and bike type, how long will a trip last?*  
   - Target: `duration_min_capped` (numerical)

3. **Rider Behavior Classification**  
   *Can riders be segmented into categories such as members vs. casual users?*  
   - Target: `member_dummy` (binary classification)

## Modeling Approach
### Regression Tasks (RQ1 & RQ2)
- Multiple Linear Regression
- K-Nearest Neighbors (KNN) Regressor
- Decision Trees
- Random Forest (Tree Ensembles)

### Classification Task (RQ3)
- Logistic Regression
- KNN Classifier
- Decision Trees
- Random Forest Classifier

Models were selected to balance interpretability and predictive power while accounting for potential non-linear relationships.

## Model Evaluation
- **Validation Strategy**: Train on 2022–2023 data, test on 2024 data
- **Regression Metrics**:
  - RMSE
  - MAPE
  - R²
- **Classification Metrics**:
  - Accuracy
  - Precision
  - Recall
  - Confusion Matrix

Thresholds were adjusted to balance marketing reach and misclassification risk.

## Key Insights
- Weather variables (especially temperature and precipitation) significantly influence demand
- Seasonal and regional patterns strongly affect usage
- Tree-based models outperformed linear baselines for most tasks
- Rider segmentation supports targeted promotions and membership conversion strategies
- Demand surges often align with holidays or special events

## Challenges & Limitations
- Moderate collinearity among weather and seasonal variables
- Data quality issues (extreme trip durations, missing values)
- Distance estimation limited by lack of GPS route data
- Curse of dimensionality for high-feature KNN models

## Future Improvements
- Segment models by season, region, or bike type
- Incorporate holiday and city event calendars
- Extend historical data to improve robustness
- Use bike-level IDs for maintenance and operational insights

## Tools & Technologies
- Python
- Pandas, NumPy
- Scikit-learn
- Matplotlib / Seaborn
- Jupyter Notebook

## Audience
City planners, transportation engineers, policy makers, and CoGo marketing and operations teams.

## Author
**Shilp Patel**  
Master’s Student – Advanced Data Analytics  
University of North Texas
