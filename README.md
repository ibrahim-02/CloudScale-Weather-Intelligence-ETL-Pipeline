# CloudScale Weather Intelligence ETL Pipeline

Automated daily pipeline that extracts weather data from OpenWeatherMap API, transforms it, and loads it into AWS S3 using Apache Airflow.

## Architecture

```
OpenWeatherMap API → Apache Airflow → AWS S3
```

## Technologies

- Apache Airflow - Workflow orchestration
- Python & Pandas - Data processing
- AWS S3 - Cloud storage
- OpenWeatherMap API - Data source

## Features

- Daily automated weather data extraction for Portland
- Temperature conversion (Kelvin → Fahrenheit)
- 12 weather metrics including temp, humidity, wind speed, pressure, sunrise/sunset times
- Timestamped CSV files stored in S3
- Error handling with 2 retries

## Setup

1. **Install dependencies**
```bash
pip install -r requirements.txt
```

2. **Configure Airflow HTTP Connection**
   - Conn Id: `weathermap_api`
   - Host: `https://api.openweathermap.org`

3. **Update credentials in code**
   - AWS credentials (key, secret, token)
   - OpenWeatherMap API key
   - S3 bucket name

4. **Run Airflow**
```bash
airflow webserver --port 8080
airflow scheduler
```

## DAG Details

- **Schedule:** Daily
- **Tasks:** API check → Extract → Transform & Load
- **Output:** `current_weather_data_portland_DDMMYYYYHHMMSS.csv`

## Data Fields

City, Description, Temperature (F), Feels Like (F), Min/Max Temp (F), Pressure, Humidity, Wind Speed, Time of Record, Sunrise/Sunset Times

## Author

Ibrahim - MS Data Analytics Engineering, Northeastern University
