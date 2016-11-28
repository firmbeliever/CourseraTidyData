# CourseraTidyData
This repo contains an R script that will download raw data from https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip
This zip contains raw data collected from mobile phone accelerometers, collected during 6 activities for 30 participants.

The script:
- downloads and unzips the data files
- reads the raw data from the 6 relevant data files
- combines the training and test data
- selects only the columns that list a mean or standard deviation
- labels the activity data with readable names (to use instead of the mapped integer values)
- combines the subject, measurement, and activity data in a final data frame
- groups and summarizes the data, calculating the mean of each measurement for each subject and activity

(Further comments in the script describe each step in detail.)

This script requires the following packages to be installed and loaded:
- base
- utils
- dplyr
- plyr

The script runs against the current working directory, and the zip file will be downloaded to and unzipped in that location.  If the user desires to use a different directory, the working directory should be adjusted before running the script.

The final step of the script creates a data frame with the mean of each variable for each subject and activity.  The name of this data frame is tidyMeans.  Note that the script does not display the data frame or write the results to disk.  If the user wishes to see the results, the data frame can be viewed using the View command.  Alternatively, the data can be saved to disk with the following command:
write.table(tidyMeans, "tidyMeans.txt", row.names = FALSE)
Once saved, this file can be read again using the following command:
read.table("tidyMeans.txt", header = TRUE)
(Both of these commands will use the current working directory.  Alter the path if desired.)

The tidyMeans data frame contains tidy data.  Each summarized observation of subject and activity is on one row. Each column summarizes exactly one feature, and each feature is in exactly one column.

Please see the codebook for more information on the data itself.
