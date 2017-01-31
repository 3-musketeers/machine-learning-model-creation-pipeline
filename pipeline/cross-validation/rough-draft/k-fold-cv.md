What are the best methods for evaluating which model is better than the other model (and eventually allow you to choose a single best model)?
Focus on learning how to use cross validation
http://stats.stackexchange.com/questions/52274/how-to-choose-a-predictive-model-after-k-fold-cross-validation 
https://www.facebook.com/kaggle/posts/10153369056763464
https://www.analyticsvidhya.com/blog/2016/02/7-important-model-evaluation-error-metrics/
http://brettromero.com/wordpress/data-science-kaggle-walkthrough-creating-model/ 

http://stats.stackexchange.com/questions/71184/cross-validation-or-bootstrapping-to-evaluate-classification-performance 
https://www.google.com/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#q=what+to+do+after+k+fold+cross+validation 
https://www.google.com/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#safe=strict&q=bootstrap+validation+machine+learning

Kfold CV seems to be the best/most popular and this is how you do it:
Kfold cross validation is used to select the best model, as well as select the best hyperparameters for that model as well, then once you have the best hyperparameters/model you train it on all of the training set and make predictions using that final model that was trained on the entire training set

The question is, could you completely change the validation process and exchange it for one from your own creative creation?



```python
def get_cross_validation(train_x, train_y, train_model, make_preds, format_function):

def train_model(train_x, train_y)
    return model

```
