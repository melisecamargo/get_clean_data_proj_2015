Data transformation
-------------------
The raw data sets are processed with run_analisys.R script to create a tidy data set.

**Merge training and test sets**

Test and tranining data (X_train.tx, X_test.txt), subject ids(subject_train.tx, subject_test.txt) and activity ids (y_train.txt, y_test.txt) are merged to obtain a single data set. Variables are labelled with the names assigned by the original collectors (features.txt)

**Extract mean and standard deviation variables**

From the merged data set is extracted an intermidiate data set with only the values of estimated mean (variables in which labels contain "mean") and standard deviation (variables in which labels contain "std").

**Use descriptive activity names**

A new column is added to the intermediate data set with the activity description. ActivityId column is used to look up descriptions in activity_labels.txt

**Label variables appropariately**
In order to obtain valid R names, without parentheses, dashes or commas, and also to have more descritpive labels, the labels given by the original colectors were changed.

**Create a tidy data set**

A final tidy data set is created from the itermediate data set. Numeric variables are averaged for each activity and each subject. The tidy data contains 10299 observations with 81 variables divided as below:
- Activity label (*Activity*): WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING
- Identifier of the subject who carried out the experiment (*Subject*): 1, 3, 5, 6, 7, 8, 11, 14, 15, 16, 17, 19, 21, 22, 23, 25, 26, 27, 28, 29, 30.
- 79-feature vector with time and frequency domain signal variables (numeric)

The following table relates the 17 signals to the names used as prefix for the variables names present in the data set. ".XYZ" represents three variables, one for each axis. 

| Name                               | Time domain                                | Frequency domain                        |
| -----------------------------------|--------------------------------------------| ----------------------------------------|
| Body Acceleration                  | TimeDomain.BodyAcceleration.XYZ            | FrequencyDomain.BodyAcceleration.XYZ    |
| Gravity Acceleration               | TimeDomain.GravityAcceleration.XYZ         |                                         |
| Body Acceleration Jerk             | TimeDomain.BodyAccelerationJerk.XYZ        | FrequencyDomain.BodyAccelerationJerk.XYZ|
| Body Angular Speed                 | TimeDomain.BodyAngularSpeed.XYZ            | FrequencyDomain.BodyAngularSpeed.XYZ    |
| Body Angular Acceleration          | TimeDomain.BodyAngularAcceleration.XYZ     |
| Body Acceleration Magnitude        | TimeDomain.BodyAccelerationMagnitude       | FrequencyDomain.BodyAccelerationMagnitude|
| Gravity Acceleration Magnitude     | TimeDomain.GravityAccelerationMagnitude    |
| Body Acceleration Jerk Magnitude   | TimeDomain.BodyAccelerationJerkMagnitude   | FrequencyDomain.BodyAccelerationJerkMagnitude|
| Body Angular Speed Magnitude       | TimeDomain.BodyAngularSpeedMagnitude       | FrequencyDomain.BodyAngularSpeedMagnitude
| Body Angular Acceleration Magnitude| TimeDomain.BodyAngularAccelerationMagnitude| FrequencyDomain.BodyAngularAccelerationMagnitude|

For variables derived from mean and standard deviation estimation, the previous labels are augmented with the terms "Mean" or "StandardDeviation"

The data set is written to the file sensor_avg_by_act_sub.txt


