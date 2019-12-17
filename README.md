## Mar 17  2019 CSCI 4930/5930 Machine Learning 
# Programming Assignment 2: Age prediction from facial images

In this assignment you are going to develop a program (in python) that would be able to guess age of a
person given his/her photo.
Roughly speaking, it is expected that you will first do the principal component analysis (PCA) to
perform dimensionality reduction of the given dataset. Then, train a linear regression model on the
reduced-dimension dataset to learn their age.

## Backgrounds on PCA
<img src="https://i.postimg.cc/gkZWYCq1/flatten.png" width="40%" style="margin-left: 10px;"></img>
Problems arise when performing learning in a higher-dimensional space due to the phenomenon known
as “Curse of the dimensionality” [curse of dimensionality](https://en.wikipedia.org/wiki/Curse_of_dimensionality). 
Significant improvements can be achieved by first mapping the data into a lower-dimensional space. And you
already have heard about principal component analysis, which is a fantastic method to do the same. In
image learning paradigm, principal components obtained from the given images are affectionately
called the “eigenfaces”.


<img src="https://i.postimg.cc/htRqh22v/step1-7.png" width="90%"></img>
<img src="https://i.postimg.cc/T3jvbns9/step8.png" width="90%"></img>








## Dataset
### baby-weights-dataset2.csv
It has 101400 rows (samples) with 37 columns (variables). Each sample represent a case
for a new-born. It contains 37 variables (just mentioned! Haha) about it. Very last
column of it is “BWEIGHT”, that true weight of the new-born (in lbs unit). Actually,
this needs to be considered as the target variable here.

### data-description.txt
You will see that the name of the 37 variables are actually contracted form of some sort.
And, the source of the dataset did not offer me description of every single of them. But,
after studying about them, I could elaborate only few of them. Please pardon my
laziness. Okay, this file contains few descriptions for the variables. All the rest are
mostly talking about the Mother’s medical history and all. No big deal, I guess, for you
to work with these variables without knowing their meaning. 

### judge-without-label.csv 
This is an interesting file. It contains new samples: additional 2001 rows with 36
columns (without the BWEIGHT target column). Once again, this should be part of the
training, as there are no ground truth target labels, right? Once the training is complete
with the dataset provided above, you must apply your prediction algorithm to predict
BWEIGHT of these 2001 samples, and submit the result as part of your assignment
submission.

## Results
### judge-submission-run-1.csv
### judge-submission-run-2.csv
### judge-submission-run-3.csv
Predicted BWEIGHT/result for each of the samples from the judge-without-label.csv file are saved 
in the files above.  

## Tasks
Please read the LinearRegression.ipynb file using Jupyter Notebook to learn about 15
mandatory tasks, and 2 additional tasks for graduate students (CSCI-5930).
