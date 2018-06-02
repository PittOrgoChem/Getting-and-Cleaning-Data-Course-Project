# The following variables were created from the files downloaded and stored in a folder in the working directory. The files were read as dataframes named as follows:

+ featuresDF: dataframe created from the downloaded file "features.txt"
+ activity_labelsDF: dataframe created from the downloaded file "activity_labels.txt"
+ subject_testDF: dataframe created from the downloaded file "subject_test.txt"
+ X_testDF: dataframe created from the downloaded file "X_test.txt"
+ y_testDF: dataframe created from the downloaded file "y_test.txt"
+ subject_trainDF: dataframe created from the downloaded file "subject_train.txt"
+ X_trainDF: dataframe created from the downloaded file "X_train.txt"
+ y_trainDF: dataframe created from the downloaded file "y_train.txt"

#Data frames containing information about the experimental subjects and activities are combined
#with the recently modified X_testDF and X_trainDF to create two new data frames testDF and trainDF

testDF <- cbind(c(subject_testDF, y_testDF), X_testDF)
trainDF <- cbind(c(subject_trainDF, y_trainDF), X_trainDF)

#The names of newly added variables containing information about subject and activity are changed

names(testDF)[c(1,2)] <- c("subject", "activity")
names(trainDF)[c(1,2)] <- c("subject", "activity")

#In order to recognize the activity, the information on the "activity_labels" data frame was used
#to add the labels to our data frames

testDF <- merge(testDF, activity_labelsDF, by.x = "activity", by.y = "V1")
trainDF <- merge(trainDF, activity_labelsDF, by.x = "activity", by.y = "V1")

#In order to recognize the new column, the name is changed

names(testDF)[564] <- "activity_label"
names(trainDF)[564] <- "activity_label"

#The variable's order is then reoorganized in both major data frames

testDF <- testDF[, c(1, 564, 2:563)]
trainDF <- trainDF[, c(1, 564, 2:563)]

#Before combining both testDF and trainDF, it is appropriate to introduce a column containing the
#type of experiment conducted that lead to the observations "TEST" or "TRAIN" and the variable's
#order reoorganized once again

testDF <- mutate(testDF, "experiment_type" = "TEST")
testDF <- testDF[, c(1, 2, 3, 565, 4:564)]
trainDF <- mutate(trainDF, "experiment_type" = "TRAIN")
trainDF <- trainDF[, c(1, 2, 3, 565, 4:564)]

#Once the two data frames (testDF and trainDF) have been appropriately cleaned using the information 
#provided, the two sets can be combined as follows

combined_DF <- rbind(testDF, trainDF)

#to extract the only the measurements on the mean and standard deviation for each measurement

mean_std_DF <- select(combined_DF, 1:4, contains("mean()"), contains("std()"))

#In order to create a derived data frame the shows the average for each variable for each separate
#activity and experimental subject, it is necessary to group the data by activity_labels, subject, and
#experiment_type

tempDF <- group_by(mean_std_DF, activity_label, subject, experiment_type)

#Once the data is appropriately grouped by variables of interest, a final data frame showing the
#average for each measurement variables per subject and activity performed can be generated

finalDF <- summarise_if(tempDF, is.numeric, mean)
