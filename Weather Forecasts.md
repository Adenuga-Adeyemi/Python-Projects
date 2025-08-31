# Exploratory Data Analysis on Weather Forecast Dataset

## Introduction
Weather forecasting plays a crucial role in various sectors, including agriculture, transportation, disaster management, and daily life planning. This report presents an Exploratory Data Analysis (EDA) conducted on a weather dataset to uncover patterns, trends, and insights related to meteorological conditions.  

The analysis is based on a Jupyter Notebook that loads and examines hourly weather data from 2012, focusing on variables such as temperature, humidity, wind speed, visibility, pressure, and weather conditions.  

The EDA aims to provide a foundational understanding of the dataset, identify key characteristics, and highlight potential areas for further modeling or prediction tasks. By visualizing and summarizing the data, we can better comprehend how weather variables interact and vary over time.  

---

## Problem Statement
Weather data is often complex and multifaceted, with numerous variables influencing conditions like temperature, precipitation, and visibility. Without proper analysis, it can be challenging to identify trends, anomalies, or correlations that could inform forecasting models or decision-making processes.  

The primary problem addressed in this report is the lack of a structured exploration of the 2012 weather dataset, which may contain insights into seasonal patterns, extreme events, or relationships between variables (e.g., humidity and visibility). Inaccurate or incomplete understanding of such data could lead to poor predictions in real-world applications, such as aviation safety or agricultural planning.  

This EDA seeks to mitigate these issues by systematically analyzing the dataset to reveal its structure, quality, and key findings.  

---

## Objectives
The main objectives of this analysis are:

- To understand the structure and content of the weather dataset, including its dimensions, data types, and unique values.  
- To identify summary statistics and distributions of key weather variables.  
- To explore relationships between variables, such as temperature and humidity, or weather conditions and visibility.  
- To detect any anomalies, missing values, or patterns (e.g., instances of clear weather with high humidity).  
- To provide recommendations for further analysis or modeling based on the insights gained.  

By achieving these objectives, the report will serve as a stepping stone for advanced weather forecasting techniques, such as machine learning models for predicting weather conditions.  

---

## Data Source
The dataset used in this analysis is titled **"Project 1 - Weather Dataset.csv"**.  
It appears to be an hourly weather record from a single location (likely Toronto, Canada, based on typical datasets of this nature) for the year 2012.  

- **Number of Rows:** 8,784  
- **Number of Columns:** 8  

### Key Columns:
- **Date/Time:** Timestamp of the observation (e.g., "1/1/2012 0:00")  
- **Temp_C:** Temperature in Celsius  
- **Dew Point Temp_C:** Dew point temperature in Celsius  
- **Rel Hum_%:** Relative humidity in percentage  
- **Wind Speed_km/h:** Wind speed in km/h  
- **Visibility_km:** Visibility in kilometers  
- **Press_kPa:** Atmospheric pressure in kilopascals  
- **Weather:** Categorical description of weather conditions (e.g., "Fog", "Clear", "Rain")  

The dataset was loaded into a Pandas DataFrame in a Google Colab environment using Python 3.  
There are **no missing values** based on the `info()` check, and the data types are appropriate.  

---

## Methodology
The analysis was conducted using **Python in a Jupyter Notebook environment (Google Colab)**.  

### Steps:
1. **Data Loading**  
   - Imported Pandas library  
   - Loaded the CSV file into a DataFrame named `weather_data`  

2. **Initial Inspection**  
   - `head()` to view the first rows  
   - `shape` to check dataset dimensions (8784 × 8)  
   - `columns` to list feature names  
   - `info()` to check data types and nulls  
   - `index` to inspect row indices  

3. **Unique Values and Distributions**  
   - Used `unique()` to identify distinct weather conditions  
   - Used `describe()` for summary statistics  

4. **Data Filtering and Queries**  
   - Filtered conditions such as clear weather with humidity > 50%  
   - Checked visibility > 40 km  

5. **Advanced EDA**  
   - Counted weather conditions with `value_counts()`  
   - Grouped by weather conditions for aggregated statistics  
   - Checked extreme events like high winds or snow  

6. **Tools and Libraries**  
   - **Python 3.12.3**  
   - **Pandas** for data manipulation  

---

## Exploratory Data Analysis

### Dataset Overview
- **Shape:** 8784 rows × 8 columns  
- **Columns:**  
  - Date/Time (object)  
  - Temp_C (float64)  
  - Dew Point Temp_C (float64)  
  - Rel Hum_% (int64)  
  - Wind Speed_km/h (int64)  
  - Visibility_km (float64)  
  - Press_kPa (float64)  
  - Weather (object)  
- **Missing Values:** None  
- **Index:** RangeIndex (0 → 8783)  

