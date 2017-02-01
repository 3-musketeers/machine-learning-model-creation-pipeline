# Standard Validation
*an attempt to summarize everything that was researched in a concise format*

**Questions/Topics to be addressed:**
 
1. Definition/Key Aspects of Validation
2. How does validation fit into the whole process of creating a machine learning model?
3. Types of Validation
   1. *General description*
   2. Pros/Cons
3. Best type of validation

## Definition/Key Aspects of Validation
**Validation**: method to evaluate how well a model is generalizing to the data, and the overall accuracy of its predictions (better score indicates a better model)
* Typically used to find the best hyperparameters for the model, for feature extraction/selection
* For kaggle competitions:
  * Validation should resemble what the model is being tested for (so you have an accurate understanding of how well the model will do in the end)
  * Validation score should be highly correlated with test set score (to indicate the model is generalizing well)


## Validation Relationship to Creating a Machine Learning Model
### Goal of Machine Learning
A core objective of a machine learning model is to generalize from its experience. Generalization in this context is the ability of a learning machine to make accurate predictions on new, unseen examples/tasks (test set) after having experienced a learning data set (training set).

Understanding exactly how well a model is generalizing and making predictions will allow the scientist to choose which models are better, and see when a change to the model causes improvement (without it, the machine would not be able to learn as it would not know if it is "learning" the better method or worse method). Since the results from validation compared to the test set results allow the scientist to understand how well a model is generalizing (without introducing overfitting), that is why validation is necessary.

## Types of Validation
### Holdout Method
*part of the dataset is set aside to evaluate model performance in addition to the test set (called the validation set)*

**Pros**: fast

**Cons**: waste of useful data that could be used to train the model

### Cross Validation
*data is partitioned multiple times, and the model is trained using part of data while evaluated on another part, and the average error over all partitions is computed*

**Pros**: all data is used to train model in the end, relatively as accurate as Holdout Method

**Cons**: takes much more time to perform

### Boostrapping
*randomly sample with replacement from the dataset to build a "boostrap sample"*
### Sensitivity, Specificity, False Positive Rate, False Negative Rate
*proportion of positives correctly identified, negatives correctly identified, positives incorrectly identified, negatives incorrectly identified*

**Pros**: gives more of an understand of where the model is making mistakes (on the positive or negative examples), doesn't take time to perform

**Cons**: N/A

### Receiver Operating Characteristic, Area Under the ROC Curve
*plot of the true positive rate (TPR) against the false positive rate (FPR) at various threshold settings, higher AUC is better*

**Pros**: N/A

**Cons**: N/A

## Best Validation (According to Kaggle Community)
1. **Cross Validation** (k-fold-validation)
2. AUC
