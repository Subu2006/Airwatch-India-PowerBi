# 🌫️ AirWatch India — Power BI Air Quality Analytics Dashboard

> An interactive Power BI project for exploring historical city-level and monitoring-station air-quality patterns across India from 2015 to 2020.

**Technologies:** Power BI Desktop · Power Query (M) · DAX · Power BI Project (PBIP) · TMDL

<!-- Add a high-quality dashboard screenshot after completing the final validation. -->
<!--
![AirWatch India — National Overview](assets/screenshots/01-national-overview.png)
-->

## 📌 Project Overview

AirWatch India is an interactive data analytics and business intelligence project developed using Microsoft Power BI.

The project transforms historical air-quality datasets into an interactive, multi-page dashboard designed to help users explore pollution patterns, compare cities and states, analyze pollutant measurements, and investigate individual monitoring stations.

The dashboard provides a structured way to examine air-quality patterns through charts, KPIs, geographic analysis, rankings, filters, and station-level drill-through.

The project covers the complete reporting workflow, including data preparation, data modeling, analytical calculations, visualization, and interactive reporting.

**Project objective:** To transform historical air-quality data into an accessible, organized, and informative analytical experience.

**Project scope:** This is a retrospective analysis of historical data, not a live AQI monitoring service, forecasting system, or public-health advisory.

## 🎯 Project Objectives

- Analyze historical Air Quality Index (AQI) patterns across Indian cities.
- Compare AQI measurements across years, months, and seasons.
- Explore the concentrations of selected air pollutants.
- Identify cities and states with comparatively high recorded AQI values.
- Examine air-quality measurements at individual monitoring stations.
- Build an interactive dashboard using Power BI.
- Apply data cleaning, transformation, dimensional modeling, and DAX calculations.
- Improve the accessibility and interpretation of air-quality information through data visualization.

## 📊 Dashboard Pages

The report is organized into five analytical pages.

### 1. National Overview

Provides a high-level summary of the available city-level air-quality records.

**Key features:**
- Total observations
- Number of distinct cities
- Number of monitoring stations
- Average AQI
- Maximum recorded AQI
- Historical AQI trend
- Top 10 cities ranked by average AQI
- AQI-category distribution
- Interactive slicers and navigation

### 2. Temporal Patterns

Explores changes in recorded AQI over time.

**Key features:**
- Monthly AQI patterns across years
- Seasonal AQI comparison
- Year-over-year analysis
- City-by-year AQI matrix
- Conditional formatting for easier comparison
- Year, city, and season filters

### 3. Pollutant Intelligence

Focuses on selected pollutant measurements and their relationships.

**Pollutants analyzed:**
- PM2.5
- PM10
- NO2
- SO2
- CO
- O3

**Key features:**
- Average pollutant measurements
- Monthly PM2.5 trend
- PM2.5 versus PM10 comparison across cities
- AQI-category distribution
- Interactive city and year filters

### 4. Geographic Hotspots

Provides geographic and comparative analysis of city, state, and monitoring-station data.

**Key features:**
- City AQI rankings
- State-level station AQI comparison
- City hotspot summary table
- Monitoring-station location visualization
- Station selection
- Geographic and time-based filtering

### 5. Station Deep Dive

Provides a more detailed view of an individual monitoring station.

**Key features:**
- Station identification
- Average station AQI
- Maximum station AQI
- Station observation count
- Selected pollutant measurements
- Station AQI trend over time
- Yearly AQI summary
- Drill-through navigation

The Station Deep Dive page is designed to display station-specific results when a station is selected through drill-through.

## 🛠️ Technologies and Tools

| Technology | Purpose |
|---|---|
| Microsoft Power BI Desktop | Dashboard development and visualization |
| Power Query (M) | Data preparation, cleaning, and transformation |
| DAX | Analytical measures, rankings, percentages, and time calculations |
| Dimensional data modeling | Organizing city-level and station-level data |
| PBIP | Power BI project file structure |
| TMDL | Semantic-model definition and inspection |
| GitHub | Source control, project documentation, and portfolio presentation |

## 🗂️ Data Sources

The principal dataset is **Air Quality Data in India (2015–2020)**, available on Kaggle.

**Dataset:**  
https://www.kaggle.com/datasets/rohanrao/air-quality-data-in-india

The project uses the following files:

| File | Purpose |
|---|---|
| `city_day.csv` | City-level daily air-quality observations |
| `station_day.csv` | Monitoring-station-level daily observations |
| `stations.csv` | Station metadata |
| `StationCoordinates.csv` | Additional station coordinates and location-related information |

The coordinate enrichment file should be used and redistributed only in accordance with its source terms and documented provenance.

### Data Coverage

