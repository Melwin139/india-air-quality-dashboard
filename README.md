# India Air Quality Dashboard: Live AQI by City

A live dashboard showing air quality and weather for 15 major Indian cities. It calculates the **Indian National AQI (CPCB scale)** from 24-hour average PM2.5 and PM10, ranks cities from cleanest to most polluted, and charts the PM2.5 trend for the past 24 hours plus the next 24-hour forecast.

**Live demo:** https://melwin139.github.io/india-air-quality-dashboard/

## Features

- **Indian AQI calculation** using CPCB National AQI breakpoints (Good → Severe), not the US AQI most apps show
- **Health advice** for each AQI category
- **AQI gauge**, PM2.5 / PM10 24-hour averages and main pollutant
- **24h + 24h trend chart** drawn on `<canvas>` with colour bands for each category, plus a "now" marker
- **City ranking**: 15 cities fetched in a single API call and sorted cleanest to most polluted; tap a city to view it
- **"My location"** using the browser Geolocation API
- Current weather (condition, temperature, humidity, wind), auto-refresh every 30 minutes, error handling, mobile layout

## Tech

Vanilla JavaScript (async/await, `fetch`, `Promise.all`, Canvas 2D), HTML5 and CSS3. No frameworks, no API key. Data comes from the free [Open-Meteo](https://open-meteo.com) Air Quality and Weather APIs (CAMS model).

## How the AQI is calculated

For each pollutant, the 24-hour average concentration is mapped onto the CPCB breakpoint table with linear interpolation:

```
AQI = (I_high − I_low) / (C_high − C_low) × (C − C_low) + I_low
```

The overall AQI is the higher of the PM2.5 and PM10 sub-indices.

> Values are model-based estimates for learning and planning, not official CPCB station readings.

## Run locally

Open `index.html` in a browser (an internet connection is needed for live data).

## Author

**Melwin Naigam**, Web Developer, Pune · [Portfolio](https://melwin139.github.io) · [LinkedIn](https://www.linkedin.com/in/melwinaigam)
