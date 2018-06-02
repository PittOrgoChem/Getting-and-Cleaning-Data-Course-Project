*The following variables were created from the files downloaded and stored in a folder in the working directory. The files were read as dataframes named as follows:*

+ featuresDF: dataframe created from the downloaded file "features.txt". Dimensions: 561 rows, 2 columns

+ activity_labelsDF: dataframe created from the downloaded file "activity_labels.txt". Dimensions: 6 rows, 2 columns

+ subject_testDF: dataframe created from the downloaded file "subject_test.txt". Dimensions: 2947 rows, 1 column

+ X_testDF: dataframe created from the downloaded file "X_test.txt". Dimensions: 2947 rows, 561 columns

+ y_testDF: dataframe created from the downloaded file "y_test.txt". Dimensions: 2947 rows, 1 column

+ subject_trainDF: dataframe created from the downloaded file "subject_train.txt". Dimensions: 7352 rows, 1 column

+ X_trainDF: dataframe created from the downloaded file "X_train.txt". Dimensions: 7352 rows, 561 columns

+ y_trainDF: dataframe created from the downloaded file "y_train.txt". Dimensions: 7352 rows, 1 column

+ testDF: dataframe created by combining by column *subject_testDF, y_testDF, X_testDF*. Dimensions: 2947 rows, 565 columns

+ trainDF: dataframe created by combining by column *subject_trainDF, y_trainDF, X_trainDF*. Dimensions: 7352 rows, 565 columns

+ combined_DF: dataframe created by binding by rows tidied versions of *testDF* and *trainDF*. Dimensions: 10,299 rows, 565 columns

+ mean_std_DF: dataframe resulting from subsetting *combined_DF* by only selecting the data from variables(columns) in which the mean and standard deviation were reported. Dimensions: 10,299 rows, 70 columns

+ finalDF: dataframe showing the average for each measurement variable per subject and activity in the experiment. Dimensions: 180 rows, 70 columns
