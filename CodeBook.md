*The following variables were created from the files downloaded and stored in a folder in the working directory. The files were read as dataframes named as follows:*

+ featuresDF: dataframe created from the downloaded file "features.txt"

+ activity_labelsDF: dataframe created from the downloaded file "activity_labels.txt"

+ subject_testDF: dataframe created from the downloaded file "subject_test.txt"

+ X_testDF: dataframe created from the downloaded file "X_test.txt"

+ y_testDF: dataframe created from the downloaded file "y_test.txt"

+ subject_trainDF: dataframe created from the downloaded file "subject_train.txt"

+ X_trainDF: dataframe created from the downloaded file "X_train.txt"

+ y_trainDF: dataframe created from the downloaded file "y_train.txt"

+ testDF: dataframe created by combining by column *subject_testDF, y_testDF, X_testDF*

+ trainDF: dataframe created by combining by column *subject_trainDF, y_trainDF, X_trainDF*

*Once the two data frames (testDF and trainDF) were appropriately cleaned using the information provided, the two sets were combined into:*

+ combined_DF: dataframe created by binding by rows *testDF* and *trainDF*. This resulting dataframe has dimensions of 10,299 rows and 565 columns

+ mean_std_DF: dataframe resulting from subsetting *combined_DF* by only selecting the data from variables(columns) in which the mean and standard deviation were reported. Dimensions: 10,299 rows, 70 columns

#In order to create a derived data frame the shows the average for each variable for each separate
#activity and experimental subject, it is necessary to group the data by activity_labels, subject, and
#experiment_type

tempDF <- group_by(mean_std_DF, activity_label, subject, experiment_type)

#Once the data is appropriately grouped by variables of interest, a final data frame showing the
#average for each measurement variables per subject and activity performed can be generated

finalDF <- summarise_if(tempDF, is.numeric, mean)
