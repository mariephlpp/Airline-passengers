# Big data project - M2 D3S
## Hélène Lechêne, Marie Philippe, Claire Serraz and Romane Soler

# Our project

"The company is elected every day by its customers." This quote, from François Michelin, CEO of Michelin between 1955 and 1999, is the core of our Big Data project. It clearly shows how important customer satisfaction is for companies. And knowing this satisfaction is often done by means of satisfaction survey.


## Data and objectives

For this project, we focus on aviation data, and more precisely on airline passengers satisfaction. Our data comes from Kaggle (link [here](https://www.kaggle.com/datasets/teejmahal20/airline-passenger-satisfaction?resource=download)). Our goal is to predict the satisfaction level of customers ("satisfied" ou "neutral or dissatisfied"), with respect to various criteria. The explanatory variables concern the traveller (age, gender, loyalty of the customer...), the type of travel (purpose, class...), scores ranking from 1 to 5 given by the customer for his/her satisfaction about criteria (wifi service, seat comfort, baggage handling, cleanliness...) and the flight itself (distance, delays...).


## Preliminary Exploration

We have two notebooks which focus on the data exploration: one is made using *Google Colab* and the second one on *Databricks*. 

The first work is: "Colab_Data_exploration_using_Pandas.ipynb". Launching this notebook recquires to modify the path to the data.

The second one is: "Databricks_Data_exploration_using_Spark.ipynb". Once again, launching this notebook recquires to modify the path to the data.

Through this explanatory part, we focus on those 2 main tasks:
- Removing the modalities equal to 0 for all the score variables,
- Removing lines containing missing values.


## MLlib

Our work concerning MLlib can be found in the following file: "Databricks_Classification_with_MLlib.ipynb".

The MLlib library enables one to do a classification with two packages: spark.mllib and spark.ml. 
Before entering the prediction models, this section contains a data cleaning part.

To perform the classification, one uses 3 algorithms: the Decision Tree Classifier, the Random Forest Classifier and the Gradient-Boosted Tree. The initial dataframe was splitted into 3 parts: a training, a validation and a test.

When using the spark.mllib package, the best model was the Decision Tree Classifier with an accuracy of 92% and when using the spark.ml package, the best model was the Gradient-Tree Boosted with an accuracy of 87%. 

One may add that the results gotten with the spark.mllib package where always better than when using the spark.ml package.

## Pipelines

Our work on Pipelines is in the following file: "Databricks_Classification_with_pipelines.ipynb".

In this section, we use machine learning pipelines to predict the customer satisfaction. A pipeline is specified as a sequence of stages, where each stage either belongs to transformers either to estimators:

- Transformers: is an algorithm which can transform one DataFrame into another DataFrame (ex: Tokenizer, StringIndexer...)
- Estimators: is an algorithm which can be fit on a DataFrame to produce a Transformer (ex: LogisiticRegression, DecisionTree...)

Using the pipeline schema, we build two decision tree models, as decision trees performed best in the previous part:

- One keeping all scores variables ranking from 1 to 5 as initally 
- One where we binarize these variables, by defining a score as "good" when being stricly above to 3.

We observed that the algorithm performed better when keeping the score variables of origin.


## Bonus: Keras (tensorflow)

The part of the project concerning Keras (from tensorflow) can be found in this file: "Colab_Classification_with_keras.ipynb".

A last classification method is used which is using a neural network with Keras. The neural network, even though it isn't very complex, gives from far the best results since one ends up with an accuracy of a little more than 99%. Thus, this would be the best method to classify the customers of the airline company. 
