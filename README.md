# Air Quality Monitoring and Prediction System

## Overview
This project provides a comprehensive system for monitoring, analyzing, and predicting air quality across major Indian cities. It combines real-time data monitoring with advanced machine learning models to forecast air quality trends and detect anomalies, delivering scheduled reports to stakeholders.

## Features
- **Multi-city Monitoring**: Track air quality across Delhi, Mumbai, Bengaluru, Hyderabad, and Kolkata
- **Real-time Data**: Access current air quality metrics from 90+ monitoring stations
- **Historical Analysis**: Analyze trends with customizable date ranges
- **ML-based Predictions**: Forecast air quality using ensemble of models (ARIMA, LSTM, etc.)
- **Anomaly Detection**: Identify unusual pollution events using Isolation Forest
- **Alert System**: Generate alerts when air quality reaches dangerous levels
- **Scheduled Reporting**: Automatically generate and send reports at configured intervals

## Tech Stack
- **Core**: Python for data processing and machine learning
- **Models**: ARIMA, LSTM, SVM, Isolation Forest, and ensemble approaches
- **Data Processing**: Custom data ingestion and validation pipelines
- **API Integration**: Urban Sciences air quality data API
- **Reporting**: Automated report generation and distribution

## Project Structure
```
project/
├── .git/                        # Git repository
├── data/                        # Data storage directory
├── ARIMA.ipynb                  # ARIMA time series forecasting model
├── data_ingestion.py            # Data collection and processing pipeline
├── data_validation.py           # Data quality verification
├── Ensemble_learnig.ipynb       # Combined model approach
├── Fetch_data.py                # API data retrieval
├── final_model_implementaion.ipynb  # Production model implementation
├── implem_model_alert.ipynb     # Alert system implementation
├── Isolation_Forest.ipynb       # Anomaly detection model
├── LSTM_encoder.ipynb           # Deep learning sequence model
├── Model_comparison.ipynb       # Performance analysis of different models
├── One_class_SVM.ipynb          # Support Vector Machine implementation
├── Problem_Statement_3[1].pdf   # Original problem description
├── reporting.ipynb              # Reporting and visualization notebook
├── site_ids.json                # Monitoring station metadata
└── TransNAS_TSAD.ipynb          # Time series anomaly detection model
```

## Running the Project

### Recommended: Google Colab
For the easiest setup with no dependency issues, we recommend running this project in Google Colab:

1. Upload the notebooks to Google Drive
2. Open with Google Colab
3. Mount your Google Drive: 
   ```python
   from google.colab import drive
   drive.mount('/content/drive')
   ```
4. Navigate to the project directory
5. Run notebooks in the recommended sequence (see below)

### Alternative: Local Setup
If you prefer to run locally:

#### Prerequisites
- Python 3.8+
- Jupyter Notebook/Lab
- Required Python libraries listed in requirements.txt

#### Installation
1. Clone the repository
```bash
git clone https://github.com/yourusername/air-quality-monitoring.git
cd air-quality-monitoring
```

2. Install dependencies
```bash
pip install -r requirements.txt
```

3. Set up environment variables for API access
```bash
export API_KEY=63h3AckbgtY
```

## Workflow

### 1. Data Collection
Run `Fetch_data.py` to collect data from the Urban Sciences API:
```
http://atmos.urbansciences.in/adp/v4/getDeviceDataParam/imei/{site_id}/params/{params}/startdate/{start_date}/enddate/{end_date}/ts/mm/avg/15/api/63h3AckbgtY?gaps=1&gap_value=NaN
```

### 2. Data Processing
Run `data_ingestion.py` and `data_validation.py` to prepare the data for modeling.

### 3. Model Training and Evaluation
Open and run these notebooks in sequence:
- `Model_comparison.ipynb`: Compare different model approaches
- `ARIMA.ipynb`: Time series forecasting
- `LSTM_encoder.ipynb`: Deep learning sequence model
- `Isolation_Forest.ipynb`: Anomaly detection
- `One_class_SVM.ipynb`: Support Vector Machine implementation
- `TransNAS_TSAD.ipynb`: Advanced time series anomaly detection
- `Ensemble_learnig.ipynb`: Combined model approach

