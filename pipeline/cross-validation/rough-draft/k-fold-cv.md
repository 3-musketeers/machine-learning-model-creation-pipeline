# K-Fold Cross Validation
*outline exactly why k-fold is the best validation, how to implement it, and a sample functions that implements it (stratified vs not stratified)*

*keep in mind: in terms of kaggle competitions, the goal is to develop a process (scoring system) that is consistent with the scoring of the public and private leaderboards, in order to give the scientist an accurate understanding of how well their model is generalizing to new examples*

*so if the process is not consistent with the public leaderboard after a couple submissions, that means the process needs to be revised*

## Why K-Fold
It allows all of the training data to be used to train the model (unlike the holdout method), while still providing an accurate measure of how well a model is generalizing. The only sacrifice is the extra time needed to run so many folds of K-Fold.

## K-Fold Method Implementation
*Input: entire training set with labels, how to train the model*

1. 

*Output: k scores based on each partitioning of the dataset*

### Details
* More folds is always better, however the number of folds should never exceed 10 (as 90% of the data is being used to train the model, which is already extremely close to 100%)
* More runs of K-fold validation will give a more accurate understanding of how well the model is generalizing (as the data is being partitioned in different intervals)
* How to choose the value of K, based on time limitations and accuracy of measurement:
  * choose K that doesn't take ridiculous amounts of time, yet is as high as possible
* Should you always partition the k-folds the same way when evaluating models? Or should you partition the K-folds randomly every time you evaluate a different model?
  * maybe you should partition it the same way a single time, then partition it randomly another time, and compare scores for the model from the two run throughs of k-fold


## Sample K-Fold Code
## Sample Stratified K-Fold Code