The current development files contain the following raw records:

| File | Raw records |
|---|---:|
| `city_day.csv` | 29,531 |
| `station_day.csv` | 108,035 |
| `stations.csv` | 230 |
| `StationCoordinates.csv` | 230 |

The current city-day data contains 26 distinct cities and covers dates from **1 January 2015 through 1 July 2020**.

The station-day file contains 110 distinct `StationId` values in this project copy, while the station metadata contains 230 records.

These figures represent different aspects of the data and should not be interpreted as interchangeable counts.

Dashboard totals may differ from raw CSV record counts because of data transformations and filtering.

## 🧹 Data Preparation and Power Query

Power Query is used to prepare the source data before it enters the analytical model.

The preparation workflow includes:

- Promoting column headers.
- Standardizing data types.
- Converting dates to the appropriate date type.
- Converting pollutant measurements to numeric types.
- Standardizing AQI fields.
- Cleaning text values using Trim and Clean transformations.
- Standardizing station identifiers.
- Removing duplicate station metadata records where appropriate.
- Filtering rows with no usable AQI or pollutant measurements.
- Enriching station metadata with geographic coordinates.
- Creating date-related analytical attributes.
- Supporting missing-value handling and data-quality checks.

The transformation steps are implemented using Power Query M.

For reproducibility, the source paths should be parameterized rather than tied to an individual computer.

## 🧮 DAX and Analytical Calculations

DAX is used to calculate the summary statistics and analytical indicators displayed in the dashboard.

The analytical model includes measures for:

### Core Metrics
- Total observations
- Distinct cities
- Distinct stations
- Station observations

### AQI Analysis
- Average AQI
- Maximum AQI
- Minimum AQI
- Station-level AQI summaries

### Pollutant Analysis
- Average PM2.5
- Average PM10
- Average NO2
- Average SO2
- Average CO
- Average O3

### Comparative Analysis
- City AQI rankings
- City PM2.5 rankings
- AQI-category percentages
- Year-over-year comparisons
- Year-to-date calculations

### Station-Level Analysis
- Average station AQI
- Maximum station AQI
- Station observation counts
- Station pollutant measurements
- Station-specific display measures

The report also uses calculated columns for AQI category ordering and additional analytical classification.

## 🏗️ Data Model

The semantic model separates city-level observations from station-level observations.

The model contains the following principal tables:

| Table | Purpose |
|---|---|
| `FactCityDay` | Daily city-level AQI and pollutant observations |
| `FactStationDay` | Daily monitoring-station AQI and pollutant observations |
| `DimDate` | Date, year, month, quarter, season, and other calendar attributes |
| `DimCity` | City and state information |
| `DimStation` | Station identifiers, station names, geography, and metadata |
| `_Measures` | Central location for DAX measures |

A staging query is also used to prepare station-coordinate information before it is incorporated into the station dimension.

### Model Structure

```text
                    DimDate
                   /       \
                  /         \
                 v           v
          FactCityDay    FactStationDay
              ^               ^
              |               |
           DimCity         DimStation
```

The intended relationships include:

- `DimDate[Date]` → `FactCityDay[Date]`
- `DimDate[Date]` → `FactStationDay[Date]`
- `DimCity[City]` → `FactCityDay[City]`
- `DimCity[City]` → `DimStation[City]`
- `DimStation[StationId]` → `FactStationDay[StationId]`

The two fact tables should not be directly related to each other.

The model is designed to keep city-level analysis and station-level analysis distinct while allowing common dimensions to support filtering and comparison.

## 🎛️ Interactivity and User Experience

The report uses Power BI features to make the analysis easier to explore.

These include:

- Interactive slicers
- Synchronized filters across report pages
- Page-navigation buttons
- Clear-all-slicers actions
- Cross-filtering between visuals
- Conditional formatting
- AQI severity color coding
- Tooltips
- Station-level drill-through
- Back navigation

AQI categories are presented in severity order rather than alphabetical order.

The intended category sequence is:

1. Good
2. Satisfactory
3. Moderate
4. Poor
5. Very Poor
6. Severe

## 🎨 Visualization and Design

The dashboard uses a consistent visual design across its pages.

The design emphasizes:

- Clear page titles
- KPI cards for key indicators
- Consistent visual hierarchy
- Readable chart titles and labels
- Appropriate chart types for comparisons
- AQI-category colors
- Consistent page navigation
- Interactive filtering
- Separation of high-level summaries from detailed analysis

The objective is to make the report understandable to users who want either a quick overview or a deeper investigation of a particular location.

## ⚠️ Data Quality and Limitations

The results should be interpreted in the context of the source data and its limitations.

### Historical Data

