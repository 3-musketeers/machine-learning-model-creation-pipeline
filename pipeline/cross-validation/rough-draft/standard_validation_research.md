# Standard Validation
*goal: determine the best process for validation*

## Definitions
**Validation**: method to evaluate how well a model is generalizing to the data, and the overall accuracy of its predictions (better score indicates a better model)

Machine Learning: learn without being explicitly programmed (learn on its own, program it how to learn and it learns on its own)

A core objective of a learner is to generalize from its experience. Generalization in this context is the ability of a learning machine to perform accurately on new, unseen examples/tasks after having experienced a learning data set. The training examples come from some generally unknown probability distribution (considered representative of the space of occurrences) and the learner has to build a general model about this space that enables it to produce sufficiently accurate predictions in new cases.

For the best performance in the context of generalization, the complexity of the hypothesis should match the complexity of the function underlying the data. If the hypothesis is less complex than the function, then the model has underfit the data. If the complexity of the model is increased in response, then the training error decreases. But if the hypothesis is too complex, then the model is subject to overfitting and generalization will be poorer.

In order for the machine to learn, you need a way to tell it how well it is performing, if you can tell it how well it is doing, then all you need to do is program it to improve how well it is performing until it reaches what you deem perfect performance. So if you can give it a definitive score, it can increase its score to improve. 

You are effectively learning in order to improve your score (the score tells you how well you are doing)

That is why there is an evaluation metric to give a model a definitive score that tells you how well the model is doing. 

The goal of machine learning is to make perfect predictions on unseen data, and the model that can make the most perfect predictions on unseen data is the best. So if the model can generalize to all possible models (seen and unseen) then it will be the perfect model. 

* what if you could have more informative scores so it could know what direction it needs to improve in order to improve its overall score (so if model complexity score is too low, then it knows it needs to improve model complexity score to improve overall score)?
* why restrict its ability to learn more (complex models), by restricting the total amount of different things it can learn, you are restricting its ability to improve and reach the best capability?
* the evalution metric will tell you how good the model is doing, but it doesn't give other information. That is why you have validation because that score compared to your leaderboard score will tell you how well the model is generalizing (and this is additional information you cannot get from the evaluation metric alone, thus this validation score is a better scoring system and can help your model improve as it's generalization can be measured)
* similar to what validation does, define another scoring system or process that can give additional information about how well a model is doing, this way it knows how to improve
* could the model be programmed to try to predict future cases, or generate what could possibly be an unseen data point in the future and give it a label? because if it can predict future cases that means it can understand all cases (similar to if you know a math concept really well, and you are experienced with completing all the problems associated with the concept then you can predict what future questions will look like and be able to solve those questions as well, and if you are able to do this that means you understand the concept really well)
  * similar to how a radiologist has probably seen so many cases of lung cancer, there are really good at identifying lung cancer, thus they could even generate on their own a new picture of a patient that has or does not have lung cancer, and if they can generate acurate pictures and labels that means they really understand lung cancer or else they would not be able to generate the new examples
  * thus there could be an algorithm that is built that is not designed to just predict the labels of unseen data (outputs), but actually predict the possible cases of the future as well as the labels of those cases
  * or another way of grading how well an algorithm is performing is to see how accurate its generations of new examples are, as well as how accurate its labels for those examples are (how are you going to do this?)
  * http://www.nature.com/news/astronomers-explore-uses-for-ai-generated-images-1.21398

## Define what is the mainstream method of machine learning, in terms of validation?
* to define a model structure, train it on training data (this is the learning part), then to judge how well a model is performing in terms of prediction ability you give it a definite score based on how well it does on unseen data (amount predicted correctly vs incorrectly)
* the end goal is always to create a model that can generalize and make perfect predictions for any unseen data
* instead of using a test set score and trying to improve that score which may lead to overfitting, there is a validation process
  * the validation process allows you to improve the score off a validation set, and the validation score matching with the test score indicates the model is not overfit to the training data
  * when both validation score and test score are very good and very correlated that means you have a model that is not overfit as well as very good (thus it generalizes very well to new examples)
* does all of the above seem correct? confirm it is, then determine how validation fits in
* so what is the best way to perform this validation according to most sources?
* search up machine learning validation techniques, from the internet and from kaggle, and determine which technique is supported by the largest body of evidence
  * then take the technique, understand it deeply, and write a function that can implement it correctly


