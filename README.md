# Rain-Traffic

**Rain-Traffic** is a data-driven project exploring how rainfall patterns affect traffic congestion, speed, and accident rates in Hyderabad, India. It integrates real weather and traffic data, builds predictive models (using machine learning), and visualizes results with a custom interactive dashboard.

---

## Overview

During the monsoon season, Hyderabad experiences significant disruptions in daily traffic, travel speed, and accident rates. This project:

- Analyzes multiple years of rainfall and traffic data at the city’s mandal (sub-district) level.
- Uses statistical and machine learning methods to explore the relationship between weather patterns and traffic flow.
- Presents interactive, “newspaper-style” visualizations for public and research use.

---

## Main Features

- **Interactive Dashboard:**  
  A rich, newspaper-like dashboard (see `Data1.html`) provides engaging visualizations:
  - **Rainfall vs Traffic Congestion:** Shows how rising rainfall decreases average traffic speeds.
  - **Peak Hour Impacts:** Compares dry vs rainy day speeds hour-by-hour.
  - **Rain Intensity vs Speed:** Boxplots show the drop in speed for heavy, moderate, light rain.
  - **Monsoon Accidents:** Stacked charts show minor, severe, fatal accidents by month.
  - **Spatial Analysis:** Map pins highlight neighborhoods most affected.
  - **Travel Delay Estimates:** Gauge shows average monsoon traffic delay.
  - **Seasonal Trends:** Multi-year line charts track both rainfall and speed.

- **Machine Learning Model:**  
  The core analysis (see `Eml_Project.ipynb`) uses a Random Forest Classifier to predict congestion/accident risk from weather features (rainfall, temperature, humidity, wind) across Hyderabad’s mandals.

- **Open, Annotated Data Science Notebook:**  
  The Jupyter Notebook (`Eml_Project.ipynb`) walks through all preprocessing, exploratory data analysis (EDA), visualization, and model building.

---

## Model & Workflow Details (From `Eml_Project.ipynb`)

### 1. Data Sources

- **Weather Data:** Multi-year, daily weather and rainfall for all Hyderabad mandals (from `Hyderabad_Weather_Data.xlsx`).
- **Geospatial Data:** Mandal boundaries from a GeoJSON file (`HYDERABAD.geojson`).

### 2. Exploratory Data Analysis & Visualization

- **Data Inspection:**  
  - Loads >8000 daily records across 16 mandals.
  - Shows trends in rainfall, temperature, humidity, and wind.
  - Plots monthly rainfall, average rainfall by mandal, and highlights patterns using matplotlib/seaborn.

- **Spatial Mapping (GeoPandas):**  
  - Reads spatial polygons for mandals.
  - Prepares data for geospatial overlays.

### 3. Feature Engineering

Key weather predictors from the dataset:
- Rain (mm)
- Max/Min Temperature
- Max/Min Humidity
- Max/Min Wind Speed

Time-based features (year, month, season) and mandal dummies are created to improve model performance.

### 4. Machine Learning Model

- **Type:** Random Forest Classifier (scikit-learn)
- **Target:** (Typically congestion class or accident risk—expand as desired)
- **Workflow:**
  - Split data into training and testing sets.
  - Fit the Random Forest model.
  - Evaluate with metrics: accuracy, confusion matrix, and classification report.
  - Feature importance: Model outputs most influential weather factors.

**Why Random Forest?**  
It’s robust to non-linear relationships and handles diverse weather features well.

**Possible Extensions:**  
Introduce regression models for predicting average traffic speed directly, or time-series methods for short-term traffic forecasting.

---

## How to Run

1. **Clone this repo:**  
   ```bash
   git clone https://github.com/Saketh875/Rain-Traffic.git
   ```
2. **Install required Python packages:**  
   - pandas, numpy, matplotlib, seaborn, scikit-learn, folium, geopandas, shapely, rtree
   - For Colab:  
     ```python
     !pip install geopandas folium scikit-learn matplotlib seaborn pyproj rtree
     ```
3. **Open and run `Eml_Project.ipynb`** in Jupyter or Google Colab.

4. **View Dashboard:**  
   Open `Data1.html` in any web browser for full data exploration and “storytelling”.

---

## Project Structure

- **Eml_Project.ipynb**: All code for loading data, cleaning, EDA, model building, and maps.
- **Data1.html**: Main dashboard, newspaper-style layout, interactive charts and map.
- **hyderabad_traffic_flow_map (2).html**: Detailed traffic flow visualization using Leaflet.
- **HYDERABAD.geojson**, **Hyderabad_Weather_Data.xlsx**: (Not stored on GitHub, add as needed for full analysis.)
- **image & reports**: Reference images and result plots.

---

## Acknowledgements

- Rainfall and weather data courtesy of Hyderabad Meteorological Department.
- Mapping by OpenStreetMap and Folium/Leaflet.
- Dashboard styled for readability and outreach.

---

## License

This project is for research and demonstration. Attribution welcome if reused or modified.

---

*Maintained by [Saketh875](https://github.com/Saketh875).*
