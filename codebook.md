The run_analysis.R script performs the data preparation and then followed by the 5 steps required as described in the course project’s definition.

A. Download the dataset
Dataset downloaded and extracted under the folder called UCI HAR Dataset

B. Assign each data to variables
features_names <- features.txt : 561 rows, 2 columns 
The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ.
activity_labels <- activity_labels.txt : 6 rows, 2 columns 
List of activities performed when the corresponding measurements were taken and its codes (labels)
Subject_test <- test/subject_test.txt : 2947 rows, 1 column 
contains test data of 9/30 volunteer test subjects being observed
X_test <- test/X_test.txt : 2947 rows, 561 columns 
contains recorded features test data
Y_test <- test/Y_test.txt : 2947 rows, 1 columns 
contains test data of activities’code labels
subject_train <- test/subject_train.txt : 7352 rows, 1 column 
contains train data of 21/30 volunteer subjects being observed
X_train <- test/X_train.txt : 7352 rows, 561 columns 
contains recorded features train data
Y_train <- test/y_train.txt : 7352 rows, 1 columns 
contains train data of activities’code labels

1. Merges the training and the test sets to create one data set
X_total (10299 rows, 561 columns) is created by merging x_train and x_test using rbind() function
Y_total (10299 rows, 1 column) is created by merging y_train and y_test using rbind() function
Subject_total (10299 rows, 1 column) is created by merging subject_train and subject_test using rbind() function

2. Extracts only the measurements on the mean and standard deviation for each measurement
selected_var (10299 rows, 88 columns) is created by subsetting features, selecting only columns which has  mean and standard deviation (std) for each measurement.

3. Uses descriptive activity names to name the activities in the data set
Activity labels and activities have been encoded and set into Y_Total.

4. Appropriately labels the data set with descriptive variable names
Variable names have been set as columns into X_total.

5. From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject
Total(180 rows, 88 columns) is created by merging , X_total, activitylabels and Subject_total using cbind() function
Total_mean is created by sumarizing total means of each variable for each activitylabel and each subject, after grouped by subject and activity.
Export Total_mean into tidydata.txt file.