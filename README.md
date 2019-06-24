# Human Activity Recognition using Smartphones
submission for Getting and Cleaning Data Course Final Project

From the information provided in (http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones), the experimental data was studied and arranged in a way that will make our analysis smoother. First, the downloaded file was unzipped and several files containing relevant information about the experiment were opened as dataframes. After getting a better picture about those files dimensions and the description offered by the authors of the experiment, two distinct data sets (*testDF* and *trainDF*) were assembled by combining the information offered in different files about experimental subjects (*subject_testDF* and *subject_trainDF*) and the activity performed during the data collection (*y_testDF* and *y-trainDF*). Additional important information was added using the file containing the legend for the activities (1-6) named *activity_labelsDF*. Lastly and for future reference, a new variable was added to each dataframe(*testDF* and *trainDF*) that explicitly described the type of experiment perfomed ("TEST" or "TRAIN").

Once the described manipulations were performed along some reoorganization of the columns/variables, a match analysis was performed using the subject columns from both *testDF* and *trainDF* to make sure there were not repeated subjects present in both experiments. Since no matching was found among the subects in both data sets, both *testDF* and *trainDF* were combined by rows to create a much larger dataframe, *combined_DF*. This new sets allowed us to streamline the analysis by first subsetting the data resulting from the calculation of the mean and the standard deviation (*mean_std_DF*), and then group our data by subejects and activities performed during data collection (*tempDF*).

A final manipulation of the data, resulted in the creation of a dataframe that shows the average of every measurement present in *combined_DF* per subject and activity performed. This last data set was conveniently named *finalDF*.
