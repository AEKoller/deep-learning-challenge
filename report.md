# Report: Deep Learning Model for Alphabet Soup

## Overview of the Analysis

The purpose of this analysis was to create a deep learning model using the provided dataset to predict whether an Alphabet Soup–funded organization will be successful. By accurately predicting the success of funded organizations, Alphabet Soup can make better decisions when choosing which organizations to fund in the future.

# Results

## Data Preprocessing
The target variable for the model is the "IS_SUCCESSFUL" column, which indicates whether the funded organization was successful.
The feature variables for the model are all columns except for "EIN", "NAME", and "IS_SUCCESSFUL". These include:
        - "APPLICATION_TYPE"
        - "AFFILIATION"
        - "CLASSIFICATION"
        - "USE_CASE"
        - "ORGANIZATION"
        - "STATUS"
        - "INCOME_AMT"
        - "SPECIAL_CONSIDERATIONS"
        - "ASK_AMT"
    - The "EIN" and "NAME" columns were removed from the input data because they are identification columns and are neither targets nor features.

    **NOTE**: I spent a great deal of time attempting to tune the model with the "NAME" column removed from the training data. As you can see, I used a Keras tuner to try and tune my model because I was not getting a precision of 75% of greater. I also added a many layers (up to 10,000 x 3 layers) and still was not getting a greater than 75% precision. After discussing the project with Sakib, we found that the "NAME" column *was* included within the feature variables, and that is how a greater than 75% precision was achieved within the answer key. This is incorrect practice, as adding "NAME" to the feature variables effectively leaks the answer key within the training data, and allows the model identify the data *not* because of a mathematical link between variables, but simply because a definitive label exists to link clusters of data together. Regardless, I added "NAME" to the feature variables under Sakib's instruction to achieve a greater than 75% precision. 

## Compiling, Training, and Evaluating the Model
The neural network model architecture consists of:
    - First hidden layer: 100 neurons with ReLU activation
    - Second hidden layer: 30 neurons with sigmoid activation
    - Third hidden layer: 10 neurons with sigmoid activation
    - Output layer: 1 neuron with sigmoid activation

- To attempt to increase model performance, the following steps were taken:
    - Increased the number of neurons in the hidden layers
    - Added additional hidden layers
    - Tried different activation functions (ReLU, sigmoid)
    - Increased the number of epochs during training
    - Attempt to tune the model using keras tuner

- After adding "NAME" back into the feature variables, an accuracy of 0.7869 was achieved

Summary
The deep learning model achieved an accuracy of approximately 78.69% in predicting the success of Alphabet Soup–funded organizations, which was above the 75% requirement. 

As an alternative approach, a Random Forest Classifier could be used to solve this classification problem. Random Forest models have several advantages:

1. They are robust to outliers and can handle non-linear relationships in the data.

2. They automatically perform feature selection during the training process, which can help identify the most important variables for prediction.

3. Random Forest models are less prone to overfitting compared to deep learning models, especially when dealing with a limited dataset.

Given the characteristics of the dataset and the potential advantages of Random Forest models, it may be beneficial to explore this alternative approach and see if it can achieve better performance in predicting the success of Alphabet Soup–funded organizations.