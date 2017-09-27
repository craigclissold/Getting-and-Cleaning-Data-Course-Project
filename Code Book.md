# Code book for Coursera Getting and Cleaning Data course project

The data set that this code book pertains to is located in the tidy_data.txt file of this repository.
See the README.md file of this repository for background information on this data set.
The structure of the data set is described in the Data section, its variables are listed in the Variables section, and the transformations that were carried out to obtain the data set based on the source data are presented in the Transformations section.

The files that will be used to load data are listed as follows:
	test/subject_test.txt
	test/X_test.txt
	test/y_test.txt
	train/subject_train.txt
	train/X_train.txt
	train/y_train.txt

From the related files, we can see:
	Values of Varible Activity consist of data from “Y_train.txt” and “Y_test.txt”
	values of Varible Subject consist of data from “subject_train.txt” and subject_test.txt"
	Values of Varibles Features consist of data from “X_train.txt” and “X_test.txt”
	Names of Varibles Features come from “features.txt”
	levels of Varible Activity come from “activity_labels.txt”
	So we will use Activity, Subject and Features as part of descriptive variable names for data in data frame.

The zip file containing the source data is located at https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip.
The following transformations were applied to the source data:
	1. The training and test sets were merged to create one data set.
	2. The measurements on the mean and standard deviation (i.e. signals containing the strings mean and std) were extracted for each measurement, and the others were discarded.
	3. The activity identifiers (originally coded as integers between 1 and 6) were replaced with descriptive activity names (see Identifiers section).
	4. The variable names were replaced with descriptive variable names (e.g. tBodyAcc-mean()-X was expanded to timeDomainBodyAccelerometerMeanX), using the following set of rules: 
		* Special characters (i.e. (, ), and -) were removed
		* The initial f and t were expanded to frequencyDomain and timeDomain respectively.
		* Acc, Gyro, Mag, Freq, mean, and std were replaced with Accelerometer, Gyroscope, Magnitude, Frequency, Mean, and StandardDeviation respectively.
		* Replaced (supposedly incorrect as per source's features_info.txt file) BodyBody with Body.
	5. From the data set in step 4, the final data set was created with the average of each variable for each activity and each subject.

The collection of the source data and the transformations listed above were implemented by the run_analysis.R