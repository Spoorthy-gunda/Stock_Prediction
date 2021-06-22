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
Method 1: 
