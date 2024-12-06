# TRU-Aurora-UAV
Sagebrush Distribution Model for Aurora UAV

This repository contains the code and methodologies developed by a team of four TRU students to create a machine learning-based predictive model for sagebrush presence or absence, tailored for Aurora UAV.

### Summary of Our Codes:

- pullingInfoFromCsv.ipynb

This script processes large geospatial TIFF files to extract valid pixel values along with their geographic coordinates. Using rasterio, it reads TIFF data in memory-efficient chunks, replaces no data values with NaN, and writes the latitude, longitude, and pixel values for non-NaN pixels to a CSV file. Designed for large datasets, it ensures efficient processing and outputs a CSV with valid geospatial data.

- mergingCsvs.ipynb

This script merges multiple CSV files containing geospatial data into a single CSV. It uses Dask for efficient handling of large datasets, ensuring memory optimization. Each file is processed by renaming the third column to a unique name based on the filename, and then all files are merged on Latitude and Longitude columns. The resulting merged data is saved to a new CSV file for further analysis.

- deletingMissingValues.ipynb

The code processes large CSV files in chunks to handle missing values efficiently. The first part identifies missing values by counting rows and columns with missing data and provides a summary of their distribution. The second part removes rows with missing values, saving the cleaned dataset incrementally to a new file. This approach ensures memory efficiency while working with large datasets.

- averaging8Closest.ipynb

This script processes a large CSV file in chunks to handle missing values for specific features. For rows with missing data, it calculates the average of the surrounding 8 coordinates based on Latitude and Longitude. The processed data is written to a new file incrementally, ensuring efficient memory usage. The script also tracks the total number of missing values filled and logs details about rows with unavailable surrounding data.

- averaging8ClosestBFS.ipynb

This script processes large geospatial dataset to handle missing values by replacing them with the average of up to 8 nearest valid pixels using a breadth-first search (BFS) approach. It supports chunk-based processing for memory efficiency and removes rows where no valid neighbors are found within a search distance of 10 units. Outputs include a cleaned CSV file and a count of filled missing values.

- checkClosestPixels.ipynb 

This script processes large geospatial dataset to analyze missing values using a breadth-first search (BFS) approach. It calculates the distance to the nearest valid pixel for each missing value and generates a summary of the distance distribution. Using chunk-based processing, it outputs a distance summary for missing values (e.g., how many missing points are 1, 2, or more steps away).

- checkCombinedGround.ipynb

This script checks ground truth coordinates against a combined CSV file containing features. It verifies the presence of ground truth points, identifies missing features for those points, and counts points not found in the combined file. The output summarizes points with complete data, missing features, or absence from the dataset, enabling detailed validation of geospatial data completeness and quality.

- NEWPIPELINE.ipynb

Final version of our pipeline. The code implements a machine learning pipeline using a Random Forest classifier for geospatial data. It begins by merging a ground truth dataset with a larger dataset on Latitude and Longitude. The merged data is preprocessed by separating features and target labels, scaling the features, and splitting the data into training and testing sets. The Random Forest model is trained on the training data, and its accuracy is evaluated on the test set. Feature importance is calculated and ranked to identify the most influential features. Further, the pipeline includes feature selection using statistical methods (e.g., ANOVA F-value) to optimize the input features. The model is retrained using the selected features, and additional features are incorporated iteratively to improve accuracy. Then, hyperparameter tuning with GridSearchCV is used for optimization. The tuned model is evaluated on metrics such as accuracy, precision, recall, and F1-score, with a classification report providing detailed performance insights.


If there are any questions regarding any of these codes, please contact us.
