Manila Flood Risk Mapping System
This project creates a flood risk mapping system for Manila, Philippines using geospatial data analysis and interactive visualization. The system processes geographical coordinates, flood height, elevation, and precipitation data to calculate and visualize flood risk through an interactive heat map.
Dataset
The data is sourced from the AEGIS Dataset available at https://www.kaggle.com/datasets/giologicx/aegisdataset. The CSV file contains latitude, longitude, flood height, elevation, and precipitation measurements for various locations in Manila.
Code Overview
The system begins by loading and cleaning the dataset, converting all numerical columns to proper data types and removing any rows with missing values. Data normalization is then applied to scale flood height, elevation, and precipitation values to a 0-1 range, with elevation values inverted since lower elevation typically indicates higher flood risk.
A weighted risk score is calculated using the formula: flood_height×0.4 + elevation×0.3 + precipitation×0.3. This score is then color-coded into five risk categories ranging from green (low risk, <0.2) to dark red (critical risk, >0.8), with yellow, orange, and red representing intermediate levels.
The final step creates an interactive Folium map centered on Manila coordinates with a heat map overlay displaying the calculated risk scores. The visualization includes radius and zoom parameters optimized for clear risk pattern identification across the metropolitan area.
Usage
This code must be executed in Google Colab to properly handle file uploads and display the interactive map. After running all cells and uploading the dataset when prompted, the system outputs detailed risk scores for each location and generates both an inline interactive map and an HTML file named 'manila_flood_risk_map.html' for offline viewing.
The resulting visualization provides urban planners and disaster management authorities with a comprehensive tool for identifying high-risk flood zones and supporting evidence-based decision making for flood mitigation strategies in Manila.
