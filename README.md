# Wifi-Positioning

## Summary
Many real-world applications need to know the location of a user to provide their services. Outdoor localization problem can be accurately solved thanks to GPS technology. However, GPS cannot be applied for indoor localization, and so it is still an open problem. For this reason, we evaluated the application of machine learning techniques to predict user location, replacing GPS signals with wifi signals.

**Data structure**: 
The data provided contains locational information and the corresponding wifi-fingerprints gathered in a multi-building and multi-floor setup on an university campus. The location to be predicted is given by three variables, i.e. LONGITUDE and LATITUDE coordinates and the floor number defining the exact position of each location (reference points). Wifi-fingerprints, on the other hand, consist of 520 columns each representing a single 'Wifi access point' (WAP) and the signal intensity (RSSI) measured for a given observation.

The data is split into three datasets varying in the way of data collection and data provided. Each dataset contains the following:

   * 'Train': Is used in model training phase. Contains almost 20k observations measured on predefined positions throughout the campus. In addition to the exact location and WAP signals measured columns are provided identifying the building, user, and phone ('BUILDINGID', 'USERID', 'PHONEID') are provided.
   * 'Validation': Is considered to validate the models trained with unseen observations. Covers over 1k observations but provides no additional columns. Observations in this dataset have been taken randomly throughout the campus to simulate real-world data. Furthermore, it has to be mentioned that the validation set contains several observations taken in areas not covered by the trainset.
   * 'Test': This dataset is not available through training and validation phase since it is considered to test the best models identified before. Likewise, the testset includes only real-world data to evaluate its positioning accuracy in a real-world setup.

**Technical Approach Summary**:
1. Exploratory Data Analysis and Preprocessing:
  * Change scale of WAP to a more human readable scale
  * Rotate Longitude and Latitude angle
  * Visualize distribution of reference points
  * Phone individual distribution
2. Feature Engineering
  * Add and remove columns
  * Delete duplicates
  * Deal with problematic phones
  * Deal with problematic signals
3. Predictions
  * Cascading predictions with confidence interval (bootstrap)

_NOTE: if a jupyter notebook script doesn't work, copy the url, go into https://nbviewer.jupyter.org/ and paste it on the site._
