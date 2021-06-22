# STOCK PREDICTION USING LSTM'S
Predicting stock prices is one of the challenging and difficut tasks. Price per stock fluctuates through out day and is effected by various factors. In this project, I use Long Short Term Memory cells(LSTM's) in a model, to train the stock prices.  
### GOAL
The end goal of the model is to predict the price per stock on 61st day based on the per stock prices of the past 60 days.
### PREPARING THE DATASET
Stock prices of Aircanada is used to train the model. The data is downloaded from https://ca.finance.yahoo.com/quote/AC.TO/. For this project, data from 2010-04-28	 to 2021-04-27 is considered. As a first step, highest price per stock in a day is extracted and stored. Each datapoint contains a series of 60 prices from day i to i+59 as the input 'X' and the price of i+60th day as the output 'y'. Loop over 'i' to contruct the whole dataset.  We have a total of 2758 rows of data, so after looping we will have 2698(=2758-60) datapoints.
### SPLITTING INTO TRAIN AND TEST SET

I have explored two differnt ways to split the dataset into traning and test set.
Method 1: Split the datset randomly with 80% as the traning set and 20% as 

### MODEL

### RESULTS AND INSIGHTS
