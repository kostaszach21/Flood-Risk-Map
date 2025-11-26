# Manila Flood Risk Map 

## Project Overview
This project analyzes and visualizes flood risk in Manila using geospatial and meteorological data. The goal is to identify high-risk areas based on key environmental factors and present them in an interactive, accurate map.

## Key Features in 
*   **Grid-Based Visualization:** A major upgrade from standard heatmaps. The map now uses a grid system where each cell is colored based on the **maximum risk score** within it. This ensures that isolated high-risk points are clearly visible and not washed out by surrounding low-risk data.
*   **Composite Risk Score:** Calculates a weighted risk score (0-1) based on:
    *   **Elevation:** Lower elevation = Higher risk.
    *   **Precipitation:** Higher rainfall = Higher risk.
    *   **Flood Height:** Historical flood levels.
    *   **Slope:** Flatter terrain = Higher risk.
*   **Interactive Map:** A fully interactive HTML map with:
    *   Color-coded grid cells indicating risk intensity.
    *   Specific markers for "Danger Zones" (Risk Score > 0.8).
    *   A custom legend for easy interpretation.
*   **Data Analysis:** Includes scatter plots and correlation matrices to understand feature relationships.

## Methodology

### 1. Data Preprocessing
-   Loads `AEGISDataset.csv`.
-   Cleans missing values and converts columns to numeric types.
-   Normalizes features to a 0-1 scale.

### 2. Risk Calculation
-   **Slope Calculation:** Computes slope for each point using a vectorized approach with a KDTree for efficiency.
-   **Weighting:** Weights are derived dynamically from the inverse of the correlation matrix, giving more importance to unique (less correlated) features.
-   **Formula:** `Risk Score = Σ (Feature * Weight)`

### 3. Visualization (The Fix)
-   **Problem:** Standard heatmaps prioritize point density, often hiding isolated high-risk areas.
-   **Solution :** We implement a spatial grid (binning).
    -   The map is divided into ~500m x 500m cells.
    -   Each cell's color is determined by the **MAXIMUM** risk score of any point inside it.
    -   **Green:** Very Low Risk (< 0.2)
    -   **Yellow:** Low Risk (0.2 - 0.4)
    -   **Orange:** Medium Risk (0.4 - 0.6)
    -   **Red:** High Risk (0.6 - 0.8)
    -   **Dark Red:** Very High Risk (> 0.8)

## Usage

1.  **Prerequisites:**
    -   Python 3.x
    -   Libraries: `pandas`, `numpy`, `folium`, `scipy`, `seaborn`, `matplotlib`
2.  **Run the Analysis:**
    -   Open `Manilla_flood_risk_map_V6.ipynb` 
    -   Execute all cells.
3.  **View the Map:**
    -   Open the generated `Manila_Flood_Risk_Map_V6.html` in your web browser.

## Files
-   `Manilla_flood_risk_map_V6.ipynb`: The main Jupyter Notebook containing the code and analysis.
-   `AEGISDataset.csv`: The source dataset.
-   `Manila_Flood_Risk_Map_V6.html`: The generated interactive map.
