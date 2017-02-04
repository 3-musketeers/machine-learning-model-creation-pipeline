# K-Fold Cross Validation
*outline exactly why k-fold is the best validation, how to implement it, and a sample functions that implements it (stratified vs not stratified)*

*keep in mind: in terms of kaggle competitions, the goal is to develop a process (scoring system) that is consistent with the scoring of the public and private leaderboards, in order to give the scientist an accurate understanding of how well their model is generalizing to new examples*

*so if the process is not consistent with the public leaderboard after a couple submissions, that means the process needs to be revised*

## Why K-Fold
It allows all of the training data to be used to train the model (unlike the holdout method), while still providing an accurate measure of how well a model is generalizing. The only sacrifice is the extra time needed to run so many folds of K-Fold.

## K-Fold Method Implementation
*Input: entire training set with labels, how to train the model*

1. Designate the number of folds to be performed (k number of folds)
2. Divide the dataset into k different sets of training examples (k1, k2, ..., kn)
3. For the number of folds (k):
   1. Train the model on k-1 of the sets of training examples (train on a different k-1 sets every time)
   2. Use model to make predictions on the leftover set of training examples
   3. Compare predictions to actual labels, and calculate score

*Output: k scores based on each partitioning of the dataset*

### Details
* In the end to train the final model, train it on all of the training data (ignore the k models that were trained previously as they are only used for evaluation purposes)
* To select hyperparameters and the best models, designate a model and its hyperparameters, run k-fold, then designate different hyperparameters or a different model, run k-fold, and compare scores to find which model/set of hyperparameters is best (based on score)
* More folds is always better, however the number of folds should never exceed 10 (as 90% of the data is being used to train the model, which is already extremely close to 100%)
* More runs of K-fold validation will give a more accurate understanding of how well the model is generalizing (as the data is being partitioned in different intervals)
* Stratified cross validation is used for imbalanced datasets (typically classification problems where there are a differing number of training examples for one class vs the others)
* Standard deviation of the k, k-fold scores can be more important than their mean (for understanding generalization purposes)
* How to choose the value of K, based on time limitations and accuracy of measurement:
  * choose K that doesn't take ridiculous amounts of time, yet is as high as possible
  * choose K that mimics the ratio of training data vs test data, which is the public leaderboard data (to get an accurate understanding of how well the model will do on the final test set)
* Should you always partition the k-folds the same way when evaluating models? Or should you partition the K-folds randomly every time you evaluate a different model?
  * maybe you should partition it the same way a single time, then partition it randomly another time, and compare scores for the model from the two run throughs of k-fold


## Sample K-Fold Code
*a sample function that can calculate k-fold scores for a given model*

## Sample Stratified K-Fold Code
*a sample function that can calculate stratified k-fold scores for a given model*

