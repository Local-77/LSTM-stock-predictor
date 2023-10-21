# LSTM-stock-predictor
## Homework 18 for shaolin AI, Deep Learning

For this homework, I took on the challenge of creating two different Long Short Term Memory models (LSTM) to achieve the task of predicting future prices of bitcoin.

### Starting Off
The starter code merged two dataframes for me, one with bitcoin historic prices, and another with sentiment on the Fear and Greed (FNG) scale. Following this, it created a function that accepts the column number for the features (X) and the target (y), and puts it in an array thaat the model can read.

### Window Sizes
Here is where we start to experiment with parameters pre model training. There are a few functions here:
- **window_size**: This essentially allows  us to change the window size of previous values that the model uses. We tried a few different windows (ranging from 1-10), but it seemed like 10 was the best option.
- **feature_column:** This function allows us to choose a specific column to use as our model features. This is where the two models differ the most. for the FNG model, the feature column was 0, and for the closing price model, we used 1
- **target_column:** this allowed us to choose a column for our target.

### Model Setup
From here, we do the final bit of preprocessing, by using train_test_split and scaling the data using MinMaxScaler. 

### Building the Model

when building the model, we first assign it to a variable by using model = Sequential(). The steps to building go as follows:
- **number_units:** this defines how many units are in each layer of the LSTM model. We went with 10 for this model.
- **dropout_fraction:** we set this to 0.2 to prevent overfitting.
- **adding the layers:** we use model.add to add three layers to the model, separating each layer with a return_sequences=True function to let the model know there's another layer coming up. We then gave it an output layer, compiled it, summarized it, and trained it.

### We ended with a loss of 0.0049, which I thought was pretty good.

After predicting with both models, I caame to the conclusion that running the model on the closing prices was much better than running it on the FNG index.

### Final Questions
the homework asked three final questions that I will address here:

***Which model has a lower loss?***
- the closing prices model had aa loss of 0.0049, and the FNG model had a loss of 0.0535, so the closing prices model beat it by a long shot.

***Which model tracks the actual values better over time?***
- once again, the closing model wins here. The predictions were almost spot on with the actual prices, whereas the FNG model was good at predicting the rises, but not the dips when compared to the actual.

***Which window size works best for the model?***

- It seemed like 10 was the best option. anything lower resulted in much more significant loss.



