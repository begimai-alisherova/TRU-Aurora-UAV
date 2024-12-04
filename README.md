# TRU-Aurora-UAV
Sagebrush Distribution Model for Aurora UAV

**Codes for South Thompson Area:**
1. checkClosestPixels.ipynb !!!RUN ON CAMPUS AND UPLOAD
This script processes large geospatial dataset to analyze missing values using a breadth-first search (BFS) approach. It calculates the distance to the nearest valid pixel for each missing value and generates a summary of the distance distribution. Using chunk-based processing, it outputs a distance summary for missing values (e.g., how many missing points are 1, 2, or more steps away).
2. checkCombinedGround.ipynb

3. displayCsv.ipynb
This file was used to display the summary for csv files and to check whether 2 files are similar or have any mismatched records.
4. replaceMissingValues.ipynb !!!RUN ON CAMPUS AND UPLOAD
This script processes large geospatial dataset to handle missing values by replacing them with the average of up to 8 nearest valid pixels using a breadth-first search (BFS) approach. It supports chunk-based processing for memory efficiency and removes rows where no valid neighbors are found within a search distance of 10 units. Outputs include a cleaned CSV file and a count of filled missing values.
5. NEWPIPELINE.ipynb
Final version of our pipeline that uses Random Forest to train and test on the ground truth data.
6. 
