# 🌦 Power BI Weather Dashboard with WeatherAPI & AQI Indicators
## Overview
This project demonstrates how to build a **real-time weather dashboard** in **Power BI** using **WeatherAPI**. It visualizes weather parameters, air quality indices (AQI), and additional metrics in an interactive dashboard.

---

## Features
- **Live Weather Data** from WeatherAPI (Temperature, Humidity, Wind Speed, Pressure, etc.)
- **Air Quality Index (AQI) Visualization** with color coding
- **Custom DAX Measures** for reusable calculations
- **Interactive Dashboard** with cards, gauges, charts, and maps
- **Dynamic City Selection** for multiple locations

---

##  Project Setup
### Get WeatherAPI Key
- Sign up at [WeatherAPI.com](https://www.weatherapi.com/)  
- Copy your **API Key**

---

## 📊 Key DAX Measures
### Temperature & Update
```DAX
Curr_Temp_C = SUM('Current'[current.temp_c]) & " °C"
Curr_Temp_F = SUM('Current'[current.temp_f]) & " °F"
last_update = "Last Updated, " & FORMAT(FIRSTNONBLANK('Current'[current.last_updated], ""), "dd mmm yy")
```

### AQI Color & Status Example (PM10)
```DAX
AQI_Status_TEMPLATE = 
VAR AQI = ROUND(SELECTEDVALUE('Current'[current.air_quality.pm10]),0)
RETURN
SWITCH(
TRUE(),
AQI <= 50, "Good",
AQI <= 100, "Moderate",
AQI <= 150, "Unhealthy for Sensitive",
AQI <= 200, "Unhealthy",
AQI <= 300, "Very Unhealthy",
"Hazardous"
)

PM10_Color_TEMPLATE = 
VAR AQI = ROUND(SELECTEDVALUE('Current'[current.air_quality.pm10]),0)
RETURN
SWITCH(
TRUE(),
AQI <= 50, "#43d946",
AQI <= 100, "#fff570",
AQI <= 150, "#ff9800",
AQI <= 200, "#d99343",
AQI <= 300, "#ff5b0f",
"#d95243"
)
```

### Other Metrics
- **Humidity**  
- **Wind Speed**  
- **Visibility**  
- **Pressure**  
- **UV Index**  
- **Precipitation**  
- **Average Daily & Hourly Temperature**  
- **Rain Chance & AQI Suggestions**  

(Full DAX measures are included in the project.)

---

## 🎨 Dashboard Visuals
- **Cards**: Temperature, Humidity, AQI
- **Gauges**: Wind Speed, UV Index
- **Line & Bar Charts**: Daily & Hourly Trends
- **Map Visuals**: City-wise Weather Display
- **Conditional Formatting**: AQI Colors (Good → Hazardous)

---

## 🖼 Dashboard Preview
![Dashboard Screenshot](https://github.com/misba-coder/Power-BI-Weather-Dashboard-/blob/main/Screenshot1.png)

---

## 📝 Conclusion
By integrating **WeatherAPI** with **Power BI**, you can build a live weather dashboard with AQI visualizations and real-time updates, enhanced by reusable DAX measures for scalability and maintainability.

---

## 📧 Author
**Misba Khatoon**  
