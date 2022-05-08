# Analysis of Charity Success Prediction
## Overview
The client has provided a CSV file containing information on charities that their company has funded over the years. With this data, they want to be able to predict the success of a charity that uses their funding.
### Purpose
Utilizing sklearn and tensorflow in Python, I will build a binary classifier that will be able to predict whether a charity has used their funding successfully. After the model is built, I will optimize it in order to reach 75% accuracy.
## Results
- Data Preprocessing
    - The target for this model will be whether the charity was successful or not, which is contained within the column **IS_SUCCESSFUL**.
    - The features for this model will be: type of application, affiliated sector of the industry, government organization classification, use care for funding, organization type, active status, income classification, special consideration for application, and funding amount requested. These will be contained within the **APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, USE_CASE, ORGANIZATION, STATUS, INCOME_AMT, SPECIAL_CONSIDERATIONS**, and **ASK_AMT** columns respectively.
    - The variables that do not need to be included in this model are contained within the **EIN** and **NAME** columns. These variables are used for identification only and have no meaning behind them that could affect the model, so they will be removed before modeling.

- Compiling, Training, and Evaluating the Model
    
    ![Model_Design.png](https://github.com/Lavernus/Neural_Network_Charity_Analysis/blob/main/Images/Model_Design.png)
    - For the model setup, I chose to use only two layers at first, with 8 and 5 neurons respectively. I wanted to keep the model simple at first so that I could avoid over-fitting, as well as provide a base from which optimization could build on. For the activation functions, I chose Relu for the hidden layers and Sigmoid for the output layer. I thought that Relu was the best choice for the input features since the features were all positive and some were nonlinear, and Sigmoid was the best choice for the output layer since **IS_SUCCESSFUL** was a binary value.

    ![Performance1.png](https://github.com/Lavernus/Neural_Network_Charity_Analysis/blob/main/Images/Performance1.png)
    - With the first model, performance was around 65% accuracy, which isn't terrible, but not at the target of 75%.
    - Optimization for this model was a battle. 
        - I first tried increasing the epochs of the model training in order to give the model increase the amount of information provided to each neuron. This resulted in a lowered accuracy.
        - I tried increasing the amount of hidden layers and added neurons instead, which would allow the model more opportunities to train on activated input values. This also decreased the accuracy, though by a smaller amount. 
        - I then removed a variable to see if it was causing noise due to outliers and changed the activation of the output layer from Sigmoid to Tanh. This resulted in an even lower accuracy score. 
## Summary
Throughout all of my optimization attempts, this model was unable to reach a 75% accuracy for prediction of success. Due to this, I am unable to recommend it as a useful tool for predicting the success of charities that accept the funding from the client's company. 
### Recommendations
If you wished to stick to using a neural network in future iterations, I would recommend binning the **ASK_AMT** column into ranges and transforming the variables into binary values for each range. This would allow you to use the sigmoid function for the hidden layers since all of the input features would then be binary values. Having the same type of data, in this case binary, for each feature would allow the activation function to work more effectively. 

I would suggest, however, pivoting to an entirely different method of modeling charity success. You could use a supervised machine learning model, such as an ensemble classifier, which are best used for determining outcomes that are on a binary. That would be perfect for this application since success is a yes or no question. It would also allow you to judge the precision for each outcome, giving you a greater idea of the effectiveness of the model.

