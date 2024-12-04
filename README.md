# TRU-Aurora-UAV
Sagebrush Distribution Model for Aurora UAV

## Codes for South Thompson Area

### Data Preprocessing codes

- pullingInfoFromCsv.ipynb

This script processes large geospatial TIFF files to extract valid pixel values along with their geographic coordinates. Using rasterio, it reads TIFF data in memory-efficient chunks, replaces nodata values with NaN, and writes the latitude, longitude, and pixel values for non-NaN pixels to a CSV file. Designed for large datasets, it ensures efficient processing and outputs a CSV with valid geospatial data.

- mergingCsvs.ipynb

This script merges multiple CSV files containing geospatial data into a single CSV. It uses Dask for efficient handling of large datasets, ensuring memory optimization. Each file is processed by renaming the third column to a unique name based on the filename, and then all files are merged on Latitude and Longitude columns. The resulting merged data is saved to a new CSV file for further analysis.

- checkClosestPixels.ipynb 

This script processes large geospatial dataset to analyze missing values using a breadth-first search (BFS) approach. It calculates the distance to the nearest valid pixel for each missing value and generates a summary of the distance distribution. Using chunk-based processing, it outputs a distance summary for missing values (e.g., how many missing points are 1, 2, or more steps away).

- replaceMissingValues.ipynb

This script processes large geospatial dataset to handle missing values by replacing them with the average of up to 8 nearest valid pixels using a breadth-first search (BFS) approach. It supports chunk-based processing for memory efficiency and removes rows where no valid neighbors are found within a search distance of 10 units. Outputs include a cleaned CSV file and a count of filled missing values.

- checkCombinedGround.ipynb

This script checks ground truth coordinates against a combined CSV file containing features. It verifies the presence of ground truth points, identifies missing features for those points, and counts points not found in the combined file. The output summarizes points with complete data, missing features, or absence from the dataset, enabling detailed validation of geospatial data completeness and quality.

### Pipeline codes

- NEWPIPELINE.ipynb

Final version of our pipeline that uses Random Forest to train and test on the ground truth data.

- alternativePipeline.ipynb

This script implements a semi-supervised learning approach using labeled and unlabeled geospatial data. A Random Forest classifier is first trained on labeled data, evaluated, and then used to generate pseudo-labels for the unlabeled dataset. High-confidence pseudo-labels are identified and combined with the labeled data to retrain the model, improving its performance. The final model is evaluated on the labeled test set, and predictions are generated for the remaining unlabeled data. This method extends the training dataset using confident predictions, enhancing model accuracy with limited labeled data.


### Other Handy codes

- displayCsv.ipynb

This file was used to display the summary for csv files and to check whether 2 files are similar or have any mismatched records.

