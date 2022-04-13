# Time Series Outlier Detection
This is a simple outlier detection algorithm developed using Moving Average. The data used is from a kaggle competition and can be found [here](https://www.kaggle.com/c/avazu-ctr-prediction). I am using a subset of 5M rows from the train dataset for this practice. If you have the prerequisites to use the full data set feel free to do so. If you are unsure how to subset the data please check out the steps below. 

1. Subsetting data on Linux:
  * *open a terminal in the file directory (where yo have saved the data)*
  * *type the following command to display the first 10 lines of data from the file: head -10 train.csv*
  * *using the same command, change the number of lines you would like to preview and use the > command to save it to another file like so: head -2000000 train.csv > subsetTrain.csv*

2. Subsetting data on Windows:
  * *open a PowerShell in the file directory*
  * *use the following command to display first 10 lines of data: get-content train.csv | select-object -first 10*
  * *using the same command, change the number of lines you would like to preview and use the Out-File command to save it to another file like so: get-content train.csv | select-object -first 2000000 | Out-File ".\subsetTrain.csv"*

### About the data
The data set includes a lot of dimensional fields with (categorical) information about the environment
(device, location, etc) but we are only concentrating on CTR and time series relevant fields, such as: 
* click: 0/1 for non-click/click
* hour: format is YYMMDDHH, so 14091123 means 23:00 on Sept. 11, 2014 UTC.

### About the algorithm
To achieve a moving average series we use linear convolusion. By theory a moving average signal is a form of convolusion. We first calculate the CTR over time, then we define a window for our moving average. We create a vector that represent a moving average with length = window and amplitude of 1/window. We calculate the moving average (rolling mean) using the np.convolve method. After that we calculate the residuals, stds and plot the results. 
