This project is dedicated to calculating a quantitative, composite Flood Risk Score for a target geographical region, using data points from the AEGIS dataset (Manila). Instead of relying on a single vulnerability factor, the final score combines multiple critical elements influencing flood risk.

Core Logic Stages

Data Preparation and Cleaning: Data is loaded, and critical features (latitude, longitude, flood_heig, elevation, precipitat) are converted to numeric types. Rows with missing values in these features are removed.

Feature Engineering: The Slope of the terrain is calculated for each data point using the k-nearest neighbors method. A full implementation should also include calculating the Distance to River using the osmnx and geopandas libraries.

Normalization: All features are scaled to a 0-to-1 range. Features where a low value indicates high risk (such as Elevation and Slope) are mathematically inverted (1 - score) so that for all final inputs, a higher value consistently represents a higher risk.

Automated Weight Assignment: Weights for the normalized features are automatically assigned using an Inverse Correlation method. This technique assigns higher weights to features that show less correlation with the other independent variables, thus aiming to reduce multicollinearity and ensure each feature contributes unique information to the final score.

Final Risk Score Calculation: The final Risk Score is computed as a weighted average of the normalized and weighted input features.

Prerequisites
The Anaconda or Miniconda distribution is required to manage Python environments and correctly install complex geospatial libraries like geopandas and osmnx. These instructions are tailored for a Windows operating system.

Execution Steps

Step 1: Create and Activate a Clean Environment
Open the Anaconda Prompt (search for it in the Windows Start Menu) and execute the following commands to set up a dedicated Python environment:

conda create -n flood_env python=3.10
conda activate flood_env
conda install -c conda-forge pandas numpy scipy jupyter geopandas osmnx

Step 3: Run the Jupyter Notebook
Once installation is complete, navigate to the project directory using the Anaconda Prompt (e.g., cd C:\Users\YourName\MyProjectFolder) and launch the Jupyter Notebook from the same active environment:

jupyter notebook

Open the project's .ipynb file, ensure the flood_env kernel is selected, and execute the code cells sequentially. The code will perform all data processing and calculate the final risk score.
