# Workshop

In this workshop you will compare the performance of the two main supervised machine learning models: a Boosted tree model and a feedforward neural network on a semi complex dataset.

Your mission is to write a report, a blog post, in the form of a Colab notebook where you compare the behavior of these 2 types of models on a given dataset.

Topics you should write about

- Your strategy for tuning
- How easy is it to tune these models
- Is one type of model performing better than the other
- Is overfitting a problem

Think of it as your first blog post on Medium or linkedin in order to promote yourself as a data scientist and demonstrate your skills. Your thoughts, impressions and reflexions are the focus of this exercise.

What's important is less the coding technique than your interpretation of the results as well as your experience in doing the workshop.

At the end of the 4 hours you will share your Colab notebook on this spreadsheet.

## Tips on using LLMs

You are free and welcome to use LLMs to write some part of the code.

However, my advice is that you do not let the LLM do all the work.

Having the LLM write pieces of code is fine and will help you be more productive. Asking the LLM to do all the work will be a waste of time. If you don't understand the code you cannot understand the behavior of the model and analyze its performance.

- OK prompt:

`split the dataframe into a test and train set`

- Not OK prompt

`Train a feed forward keras network on the data, use grid search, with 5 fold and metric ...`

In short use the LLM to learn not to do the job in your place.

Note: the Gemini LLM in colab is not very good. you are warned. hahaha!

## The dataset

The dataset is the  [([Student Performance dataset]](https://archive.ics.uci.edu/dataset/320/student+performance))

649 rows, 30 features of student grades, demographic, social and school related features. it was collected by using school reports and questionnaires.

The dataset can be loaded directly from the UCI repository.

The data contains 3 target variables which are the grades for levels 1 , 2 and 3: G1, G2, G3. Your target is G3 which are the grades obtained at the end of high school. It ranges from 0 to 20. You will transform that variable into a binary one : pass (1) or fail (0)

The data loading and target transformation code is below.

You can read more about that dataset in this paper: [Using data mining to predict secondary school student performance](https://www.semanticscholar.org/paper/Using-data-mining-to-predict-secondary-school-Cortez-Silva/61d468d5254730bbecf822c6b60d7d6595d9889c).

## The models

You will train and compare the results of a baseline model and 2 more complex models.

The order in which you should train the models once you have standardized and encoded your data

1. establish the baseline
2. train the gradient boosted trees
3. train the feed forward neural network


### Baseline: logistic regression model

The logistic regression model is your baseline

The role of the baseline is to demonstrate that using more complex models actually brings significantly better performance. It's worth the effort and the resources.


### Gradient Boosted tree model

Depending on your experience level with machine learning, you either train
- beginner: sklearn's GradientBoostingClassifier
- advanced: XGboost or LightGBM

### Feed forward neural network with Keras

This [page](https://keras.io/examples/structured_data/structured_data_classification_from_scratch/) is a good example of classification with structured tabular data. Focus on the Classifier class definition.

Note: Keras offers normalizers and feature processing methods. To keep things simple and your work within the short 4h timeframe of the workshop, I suggest you only ues scikit learn [preprocessing](https://scikit-learn.org/stable/api/sklearn.preprocessing.html) methods.


## Steps


The notebook should include

- categorical data encoding with either one hot encoding or ordinal encoding.
- parameter optimization with K fold cross validation using GridSearchCV or Hyperopt
- implement early stopping for both the boosted tree model and the feed forward neural net
- check out feature importance for the boosted tree model

Don't forget to

- set the random seed for reproducibility
- check out for overfitting
- compare different encoding techniques : one hot necoding or ordinal encoding
- compare different different scaler: [MinMax](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.MinMaxScaler.html#sklearn.preprocessing.MinMaxScaler) or StandardScaler


When reporting on the model comparison, do not focus only on the performance of the models.
Write about your experience, train of thoughts and the strategies you implemented to tune and train the models.

To interpret the performance of your model take into account

- the confusion matrix,
- classification metrics: accuracy, AUX, F1 score, Recall etc
- histograms of predicted probabilitiies (use the function predict_proba() if available)


# Beginner vs Advanced

If you are a beginner with Machine Learning use

- [GradientBoostingClassifier](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.GradientBoostingClassifier.html)
- [GridSearchCV](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html) for cross validation and parameter optimisation

If you already have some experience with machine learning

- use [XGboost](https://xgboost.readthedocs.io/en/stable/python/index.html) or [LightGBM](https://lightgbm.readthedocs.io/en/latest/index.html). Note that XGBoost provides an easy to use [scikit-learn interface](https://xgboost.readthedocs.io/en/stable/python/python_intro.html#scikit-learn-interface) for some pre-defined models including regression, classification and ranking.
- Hyperopt

In both cases, train a Keras Feed Forward neural network


