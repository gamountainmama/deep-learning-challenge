# deep-learning-challenge

Overview   

The purpose of this analysis was to create a model to predict whether a charity will receive the requested funding, given multiple features to consider.   

Results   

Data Preprocessing   

- The target variable was the IS_SUCCESSFUL variable, with 1 being the charity received the money and 0 being they did not.
- The features I chose to use were APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, USE_CASE, ORGANIZATION, INCOME_AMT, and ASK_AMT.
- The features I chose to remove from the model were EIN, NAME, STATUS, and SPECIAL_CONSIDERATIONS. The EIN and NAME for each charity was unique, therefore unnecessary. The STATUS and SPECIAL_CONSIDERATIONS had too few cases to be appropriately used in the model. 

Compiling, Training, and Evaluating the Model   

- I selected four hidden layers and an output layer. The first and third hidden layers use ‘relu’ activation, the second and fourth use ‘tanh’, and the output layer uses ‘sigmoid’. I tried many different combinations of activation functions before finding this combination.
- The input dimension matches the number of columns in the X training data. The output dimension is one, either 0 for no success or 1 for success.
- I used 50 neurons in the first and second layers, 40 neurons in the third layer, and 30 neurons in the fourth layer. I gradually increased the number of neurons to increase the accuracy of the model.
- I was able to achieve 0.7502 or 75.02% accuracy after several tries.
- I increased the accuracy by trying several combinations. My final accuracy was achieved by the following:   
      -- Dropping EIN, NAME, STATUS, and SPECIAL_CONSIDERATIONS columns.
      -- Binning the small value counts of APPLICATION_TYPES and CLASSIFICATION. 
      -- Determining the outliers of the ASK_AMT column and dropping rows with outliers.   
      -- I originally tried binning the ASK_AMT, but this was not enough to reach 75% accuracy.
- I split the remaining data into training data and test data, scaled it, and created the model. I compiled the model using binary_crossentropy, the adam optimizer, and the accuracy metric. I then trained the model using the training data with 100 epochs. Finally, I determined the accuracy of the model using the remaining test data.

Summary   

Overall, I achieved 75% accuracy using four hidden layers with neurons varying from 30 - 50, for a total of 40,651 trainable parameters. Other models could also solve this classification problem by altering the chosen features, activation functions, number of layers and neurons, and epochs. I recommend trying the model without binning the APPLICATION_TYPES and CLASSIFICATION and using more of the ASK_AMT data by setting a higher cutoff value rather than the traditional definition of an outlier.

