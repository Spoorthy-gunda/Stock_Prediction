# Stock Prediction Using LSTM'S
Predicting stock prices is one of the challenging and difficut tasks. Price per stock fluctuates through out day and is effected by various factors. In this project, I use Long Short Term Memory cells(LSTM's) in a model, to train the stock prices.  
### Goal
The end goal of the model is to predict the price per stock on 61st day based on the per stock prices of the past 60 days.
### Preparing the data
Stock prices of Aircanada is used to train the model. The data is downloaded from https://ca.finance.yahoo.com/quote/AC.TO/. For this project, data from 2010-04-28	 to 2021-04-27 is considered. As a first step, highest price per stock in a day is extracted and stored. Each datapoint contains a series of 60 prices from day i to i+59 as the input 'X' and the price of i+60th day as the output 'y'. Loop over 'i' to contruct the whole dataset.  We have a total of 2758 rows of data, so after looping we will have 2698(=2758-60) datapoints.
### Splitting into train and test set
I have explored two differnt ways to split the dataset into traning and test set.
#### Method 1:
Splitting the dataset based on the time, first 80% of the datapoints are considered as training set and the last 20% of the datapoints.
#### Method 2:
Split the datset randomly with 80% as the traning set and 20% as the test set. Used the function train_test_split from sklearn.model_selection to split the dataset. 

### Results and Insights

On the network with two LSTM layers and one dense layer the following are the results obtained for different methods.
Accuracy calculated based the difference of predicted stock price and the actual stock price. If the difference is less than 0.2, then no loss is added and if the difference is greater than 0.2 then a loss of 1/(size of test set) is added.

Method 1: 57.19% accuracy i.e., 57.19% of datapoints were predicted within difference of 0.2 of the actual price.
Method 2: 82.60% accuracy i.e., 82.60% of datapoints were predicted within difference of 0.2 of the actual price.

When analysed the differences between both the methods the following reasoning seemed apt. In method 1, the trainining set did not include the maximum stock price in the whole data set. The model only learnt about the prices that were in the range of training set. If there is a datapoint in test set that is not in the range of the train set, the model prediction is very different from the actual price. Refer to the following image.
