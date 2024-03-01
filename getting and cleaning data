# 1. Load library
library(dplyr)

# 2. Download and unzip the dataset
url <- "https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip"
download.file(url, destfile = "UCI_HAR_Dataset.zip")
unzip("UCI_HAR_Dataset.zip")

# 3. Load the data
# Load features and activity labels
features <- read.table("UCI HAR Dataset/features.txt", col.names = c("feature_id", "feature_name"))
activity_labels <- read.table("UCI HAR Dataset/activity_labels.txt", col.names = c("activity_id", "activity_name"))

# Load training data
train_x <- read.table("UCI HAR Dataset/train/X_train.txt", col.names = features$feature_name)
train_y <- read.table("UCI HAR Dataset/train/y_train.txt", col.names = "activity_id")
train_subject <- read.table("UCI HAR Dataset/train/subject_train.txt", col.names = "subject_id")

# Load test data
test_x <- read.table("UCI HAR Dataset/test/X_test.txt", col.names = features$feature_name)
test_y <- read.table("UCI HAR Dataset/test/y_test.txt", col.names = "activity_id")
test_subject <- read.table("UCI HAR Dataset/test/subject_test.txt", col.names = "subject_id")

# 4. Merge the training and test sets
merged_x <- rbind(train_x, test_x)
merged_y <- rbind(train_y, test_y)
merged_subject <- rbind(train_subject, test_subject)

# 5. Extract only the mean and standard deviation measurements
selected_features <- features[grep("mean\\(\\)|std\\(\\)", features$feature_name), ]
selected_columns <- c("subject_id", "activity_id", selected_features$feature_name)
merged_data <- cbind(merged_subject, merged_y, merged_x[, selected_features$feature_id])

# 6. Use descriptive activity names
merged_data <- merge(merged_data, activity_labels, by = "activity_id", all.x = TRUE)
merged_data$activity_name <- as.factor(merged_data$activity_name)

# 7. Appropriately label the data set
names(merged_data) <- gsub("^t", "time_", names(merged_data))
names(merged_data) <- gsub("^f", "frequency_", names(merged_data))
names(merged_data) <- gsub("\\()", "", names(merged_data))
names(merged_data) <- gsub("-", "_", names(merged_data))

# 8. Create a tidy data set with the average of each variable for each activity and each subject
tidy_data <- merged_data %>%
  group_by(subject_id, activity_name) %>%
  summarise_all(mean)

# 9. Write the tidy data set to a file
write.table(tidy_data, "tidy_data.txt", row.names = FALSE)
