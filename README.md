# pred_accident_frm_speed_turns_data
The prepared files include:
-	trip data train.zip: a zipped folder containing the relevant csv trip data, where each trip has a series of records containing:
  -	time seconds: the time in seconds since the start of the trip (float)
  -	speed meters per second:  the speed in m/s of the vehicle (float ∈ [0, ∞), invalid values will be indicated with NaN)
  -	heading degrees: the angle in deg of the vehicle’s travel relative to north (clockwise positive, float ∈ [0, 360), invalid values will be indicated with NaN)
 
-	model data train.csv: a csv file containing:
  -	a column filename to join to the file names in trip data train.zip
  -	the data matrix X as columns feature1, ..., featureN
  -	the vector y as column y
-	trip data test.zip and model data test.csv: similar trip data but without the label column y

The additional features to augment the data matrix should be the following:
-	the count of stops in the trip [int]
-	the count of turns (greater than 60 degrees) [int]
For turns and stops, consider events within 3 seconds of one another to be the same event, and exclude events lasting shorter than 3 seconds. A left turn followed immediately by a right turn (or vise versa) should be treated as two separate turns. To help with building the feature extraction, the trip data corresponding to filename = "0001.csv" should have approximately:
  -	1 stop
  -	9 turns

The (discrete binary) target variable yi ∈ {0, 1} represents whether the ith trip is “interesting” or not, and the objective of the work sample is to fit a model (using the training data) that can make an accurate prediction yˆ = f (Xa) of y. The model will then be used to generate predictions on the provided test data.
