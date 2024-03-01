# Human Activity Recognition Data Analysis

This repository contains an R script (`run_analysis.R`) for analyzing the Human Activity Recognition dataset from accelerometers in the Samsung Galaxy S smartphone.

## Script Overview

The `run_analysis.R` script performs the following tasks:

1. **Load Necessary Libraries**: The script begins by loading the `dplyr` library, which is essential for data manipulation.

2. **Download and Unzip Dataset**: The script downloads and unzips the Human Activity Recognition dataset from the specified URL.

3. **Load Data**: Loads features and activity labels, as well as training and test datasets, including measurements, activity labels, and subject information.

4. **Merge Training and Test Sets**: Merges the training and test sets to create a unified dataset.

5. **Extract Mean and Standard Deviation Measurements**: Extracts only the measurements related to mean and standard deviation for each feature.

6. **Use Descriptive Activity Names**: Applies descriptive activity names to the dataset.

7. **Label Dataset Appropriately**: Labels the dataset with descriptive variable names, making it more readable.

8. **Create Tidy Data Set**: Creates a tidy data set with the average of each variable for each activity and each subject.

9. **Write Tidy Data to File**: Writes the tidy data set to a file named `tidy_data.txt`.

## How to Use

To reproduce the analysis:

1. Clone this repository to your local machine:

