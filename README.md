# SpaceX Launch Data Analysis

## Introduction

![SpaceX Launch](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DS0701EN-SkillsNetwork/api/Images/landing_1.gif)

## Table of Contents

- [Background](#background)
- [Project Goals](#project-goals)
- [Executive Summary](#executive-summary)
- [Results](#results)
  - [Exploratory Data Analysis](#exploratory-data-analysis)
  - [Visualization / Analytics](#visualization--analytics)
  - [Predictive Analytics](#predictive-analytics)
- [Methodology](#methodology)
  - [Data Collection - API](#data-collection---api)
  - [Data Collection - Web Scraping](#data-collection---web-scraping)
  - [Data Wrangling](#data-wrangling)
  - [EDA with Visualization](#eda-with-visualization)
  - [EDA with SQL](#eda-with-sql)
  - [Maps with Folium](#maps-with-folium)
  - [Dashboard with Plotly Dash](#dashboard-with-plotly-dash)
  - [Predictive Analytics](#predictive-analytics)
- [Conclusion](#conclusion)

## Background

SpaceX, a leader in the space industry, is revolutionizing space travel by making it more affordable and accessible. Its achievements include:

- Sending spacecraft to the International Space Station.
- Launching a satellite constellation for internet access.
- Conducting manned space missions.

A significant factor in SpaceX's cost efficiency ($62 million per launch) is the reuse of the first stage of its Falcon 9 rocket, compared to the $165 million per launch cost for other providers who do not reuse rocket stages. By predicting the landing outcome of the first stage, we can estimate the cost of a launch.

## Project Goals

- Explore how payload mass, launch site, number of flights, and orbits affect first-stage landing success.
- Analyze the rate of successful landings over time.
- Determine the best predictive model for successful landings using binary classification.

## Executive Summary

This research aims to identify factors contributing to a successful rocket landing. The following methodologies were employed:

- **Data Collection:** Using SpaceX REST API and web scraping techniques.
- **Data Wrangling:** Creating a success/fail outcome variable.
- **Exploratory Data Analysis (EDA):** Using visualization techniques to analyze factors such as payload, launch site, flight number, and yearly trends.
- **Data Analysis with SQL:** Calculating total payload, payload range for successful launches, and the number of successful and failed outcomes.
- **Launch Site Success Analysis:** Exploring success rates and proximity to geographical markers.
- **Visualization:** Identifying the most successful launch sites and payload ranges.
- **Predictive Modeling:** Using logistic regression, support vector machine (SVM), decision tree, and K-nearest neighbor (KNN) to predict landing outcomes.

## Results

### Exploratory Data Analysis

- Launch success has improved over time.
- KSC LC-39A has the highest success rate among landing sites.
- Orbits ES-L1, GEO, HEO, and SSO have a 100% success rate.

### Visualization / Analytics

- Most launch sites are near the equator and close to the coast.

### Predictive Analytics

- All models performed similarly on the test set. The decision tree model slightly outperformed others based on the best score.

## Methodology

### Data Collection - API

- **Request Data:** Fetch rocket launch data from the SpaceX API.
- **Decode Response:** Convert the JSON response to a DataFrame using `.json_normalize()`.
- **Request Launch Information:** Use custom functions to gather detailed launch information.
- **Create Dictionary:** Organize the data into a dictionary format.
- **Create DataFrame:** Convert the dictionary to a DataFrame.
- **Filter Data:** Focus on Falcon 9 launches.
- **Handle Missing Values:** Replace missing payload mass values with the mean.
- **Export Data:** Save the DataFrame to a CSV file.

### Data Collection - Web Scraping

- **Request Data:** Fetch Falcon 9 launch data from Wikipedia.
- **Create BeautifulSoup Object:** Parse the HTML response.
- **Extract Column Names:** Identify column names from the HTML table header.
- **Collect Data:** Parse and organize HTML table data into a dictionary.
- **Create DataFrame:** Convert the dictionary to a DataFrame.
- **Export Data:** Save the DataFrame to a CSV file.

### Data Wrangling

- **Convert Outcomes:** Encode landing outcomes as binary values (1 for success, 0 for failure).

### EDA with Visualization

- **Create Charts:** Visualize relationships and comparisons in the data.

### EDA with SQL

- **Query Data:** Use SQL to derive insights from the data.

### Maps with Folium

- **Create Maps:** Visualize launch sites, launch outcomes, and proximities.

### Dashboard with Plotly Dash

- **Create Dashboard:**
  - Pie chart showing successful launches.
  - Scatter chart showing Payload Mass vs. Success Rate by Booster Version.

### Predictive Analytics

- **Prepare Data:** Create a NumPy array from the class column and standardize it using `StandardScaler`.
- **Split Data:** Use `train_test_split` to create training and test sets.
- **Optimize Models:** Use `GridSearchCV` with cross-validation (cv=10) for parameter tuning.
- **Apply Models:** Train logistic regression, SVM, decision tree, and KNN models.
- **Evaluate Models:** Calculate accuracy, confusion matrix, Jaccard score, F1 score, and overall accuracy.

## Conclusion

- **Model Performance:** The decision tree model slightly outperformed other models on the test set.
- **Equatorial Advantage:** Most launch sites are near the equator, leveraging Earth's rotational speed.
- **Coastal Proximity:** All launch sites are close to the coast for logistical advantages.
- **Launch Success:** Success rates have improved over time.
- **KSC LC-39A:** This launch site has the highest success rate, especially for payloads under 5,500 kg.
- **Orbit Success Rates:** Orbits ES-L1, GEO, HEO, and SSO have a 100% success rate.
- **Payload Mass Correlation:** Higher payload masses correlate with higher success rates.
