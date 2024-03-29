## Mar 17  2019 CSCI 4930/5930 Machine Learning 
# Programming Assignment 2: Age prediction from facial images

In this assignment you are going to develop a program (in python) that would be able to guess age of a
person given his/her photo.
Roughly speaking, it is expected that you will first do the principal component analysis (PCA) to
perform dimensionality reduction of the given dataset. Then, train a linear regression model on the
reduced-dimension dataset to learn their age.

## Backgrounds on PCA
<img src="https://i.postimg.cc/gkZWYCq1/flatten.png" width="40%"></img>

Problems arise when performing learning in a higher-dimensional space due to the phenomenon known
as “Curse of the dimensionality” [curse of dimensionality](https://en.wikipedia.org/wiki/Curse_of_dimensionality). 
Significant improvements can be achieved by first mapping the data into a lower-dimensional space. And you
already have heard about principal component analysis, which is a fantastic method to do the same. In
image learning paradigm, principal components obtained from the given images are affectionately
called the “eigenfaces”.


<img src="https://i.postimg.cc/htRqh22v/step1-7.png" width="90%"></img>
<img src="https://i.postimg.cc/T3jvbns9/step8.png" width="90%"></img>

### Step 1
Download wiki_labeled.zip (MD5sum: 8af376e8a0f9898d8d3dd5653351070e),
and extract the contents. The wiki_labeled/ directory will contains 60327 facial images kept in
100 folders, naming 00-99. Dimension of each image is 100 pixels by 100 pixels. Also,
download the wiki_labeled.mat (md5sum: d5b65bb4c4d414a230b60b8025ece276) file,
containing meta information of each of the 60327 images:

#### • ID: identification number of the subject (starting from 2002)
#### • dob: the date of birth of the subject. (It is Matlab’s datenum value calculated based on total number of days since January 0, 0000.)
#### • dob_str: the DD-MMM-YYYY format dob value.
#### • photo_taken: when the photo was taken (only the year value)
#### • full_path: directory path, including filename of the image
#### • gender: Gender of the subject (0: female, 1: male, NaN if unknown)
#### • name: name of the subject
#### • face_location: location of the face.
#### • face_score: detector score (the higher the better). Inf implies that no face was found in the image, and the face_location then just returns the entire image.
#### • second_face_score: detector score of the face with the second highest score. This is useful to ignore images with more than one face. second_face_score is NaN (not a number) if no second face was detected.
#### • age: age of the person (in years), and was calculated based on the “dob” value and the “photo_taken” values.

### Step 2
Randomly split the dataset into 80% training and 20% test sets.

### Step 3
Compute the principal components (i.e., eigenfaces) from the training dataset by following the
steps to compute principal components described in the “Backgrounds” section. Please note
that: you can not call a library function to directly compute the principal components. For
example: the PCA library in sklearn. However, you can use library functions to calculate the
eigenvalues and eigenvectors of a square matrix.

### Step 4
Draw a scree-plot to choose a best value for K that denotes how many principal components to
retain.

### Step 5
Show the top 20 ghosts (i.e., eigenfaces) in a 10x10 grid.

### Step 6
Considering the chosen K value above, project the training and test images on to the eigenfaces
to reduce the dimensionality.

### Step 7
Perform Stochastic gradient descent (SGD) based linear regression on the training dataset to
learn “age”. Please do a trial-and-error search to tune the hyper-parameters of the SGD based
linear regression (e.g., number of epochs, learning rate), and make a note why you select a
specific set of hyper-parameters.

### Step 8
Predict the test dataset (from step 2) based on the learned model in step 7, and report Root
Mean Square Error (RMSE).

### Step 9
From Canvas download the wiki_judge_images.zip (md5sum:
551a46ee18286824ad03d9110750da01) containing 2001 facial images (1.png, 2.png, …,
2001.png) of resolution 100x100. You can obtain another meta file, wiki_judgeX.mat
(md5sum: b7382fd03b8fc05575bb5701c0eec25b) from Canvas containing some information
about the images. However, the information does not include “age” field. Using your best
regression model, predict age of each of the 2001 facial image, and prepare a submission.csv
file