### Sample Data (First 5 Rows)

| Date/Time     | Temp_C | Dew Point Temp_C | Rel Hum_% | Wind Speed_km/h | Visibility_km | Press_kPa | Weather                  |
|---------------|--------|------------------|-----------|-----------------|---------------|-----------|--------------------------|
| 1/1/2012 0:00 | -1.8   | -3.9             | 86        | 4               | 48.0          | 101.24    | Fog                      |
| 1/1/2012 1:00 | -1.8   | -3.7             | 87        | 4               | 48.0          | 101.24    | Fog                      |
| 1/1/2012 2:00 | -1.8   | -3.4             | 89        | 9               | 48.0          | 101.26    | Freezing Drizzle, Fog    |
| 1/1/2012 3:00 | -1.5   | -3.2             | 88        | 6               | 48.0          | 101.27    | Freezing Drizzle, Fog    |
| 1/1/2012 4:00 | -1.5   | -3.3             | 88        | 7               | 48.0          | 101.23    | Fog                      |

---

### Summary Statistics

| Statistic | Temp_C | Dew Point Temp_C | Rel Hum_% | Wind Speed_km/h | Visibility_km | Press_kPa |
|-----------|--------|------------------|-----------|-----------------|---------------|-----------|
| count     | 8784   | 8784             | 8784      | 8784            | 8784          | 8784      |
| mean      | 8.8    | 2.6              | 67.4      | 14.6            | 27.7          | 101.05    |
| std       | 11.7   | 10.9             | 16.9      | 8.9             | 12.6          | 0.84      |
| min       | -23.3  | -28.5            | 18        | 0               | 0.2           | 97.5      |
| 25%       | -1.2   | -5.9             | 56        | 9               | 24.1          | 100.5     |
| 50%       | 9.3    | 3.3              | 68        | 13              | 25.0          | 101.0     |
| 75%       | 18.8   | 11.8             | 81        | 20              | 48.3          | 101.6     |
| max       | 33.0   | 24.4             | 100       | 83              | 48.3          | 103.6     |

**Insights:**  
- Temperature ranges from -23.3°C to 33.0°C.  
- Average humidity is 67.4%, with extremes up to 100%.  
- Wind speed reaches up to 83 km/h.  
- Visibility averages 27.7 km but drops as low as 0.2 km.  

---

### Unique Weather Conditions
There are **50 unique weather conditions**, including:  
- Fog  
- Freezing Drizzle, Fog  
- Mostly Cloudy  
- Rain  
- Snow  
- Thunderstorms  
- Rain + Snow combinations  

Most frequent conditions:  
- **Mainly Clear** (2106 occurrences)  
- **Mostly Cloudy** (2069 occurrences)  
- **Cloudy** (1728 occurrences)  

---

### Key Insights from Queries
- **Clear Weather with Humidity > 50%**: 1070 instances  
- **Visibility > 40 km**: 2014 instances, often under clear/cloudy skies  
- **Wind Speed = 4 km/h**: 474 instances, mostly calm foggy conditions  
- **Snow Events**: 390 occurrences, mostly winter  
- **Max Wind Speed (83 km/h)** recorded during "Rain" (3/10/2012) and "Fog" (9/9/2012)  

---

### Correlations and Patterns
- **Temperature ↔ Dew Point**: Highly correlated (expected)  
- **Humidity > 80%**: Associated with **low visibility** (<10 km)  
- **Pressure Drops**: Linked with stormy weather  

*Suggested Visualizations:*  
- Histogram of temperatures  
- Scatter plot: Temp vs. Humidity  
- Bar chart: Weather condition frequencies  
- Time-series plot: Temperature over 2012  

---

## Conclusion
This EDA reveals a **well-structured dataset** with diverse weather patterns throughout 2012.  

Key findings:  
- Seasonal temperature variations from -23.3°C to 33.0°C  
- Frequent "Clear" or "Cloudy" conditions  
- Strong correlation between **humidity and visibility**  
- Extreme events like strong winds and fog detected  
- No missing values, making the dataset reliable  

The dataset provides a **solid foundation for weather modeling and forecasting**.  

---

## Recommendations
- **Data Enhancement:** Add more years or locations for comparative insights  
- **Advanced Modeling:** Use regression (temperature) or classification (weather type) models  
- **Visualization:** Incorporate Matplotlib/Seaborn plots for clarity  
- **Outlier Handling:** Re-check extreme events like wind speeds of 83 km/h  
- **Further Analysis:** Monthly/seasonal trends, event-specific breakdowns  
- **Deployment:** Convert EDA into an **interactive dashboard (Streamlit, Dash, or PowerBI)**  

---
