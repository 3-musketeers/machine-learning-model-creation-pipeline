# Machine Learning Model Creation Pipeline Overview
## Definitions: 
**Machine Learning**: is a type of artificial intelligence (AI) that provides computers with the ability to learn without being explicitly programmed.

**Model**: the thing that is trained on data, and used later for a specific purpose (not a good definition)

**Pipeline**: a set of processes that allows a person to achieve a certain goal

**"Machine Learning Model Creation Pipeline"**: everything a person should do, if they are given a problem and pertinent data and they need to return the best model that solves the problem (basically how to approach any [Kaggle](https://www.kaggle.com/) competition).

## Pipeline Modules: 
**Pipeline input**: a kaggle competition (or: a problem and a dataset)

1. Understanding the context 
   1. Understanding the problem 
   2. Understanding the data 
   3. Understanding the evaluation metric 
2. Build simple model
3. Build consistent cross validation
4. Look for similar approaches from past competitions
5. Get all domain-specific knowledge
6. Get to know the data
7. Create list of all possible useful models
8. For all possible useful models:
   1. preprocess data
   2. feature engineer
   3. feature selection
   4. optimize hyperparameters (on CV)
   5. find final CV/LB score of model
9. Ensembling

**Pipeline output**: the best machine learning model (that solves the problem)

## Resources:
Resources used to compile this pipeline...

1. Kyle's prior knowledge and experience (not a lot)
2. Abhishek Thakur's Tutorial to "Approach Almost Any Machine Learning Problem" (found [here](http://blog.kaggle.com/2016/07/21/approaching-almost-any-machine-learning-problem-abhishek-thakur/))
3. google search: machine learning pipeline, approaching any machine learning problem, automating machine learning model creation
4. kaggle top people interviews (specifically: how they approach a competition, found [here](http://blog.kaggle.com/tag/profiling-top-kagglers/))
   1. leustagos' interview (found [here](http://blog.kaggle.com/2016/02/22/profiling-top-kagglers-leustagos-current-7-highest-1/))
   2. luca massaron's interview (found [here](http://blog.kaggle.com/2016/07/14/kaggle-master-data-scientist-author-an-interview-with-luca-massaron/))
   3. Gilberto Titericz's interview (found [here](http://blog.kaggle.com/2015/11/09/profiling-top-kagglers-gilberto-titericz-new-1-in-the-world/))
   4. Kazanova's interview (found [here](http://blog.kaggle.com/2016/02/10/profiling-top-kagglers-kazanova-new-1-in-the-world/))
5. 2 useful articles 
   1. Learning from the best (found [here](http://blog.kaggle.com/2014/08/01/learning-from-the-best/))
   2. What do top Kaggle competitors focus on? (found [here](http://blog.kaggle.com/2012/07/18/what-do-top-kaggle-competitors-focus-on/))
