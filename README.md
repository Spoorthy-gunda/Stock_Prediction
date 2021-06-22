# Stock Prediction Using LSTM'S
Predicting stock prices is one of the challenging and difficut tasks. Price per stock fluctuates through out day and is effected by various factors. In this project, I use Long Short Term Memory cells(LSTM's) in a model, to train the stock prices.  
### Goal
The end goal of the model is to predict the price per stock on 61st day based on the per stock prices of the past 60 days.
### Preparing the data
Stock prices of Air Canada is used to train the model. The data is downloaded from https://ca.finance.yahoo.com/quote/AC.TO/. For this project, data from 2010-04-28	 to 2021-04-27 is considered. As a first step, highest price per stock in a day is extracted and stored. Each datapoint contains a series of 60 prices from day i to i+59 as the input 'X' and the price of i+60th day as the output 'y'. Loop over 'i' to contruct the whole dataset.  We have a total of 2758 rows of data, so after looping we will have 2698(=2758-60) datapoints.
### Splitting into train and test set
I have explored two differnt ways to split the dataset into traning and test set.
#### Method 1:
Splitting the dataset based on the time, first 80% of the datapoints are considered as training set and the last 20% of the datapoints as the test set.
#### Method 2:
Split the datset randomly with 80% as the traning set and 20% as the test set. Used the function train_test_split from sklearn.model_selection to split the dataset. 

### Results and Insights

On the network with two LSTM layers and one dense layer the following are the results obtained for different methods.
Accuracy calculated based the difference of predicted stock price and the actual stock price. If the difference is less than 0.2, then no loss is added and if the difference is greater than 0.2 then a loss of 1/(size of test set) is added.

Method 1: 57.19% accuracy i.e., 57.19% of datapoints were predicted within difference of 0.2 of the actual price.
Method 2: 82.60% accuracy i.e., 82.60% of datapoints were predicted within difference of 0.2 of the actual price.

When analysed the differences between both the methods the following reasoning seemed apt. In method 1, the trainining set did not include the maximum stock price in the whole data set. The model only learnt about the prices that were in the range of training set. If there is a datapoint in test set that is not in the range of the train set, the model prediction is very different from the actual price. This is the resulted in huge loss. The followingfigure is a scatter plot of the actual and predicted prices of the stock. The first plot is only for the test set and the second is for the whole set. It is clearly visible that the model prediction was good when the price range is within the range that it was exposed to.
![method1](https://user-images.githubusercontent.com/77033276/122875305-eddf1d80-d2e8-11eb-87dd-2a879ef540c3.png)

Whereas in method 2 we split the dataset randomly, hence during the training stage the model has access to the highest price and hence made less error on the test set. In one instance the following test set was obtained from random split and we can notice that the model's perfomance was similar for any range of values.
![method2](https://user-images.githubusercontent.com/77033276/122875430-16ffae00-d2e9-11eb-8a25-ae86038f7176.PNG)
