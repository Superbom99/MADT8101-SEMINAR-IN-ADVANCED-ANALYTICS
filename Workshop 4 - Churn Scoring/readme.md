# Churn Scoring
![Generic badge](https://img.shields.io/badge/Concept-red) ![Generic badge](https://img.shields.io/badge/Presentation-gold) ![Generic badge](https://img.shields.io/badge/Python-yellow) ![Generic badge](https://img.shields.io/badge/XGBoost-red)


Imagine you have a favorite ice cream shop, and you go there all the time to buy their delicious ice cream. Churn scoring is like predicting whether you might suddenly stop going to that ice cream shop and switch to another one.

Churn means when people stop using a service or buying a product from a company. So, churn scoring is when a company tries to figure out which customers are more likely to leave and go somewhere else. They do this by looking at different things like how often you visit the shop, how much you like their ice cream, and maybe even if they change the flavors often.

They take all this information and use it to give you a "churn score." If your churn score is high, it means you might be thinking about leaving the ice cream shop. The company can then try to do something special to make you stay, like giving you a discount or introducing new exciting flavors to keep you interested.

In a more technical way, churn scoring involves analyzing data about customers to find patterns that might show who's likely to leave. This helps the company take action before you actually stop coming to the shop. So, churn scoring is like a clever way for companies to guess who might stop being their customers and try to keep them happy!

### Step 1: Import the libraries

The first step is to import the libraries that we will need. These include:

- pandas: for data manipulation
- numpy: for mathematical operations
- scikit-learn: for machine learning

      import pandas as pd
      import numpy as np
      from sklearn.ensemble import RandomForestClassifier

### Step 2: Load the dataset

The next step is to load the dataset. We can do this using the read_csv() function from the pandas library.

    dataset = pd.read_csv('churn_data.csv')

### Step 3: Explore the dataset


Before we start building our model, it is important to explore the dataset. This will help us to understand the data and identify any potential problems.

We can explore the dataset using the following commands:

- head(): to display the first few rows of the dataset
- describe(): to get a summary of the statistical distribution of the data
- info(): to get information about the data types and missing values

      dataset.head()
      dataset.describe()
      dataset.info()

### Step 4: Select the features

The next step is to select the features that we will use to build our model. We need to select features that are predictive of customer churn.

We can select the features using the following steps:

- Identify the features that are related to customer churn.
- Remove features that are not relevant or that are too noisy.
- Normalize the features so that they have a similar scale.

      # Identify the features that are related to customer churn.
      churn_related_features = [
          'tenure',
          'monthly_charges',
          'contract_type',
          'payment_method',
          'number_of_calls',
          'number_of_texts',
          'number_of_data_usage'
      ]
      
      # Remove features that are not relevant or that are too noisy.
      not_relevant_features = ['customer_id', 'gender']
      noisy_features = ['customer_name']
      
      # Normalize the features.
      for feature in churn_related_features:
          dataset[feature] = (dataset[feature] - dataset[feature].mean()) / dataset[feature].std()

### Step 5: Build the model

Now that we have selected the features, we can build the model. We will use a random forest classifier for this task.

A random forest classifier is an ensemble learning algorithm that builds multiple decision trees and then combines their predictions to make a final decision.

      # Create a random forest classifier.
      model = RandomForestClassifier(n_estimators=100)
      
      # Fit the model to the training data.
      model.fit(X_train, y_train)

### Step 6: Evaluate the model

Once the model is built, we need to evaluate its performance. We can do this using the following metrics:

- Accuracy: the percentage of predictions that are correct
- Precision: the percentage of positive predictions that are actually positive
- Recall: the percentage of actual positives that are predicted as positive

      # Evaluate the model on the test data.
      y_pred = model.predict(X_test)
      
      accuracy = np.mean(y_pred == y_test)
      precision = np.mean(y_pred[y_test == 1])
      recall = np.mean(y_test[y_pred == 1])




