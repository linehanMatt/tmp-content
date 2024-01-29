---
title: 'Overfitting'
description: 'Overfitting is a concept in statistical modeling that occurs when a model that has been created represents the data it was built on too closely, but does not represent the real world.'
lastUpdated: '2023-04-24T22:47:02.495Z'
tags: ['dictionary', 'data terms']
---

### Overview

One of the primary reasons we build statistical models is to represent real-world conditions and to create predictions about future outcomes.  Statistical models, by their very nature, are built on training data, historical data collected with observations, and resulting outcomes.  Overfitting occurs when the model is built in a way that makes it very accurate for the training data but a poor predictor of future outcomes.  Another way of thinking about how overfitting happens is to say that the model learned too much from the noise in the training data.

### Example

Let's offer a simple example of overfitting.  Assume we have the following data set we'll use to train a model.

| Name      | Gender | Age |
|-----------|--------|-----|
| Bob       | Male   | 25  |
| Amy       | Female | 26  |
| Fred      | Male   | 33  |
| Mary      | Female | 34  |
| Benedict  | Male   | 57  |
| Gertrude  | Female | 66  |

Let's assume we used this data set to train a model that would predict someone's age based on their name and gender.  One way we could make the prediction is by using the number of characters in someone's name (in effect, we're creating a new feature, a process called feature engineering) as the strongest predictor of their age.

We find that if we use the length of the name alone, we can create a pretty accurate model.

| Name     | Length | Gender | Age | Prediction | Difference |
|----------|--------|--------|-----|------------|------------|
| Bob      | 3      | Male   | 25  | 24         | -1         |
| Amy      | 3      | Female | 26  | 24         | -2         |
| Fred     | 4      | Male   | 33  | 32         | -1         |
| Mary     | 4      | Female | 34  | 32         | -2         |
| Benedict | 7      | Male   | 57  | 56         | -1         |
| Gertrude | 8      | Female | 66  | 64         | -2         |

While this result is pretty accurate and enterprise, a statistician might want the model to be an even better prediction of the training data.  If we take a close look at the results, we'll notice that the prediction for each male in the data set is exactly one year below the actual age.  For each woman, it is precisely two years below.  We could adjust our model to incorporate gender and have the new model predict age as eight times the name length plus one for males and eight times the name length plus two for females.

| Name     | Length | Gender | Age | Prediction | Difference |
|----------|--------|--------|-----|------------|------------|
| Bob      | 3      | Male   | 25  | 24         | 0          |
| Amy      | 3      | Female | 26  | 24         | 0          |
| Fred     | 4      | Male   | 33  | 32         | 0          |
| Mary     | 4      | Female | 34  | 32         | 0          |
| Benedict | 7      | Male   | 57  | 56         | 0          |
| Gertrude | 8      | Female | 66  | 64         | 0          |

We now have a perfect fit for our training data, which naturally seems to be a good thing.  Problems begin to arise when we try to use our model for future observations as can be demonstrated with the following data set  
  
| Name     | Gender | Age | Prediction | Difference |
|----------|--------|-----|------------|------------|
| Brooklyn | Female | 18  | 66         | 48         |
| Abigail  | Female | 26  | 58         | 32         |
| Bo       | Male   | 45  | 17         | -28        |
| Jonathan | Male   | 55  | 65         | 10         |

As you can see, even though the model was excellent (in fact, perfect) at predicting our first data set.  It is quite bad at predicting subsequent data.  This phenomenon is overfitting  
  
#### Preventing Overfitting

There are several techniques used to avoid overfitting.

#### Test Data Sets

Using test data sets is a technique where a portion of the training data is held back when creating the model.  The subset of the data that is held back is then tested against the model after it has been built.  If the model has overfitting, it will likely do a lousy job of predicting the values in the test data set.

#### Adding Additional Observations / Features

Adding additional data to a model may provide the model with a better foundation to make its predictions.  Adding more data could come in the form of adding more rows of data or adding additional features (adding more columns).  This technique will not always work, and one has to be careful not to introduce more noise into the model and causing more overfitting.  

In the example above, had more rows been added to our training set, our simple model would have broken down pretty quickly.  While that would have resulted in overfitting, it is entirely likely that using just someone's name and gender; it is impossible to create a model that accurately predicts their age.  To fix that problem, we might have to introduce additional features into the training data (ex: height, number of siblings, hair color) to have a sufficiently predictive model.

#### Feature Selection

Contrasting the strategy of adding more training data to the model, sometimes the best way to prevent overfitting is to remove any features from the model that are noise, but are being used by the model to make predictions.  As was stated above, one way to think about overfitting is that the model is using noise instead of signal to produce its predictions.  

### Using Narrative to Prevent Overfitting

Narrative's Data Streaming Platform can be leveraged to prevent overfitting using the strategies discussed previously.  The ease in buying data lets the team that is building the model quickly test a number of hypotheses as to how to fix overfitting.

#### Adding Additional Observations / Features Using Narrative

If a company that is using Narrative is experiencing overfitting in their models, they might consider adding additional observations or features to their data set. Adding additional rows or columns using Narrative would entail:

* Matching the Narrative data type that contains the same features in the data set being used to train the model.  
* Creating an order for that data type.
* If the desire is only to add new rows to the training data, the user should make sure to create an exclusion filter to prevent buying observations that already exist in the training set.
* If the user is looking to add additional columns, an inclusion filter should be created to buy only records with a matching key to the key being used in the training set.
* Use a destination to send the purchased data to the system where the model is being built so the new data can be incorporated into the training.

### Additional Resources

* XKCD: [Electoral Precedent](https://xkcd.com/1122/)
* Wikipedia: [Overfitting](https://en.wikipedia.org/wiki/Overfitting)
