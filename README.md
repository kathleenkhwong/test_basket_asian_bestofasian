# User Manual for test_basket_asian_bestofasian

The author of this code is Wanqi Li (wanqi@outlook.com). This code is written to test ADMAT 2.0 on finding gradients for basket options, Asian options, and best of Asian options. In order to run it, you will need ADMAT 2.0 with jacobianst.m and MATLAB 2016b or later.

This user manual assumes a basic understanding of automatic differentiation. Introduction to automatic differentiation can be found in the following book.

Coleman, T. F., & Xu, W. (2016). Automatic Differentiation in MATLAB using ADMAT with Applications. Society for industrial and applied mathematics.

# Table of Contents

### 1. Basket Options

* Initialize parameters
  
* Time required for option pricing and gradient computation
  
* Space required for option pricing and gradient computation
  
* Option value and gradient outputs, if interested
  
### 2. Asian Options

* Initialize parameters
  
* Time required for option pricing and gradient computation
  
* Space required for option pricing and gradient computation
  
* Option value and gradient output, if interested

### 3. Best of Asian Options

* Initialize parameters
  
* Time required for option pricing and gradient computation
  
* Space required for option pricing and gradient computation
  
* Option value and gradient outputs, if interested
  
# Instructions

## 1. Basket Options

### Step 0. 

Enter "startup" in command line to ensure ADMAT 2.0 has been installed successfully.

![step0](https://user-images.githubusercontent.com/31410379/29795493-79f9a9bc-8c1a-11e7-9a76-7d2c050da54c.PNG)

### Step 1. Initialize Parameters

#### Set number of underlying assets and number of baskets: 

For this example, we will initialize 10 underlying assets and 5 baskets. The number of assets and number of baskets will be keep constant for this experiment. 

![n_asset](https://user-images.githubusercontent.com/31410379/29795930-8fdb63b8-8c1c-11e7-8a18-357006292e74.PNG)

Number of underlying assets

![n_basket](https://user-images.githubusercontent.com/31410379/29795969-be882c00-8c1c-11e7-8199-70896c7472ea.PNG)

Number of baskets

#### Set number of total Monte Carlo instances and batch size:

In this experiment, these are the only two parameters to change. The goal is to find the time (sec) required and space (MB) required by different combinations of Monte Carlo (MC) instances and batch sizes. Batch size represents number of paths in each batch. In the structured test case below:

`Param.mc_insts` represents MC instances, i.e. MC instances = 10000

`Param.batch_size` respresents batch size, i.e. batch size = 100

![mcpath_batchsize](https://user-images.githubusercontent.com/31410379/29796222-01f72d1e-8c1e-11e7-80a9-da312f88ed15.PNG)

Note: When MC instances equals to batch size, the code is not exploiting structure, i.e. plain reverse mode. This is used as a control case to show the effect on time and space after exploiting structured AD. Below is an example of plain reverse mode AD:

`Param.mc_insts` represents MC instances, i.e. MC instances = 10000

`Param.batch_size` respresents batch size, i.e. batch size = 10000

### Step 2. Time required for gradient computation

#### Use tic toc and comment out the other two options in the function:

`tag_weighted` represents basket options in the function `test_basket_asian_bestofasian()`

1. For time required by basket options, put tic toc around `run_test(tag_weighted)`.

2. Comment out `run_test(tag_asian)` and `run_test(tag_best_of)`.

3. Run the function `test_basket_asian_bestofasian()`.

4. For `Param.mc_insts` = 10000 and `Param.batch_size` = 100, the total time (i.e. option pricing + gradient computation) required by the basket option is 13.27 seconds.

![time_basket](https://user-images.githubusercontent.com/31410379/29797202-cd59c408-8c23-11e7-97f8-50119ce2aba8.PNG)

### Step 3. Space required for gradient computation

#### Use profiler and comment out the other two options in the function:

`tag_weighted` represents basket options in the function `test_basket_asian_bestofasian()`

1. For space required by basket options, put `profile -memory on` and `profreport` around `run_test(tag_weighted)`.

2. Comment out `run_test(tag_asian)` and `run_test(tag_best_of)`.

3. Run the function `test_basket_asian_bestofasian()`.

![space_basket](https://user-images.githubusercontent.com/31410379/29797537-a1e7d5a6-8c25-11e7-84ad-0f75d41068d7.PNG)

4. For the basket option with `Param.mc_insts` = 10000 and `Param.batch_size` = 100, the peak memory is 5.64 MB.

![profiler_basket](https://user-images.githubusercontent.com/31410379/29797480-4b142d60-8c25-11e7-8337-9db6dacec1b5.PNG)

### Step 4. Option value and gradient outputs, if interested

#### If interested in the option values and gradients, uncomment the lines specificed below and run `test_basket_asian_bestofasian()` as shown in the previous step:

`z1` represents the vector of option values

`J` represents the Jacobian

![values_output](https://user-images.githubusercontent.com/31410379/29797939-fd7794d6-8c27-11e7-83b6-c881090935fa.PNG)

The lines `J` and `fprintf('option value %f\n', z1)` are usually commented out in the file, i.e. except for demostration in the figure above. Uncomment these two lines if interested in these values. 

## 2. Asian Options

### Step 1. Initialize Parameters

#### Set number of underlying assets:

For this example, we will initialize 10 underlying assets.

![n_asset](https://user-images.githubusercontent.com/31410379/29795930-8fdb63b8-8c1c-11e7-8a18-357006292e74.PNG)

Number of underlying assets

![n_basket](https://user-images.githubusercontent.com/31410379/29795969-be882c00-8c1c-11e7-8199-70896c7472ea.PNG)

Note: No need to change anything here. It does not affect the number of underlying assets for the Asian option leaving it as it. We will have 10 option values as the output.

Everything is the same as basket options except we now use `run_test(tag_asian)` instead of `run_test(tag_weighted)`.

![asian](https://user-images.githubusercontent.com/31410379/29798296-43512dbc-8c2a-11e7-9c84-a09954e41346.PNG)

## 3. Best of Asian Options

Everything is the same as Asian options except we now use `run_test(tag_best_of)` instead of `run_test(tag_asian)`.

![best_of](https://user-images.githubusercontent.com/31410379/29798297-43600490-8c2a-11e7-974d-6f3f4f1cff43.PNG)