The project uses historical observations ending on 1 July 2020.

Therefore, 2020 represents a partial year. Comparisons between 2020 and complete calendar years should account for the difference in coverage.

The dashboard should not be described as a live air-quality monitoring system.

### AQI Validation

The current report export displays a maximum AQI value of **2,049**.

This value is outside the 0–500 AQI-category ranges used in the report. It should be investigated before being interpreted or presented as a valid AQI result.

Potential causes should be checked against the original data, transformations, and calculation logic rather than assumed.

### Missing Values

Missing AQI and pollutant measurements can affect averages, rankings, and comparisons.

Where imputation or missing-value handling is used, the method should be documented and its effect on the results considered.

### Monitoring-Station Coverage

The station metadata contains 230 records, whereas the current station-day file contains 110 distinct station identifiers.

These figures represent different things. The number of metadata records should not automatically be treated as the number of stations with observations in the selected period.

### Geographic Coordinates

Station locations depend on the quality and provenance of the coordinate data.

Coordinates should be validated before the map is used to make location-specific claims.

### Interpretation

This project is intended for educational purposes, portfolio demonstration, and exploratory data analysis.

It should not replace official current air-quality readings, scientific validation, or public-health guidance.

## 🚀 How to Open the Project

The public repository is intended to contain the Power BI project source and documentation rather than raw data by default.

To reproduce the project:

1. Install Microsoft Power BI Desktop.
2. Obtain the source dataset from the original dataset page.
3. Review the source dataset's current terms and attribution requirements.
4. Place the required CSV files in a local data folder.
5. Open the PBIP project in Power BI Desktop.
6. Open **Home → Transform data → Manage parameters**.
7. Set the data-folder parameter to the full path of your local data folder.
8. Select **Close & Apply**.
9. Refresh the model.
10. Review the report pages and check for query or visual errors.
11. Validate AQI values, station coverage, and geographic coordinates.
12. Test slicers, interactions, and drill-through behavior.

The exact file and folder names must match the paths expected by the Power Query queries.

The public project should use a placeholder or parameterized data path rather than a personal path such as `C:\Users\...`.

## 📁 Repository Structure

The recommended repository structure is:

```text
airwatch-india-powerbi/
│
├── README.md
├── .gitignore
│
├── docs/
│   ├── DATA_SOURCES.md
│   ├── METHODOLOGY.md
│   └── RELEASE_CHECKLIST.md
│
├── assets/
│   └── screenshots/
│       ├── 01-national-overview.png
│       ├── 02-temporal-patterns.png
│       ├── 03-pollutant-intelligence.png
│       ├── 04-geographic-hotspots.png
│       └── 05-station-deep-dive.png
│
└── PowerBI/
    ├── AIRWATCHINDIA.pbip
    ├── AIRWATCHINDIA.Report/
    └── AIRWATCHINDIA.SemanticModel/
```

Keep the PBIP report and semantic-model folder structure intact.

Do not commit local Power BI settings, cache files, or personal file paths.

Raw CSV files and PBIX files containing embedded data should not be included in a public repository unless redistribution rights have been confirmed.

## 🔒 Data and Licensing

The principal dataset is credited to Rohan Rao and is available through Kaggle.

Dataset page:

https://www.kaggle.com/datasets/rohanrao/air-quality-data-in-india

Follow the dataset's current licence, terms, and attribution requirements.

The project repository should distinguish original project work from third-party data, coordinate information, visuals, and other assets.

Do not assume that a licence applied to this repository automatically grants redistribution rights for external datasets.

Choose an appropriate licence for original project files only after confirming the ownership and licensing of the included materials.

## 🔍 Future Improvements

Possible future improvements include:

- Investigating and documenting AQI values outside the intended category ranges.
- Validating the source and quality of station coordinates.
- Measuring the effect of missing-value handling on average AQI and rankings.
- Adding automated data-quality checks.
- Improving geographic visualizations.
- Documenting DAX measures and their intended filter behavior.
- Further optimizing Power Query transformations and model performance.
- Expanding automated validation of relationships and slicer interactions.
- Publishing a validated dashboard preview.

These are potential improvements rather than claims that all of them have already been implemented.

## 👨‍💻 Author

**Subrat Panigrahi**

B.Tech Computer Science Engineering Student

Interests: Data Analytics, Business Intelligence, Data Visualization, and Software Development.

GitHub: https://github.com/Subu2006

## 💬 Feedback

Feedback on the data model, DAX measures, Power Query transformations, visual design, and data-quality validation is welcome.

If you identify an issue, please provide a clear description and, where possible, a reproducible example or screenshot.

---

**AirWatch India — Turning Historical Air-Quality Data into Interactive Insights.**
