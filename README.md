Manila Flood Risk Mapping System
An interactive geospatial analysis tool for visualizing and assessing flood risk across Manila, Philippines.
Overview
This project implements a comprehensive flood risk mapping system that processes geographical and meteorological data to generate interactive visualizations of flood-prone areas in Manila. The system combines multiple risk factors including terrain elevation, historical flood heights, and precipitation patterns to produce actionable risk assessments for urban planning and disaster management.
Features

Multi-factor Risk Analysis: Integrates flood height, elevation, and precipitation data
Interactive Visualization: Heat map overlay on an interactive Folium map
Risk Categorization: Five-tier color-coded risk levels (Low to Critical)
Exportable Maps: Generates standalone HTML files for offline viewing
Data Normalization: Standardized scoring system for consistent risk assessment

Dataset
The project utilizes the AEGIS Dataset, which contains comprehensive geospatial and meteorological measurements for Manila:

Source: AEGIS Dataset on Kaggle
Data Points: Latitude, Longitude, Flood Height, Elevation, Precipitation
Coverage: Metropolitan Manila area

Methodology
Data Processing

Data Cleaning: Converts all numerical columns to appropriate data types and removes incomplete records
Normalization: Scales all measurements to a 0-1 range for consistent comparison
Elevation Inversion: Lower elevations receive higher risk scores (inverted scaling)

Risk Calculation
The system calculates a weighted composite risk score using the following formula:
Risk Score = (Flood Height × 0.4) + (Elevation × 0.3) + (Precipitation × 0.3)
Weighting Rationale:

Flood Height (40%): Primary indicator of actual flood risk
Elevation (30%): Topographical vulnerability factor
Precipitation (30%): Meteorological risk contributor

Risk Categories
CategoryScore RangeColorDescriptionLow< 0.2GreenMinimal flood riskModerate0.2 - 0.4YellowSome risk during heavy rainfallHigh0.4 - 0.6OrangeSignificant flood potentialVery High0.6 - 0.8RedHigh vulnerabilityCritical> 0.8Dark RedExtreme flood risk
Installation & Usage
Requirements

Python 3.7+
Google Colab (recommended) or Jupyter Notebook
Required libraries: pandas, folium, numpy