### 4. Implementation
- `final_model_implementaion.ipynb`: Deploy the best-performing model
- `implem_model_alert.ipynb`: Set up the alert system

### 5. Reporting
- `reporting.ipynb`: Generate scheduled reports

## Data Sources
The system utilizes air quality data from 90+ monitoring stations across 5 major Indian cities, including:
- Delhi
- Mumbai
- Bengaluru
- Hyderabad
- Kolkata

### Monitoring Stations
Stations are managed by various pollution control boards:
- Central Pollution Control Board (CPCB)
- Delhi Pollution Control Committee (DPCC)
- Karnataka State Pollution Control Board (KSPCB)
- Telangana State Pollution Control Board (TSPCB)
- West Bengal Pollution Control Board (WBPCB)
- Maharashtra Pollution Control Board (MPCB)

### Parameters Monitored
- PM2.5: Fine particulate matter (particles ≤ 2.5 μm in diameter)
- PM10: Coarse particulate matter (particles ≤ 10 μm in diameter)

## Machine Learning Models

### 1. Time Series Forecasting
- **ARIMA**: Statistical model for time series forecasting
  - Handles seasonality and trends in air quality data
  - Used for short-term predictions (24-48 hours)

- **LSTM**: Long Short-Term Memory neural network
  - Captures complex temporal patterns
  - Better for mid-term forecasting (72-120 hours)

### 2. Anomaly Detection
- **Isolation Forest**: Identifies unusual pollution events
  - Effective at detecting sudden spikes in pollution levels
  - Low computational requirements

- **One-class SVM**: Support Vector Machine for outlier detection
  - Useful for detecting gradual deviations from normal patterns
  - Robust against noise in the data

### 3. Ensemble Approach
- Combines multiple models for improved accuracy
- Weighted averaging based on historical performance
- Adaptive weights that adjust seasonally

### 4. TransNAS Time Series Anomaly Detection
- Neural architecture search for optimized model structure
- Specialized for environmental time series data
- Improved detection of subtle anomalies

## Automated Reporting System
The project includes a scheduled reporting mechanism that:
- Generates comprehensive PDF reports
- Includes visualizations of current and predicted air quality
- Highlights anomalies and concerning trends
- Distributes reports to configured recipients
- Can be scheduled daily, weekly, or monthly

## Air Quality Standards
The system uses the following AQI standards for PM2.5 and PM10:

| Category | PM2.5 (μg/m³) | PM10 (μg/m³) | Health Impact |
|----------|---------------|--------------|---------------|
| Good | 0-30 | 0-50 | Minimal Impact |
| Satisfactory | 31-60 | 51-100 | Minor breathing discomfort to sensitive people |
| Moderate | 61-90 | 101-250 | Breathing discomfort to people with lung disease |
| Poor | 91-120 | 251-350 | Breathing discomfort to most people on prolonged exposure |
| Very Poor | 121-250 | 351-430 | Respiratory illness on prolonged exposure |
| Severe | >250 | >430 | Affects healthy people and seriously impacts those with existing diseases |

## Results and Performance
Our ensemble model achieves:
- 85%+ accuracy in 24-hour predictions
- 75%+ accuracy in 72-hour predictions
- 92% accuracy in anomaly detection
- Alert lead time of 6-12 hours before critical pollution events

## Future Work
- Extending the model to predict additional pollutants (SO2, NO2, O3)
- Incorporating weather data for improved predictions
- Developing a simple web dashboard for visualizations
- Adding hyperlocal predictions at street level

## Contributors
- Team Introspectors
- WCE Hackathon 2025

## License
This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgements
- Data provided by Urban Sciences
- Monitoring stations maintained by various pollution control boards across India
- WCE Hackathon 2025 for the problem statement and opportunity