* note cross validation process should resemble the leaderboard or test set as best as possible (because if it does represent the test set, then you have an accurate understanding of how good your model is, otherwise you have no clue how good your model is)
  * "In regards to CV, I try to best resemble what I am being tested on." ([kazanova](http://blog.kaggle.com/2016/02/10/profiling-top-kagglers-kazanova-new-1-in-the-world/))

Types of Validation:

1. Holdout method: part of dataset is set aside to evaluate model performance ([here](https://en.wikipedia.org/wiki/Test_set#Validation_set))
2. Cross validation: data is partitioned multiple times, and the model is trained using part of data while evaluated on another part, and the average error over all partitions is computed ([here](https://en.wikipedia.org/wiki/Cross-validation_(statistics))
   1. Leave-one-out cross-validation
   2. k-fold cross validation
3. Boostrapping
4. [Sensitivity and specificity](https://en.wikipedia.org/wiki/Sensitivity_and_specificity) (True Positive Rate: TPR and True Negative Rate: TNR, respectively), [False Positive Rate](https://en.wikipedia.org/wiki/False_positive_rate) (FPR) as well as the [False Negative Rate](https://en.wikipedia.org/wiki/False_positives_and_false_negatives#false_negative_rate) (FNR)
5. [Receiver operating characteristic](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) (ROC) along with the accompanying Area Under the ROC Curve (AUC)

More about cross validation
* https://www.kaggle.com/c/titanic/forums/t/3244/cross-validation-methods
* for which k to choose, choose one that mimics the ratio of training vs testin in the validation process
* standard deviation of cv score matters more than mean
* stratified k-fold used for imbalanced dataset (classification problems)
* look for high correlation between local CV and LB score, so when one increases and decreases so does the other (always trust local CV more though)
support for k-fold cross validation:
http://www.slideshare.net/markpeng/general-tips-for-participating-kaggle-competitions
http://www.cs.utah.edu/~piyush/teaching/22-9-slides.pdf

If your local validation is set up well and is consistent with the leaderboard (which you need to test by making one or two submissions), there’s really no need to make many submissions. 

k-fold cross validation is the most common approach (stratified k-fold is necessary so that the validation set contains the sample percentage of each target class as the original complete dataset) 
  * AUC can give you more information
  * more folds the better (10 max), and the more times you run it on different samples of the dataset the better
  * the question is:
    * how to choose the best k that also doesn't take too much time
    * and whether or not you randomly partition the dataset every single time you run CV, or you use the same partitions every time you do CV (for consistency), or maybe you have one set partitions that you use every time and you also run a random version as well, can this be proven empirically?

## Data scientist significance
you are basically a scientist, you just define new types of methods and approaches to machine learning then all you have to do is just test the methods and see if it produces a better model, and if it does produce better models overall then that means you can justify your method is better (and you redefine how people make models!!). Thus it is all about the scientific method when you create a hypothesis, devise a way to test and support hypothesis, perform the test and show your results
  * [here](http://blog.kaggle.com/2016/07/14/kaggle-master-data-scientist-author-an-interview-with-luca-massaron/) luca talks about how you need a scientific mindset to be a data scientist, and it would be very interesting if you could merge the two competing cultures to a single one that does train black boxes, but the black boxes can incorporate prior knowledge, and eventually explain their understanding of the problem or the world
  * "accepting its strict empiricism based on data, and it means supporting work using only scientific tests (namely properly executed cross-validation) to prove the effectiveness of the chosen algorithmic solution."


## Resources
http://stats.stackexchange.com/questions/52274/how-to-choose-a-predictive-model-after-k-fold-cross-validation 
https://www.facebook.com/kaggle/posts/10153369056763464
https://www.analyticsvidhya.com/blog/2016/02/7-important-model-evaluation-error-metrics/
http://brettromero.com/wordpress/data-science-kaggle-walkthrough-creating-model/ 

http://stats.stackexchange.com/questions/71184/cross-validation-or-bootstrapping-to-evaluate-classification-performance 
https://www.google.com/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#q=what+to+do+after+k+fold+cross+validation 
https://www.google.com/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#safe=strict&q=bootstrap+validation+machine+learning
* good slides to learn about anything in machine learning ([here](http://www.cs.utah.edu/~piyush/teaching/cs5350.html))
http://www.slideshare.net/markpeng/general-tips-for-participating-kaggle-competitions
https://yanirseroussi.com/2014/08/24/how-to-almost-win-kaggle-competitions/
http://mlwave.com/reflecting-back-on-one-year-of-kaggle-contests/

## Improving Cross Validation over Time
http://blog.kaggle.com/2015/05/07/profiling-top-kagglers-kazanovacurrently-2-in-the-world/


## K-fold Cross Validation
### Process
Kfold CV seems to be the best/most popular and this is how you do it:
Kfold cross validation is used to select the best model, as well as select the best hyperparameters for that model as well, then once you have the best hyperparameters/model you train it on all of the training set and make predictions using that final model that was trained on the entire training set
### Code
https://www.kaggle.com/wiki/GettingStarted

```python
def get_cross_validation(train_x, train_y, train_model, make_preds, format_function):

def train_model(train_x, train_y)
    return model

```

from sklearn.model_selection import StratifiedKFold
def train_xgboost():
    df = pd.read_csv('../input/stage1_labels.csv')

    x = get_trn()
    y = df['cancer'].as_matrix()

    clfs = []
    for seed in range(15):

        skf = StratifiedKFold(n_splits=10, random_state=14+seed, shuffle=True)
    
        
        
        for train_index, test_index in skf.split(x, y):
            trn_x, val_x = x[train_index,:], x[test_index,:]
            trn_y, val_y = y[train_index], y[test_index]
    
            clf = xgb.XGBRegressor(max_depth=11,
                                   n_estimators=1500,
                                   min_child_weight=9,
                                   learning_rate=0.03,
                                   nthread=8,
                                   subsample=0.80,
                                   colsample_bytree=0.80,
                                   seed=88+seed)
    
            clf.fit(trn_x, trn_y, eval_set=[(val_x, val_y)], verbose=True, eval_metric='logloss', early_stopping_rounds=50)
            clfs.append(clf)

    return clfs
