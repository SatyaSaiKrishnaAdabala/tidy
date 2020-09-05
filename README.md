---
output: pdf_document
---
# tidy

# Synopsis

The attached R code performs the tasks of cleaning, transforming raw data into a tidy set to perform the analysis of various persons between the age of 19 - 48 years . Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING)

The source of the data is from Samsung Galaxy Smart Phone tied on the waist of each subject and with embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity

The data set for the analysis is downloaded from http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones 

# Objective:

1) Merges the training and the test sets to create one data set.
2) Extracts only the measurements on the mean and standard deviation for each measurement.
3) Uses descriptive activity names to name the activities in the data set
4) Appropriately labels the data set with descriptive activity names.
5) Creates a second, independent tidy data set with the average of each variable for each activity and each subject.



# Files and thier functionality

The below files are uploaded to the repository with thier specific tasks

tidy.R: R code performing the cleaning and transformation tasks for achieving the objectives listed in section Objectives
   
README.md: Mark Down Document containing details of the purpose and analysis 

Code.md: Mark Down Document containg the details of the code with explaination

# Analysis of tidy.R

1) The code reads the respective files from the local directory after the required libraries are loaded and the working directory is set

2) Once the files are loaded for respective filed names are added as the column names for the data read from the files and are stored into the respective datasets

3) The test and training datasets are binded with the respective y and subject data added to the columns and the duplicated columns are removed using the r in built functions

4) the test and training data set are merged to form a unique Analysis_Set which clubs both the data frames and also an additional column depicting the type of the data names Datatype is added

5) A new dataframe from the Analysis_Set is derived containing the mean and standard deviation using the functions from the dplyr package

6)The appropriate labels for the activities are read and added to the Analysis_set to assign the respective names for the activity ID`s

7) Finally the avaerage_set dataframe is derived from the Analysis_set having the mean of all observations grouped at the activity and subject level
 
