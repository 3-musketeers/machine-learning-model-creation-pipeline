# Standard Validation
*goal: determine the best process for validation*

## Definitions
**Validation**: method to evaluate how well a model is generalizing to the data, and the overall accuracy of its predictions 


http://stats.stackexchange.com/questions/52274/how-to-choose-a-predictive-model-after-k-fold-cross-validation 
https://www.facebook.com/kaggle/posts/10153369056763464
https://www.analyticsvidhya.com/blog/2016/02/7-important-model-evaluation-error-metrics/
http://brettromero.com/wordpress/data-science-kaggle-walkthrough-creating-model/ 

http://stats.stackexchange.com/questions/71184/cross-validation-or-bootstrapping-to-evaluate-classification-performance 
https://www.google.com/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#q=what+to+do+after+k+fold+cross+validation 
https://www.google.com/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#safe=strict&q=bootstrap+validation+machine+learning


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
