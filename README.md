# User Manual for test_basket_asian_bestofasian

The author of this code is Wanqi Li. This code is written to test ADMAT 2.0 on finding gradients for basket options, Asian options, and best of Asian options. In order to run it, you require ADMAT 2.0 with jacobianst.m and MATLAB 2016b or later.

This user manual assumes a basic understanding of automatic differentiation. Introduction to automatic differentiation can be found in following books.

Coleman, T. F., & Xu, W. (2016). Automatic Differentiation in MATLAB using ADMAT with Applications. Society for industrial and applied mathematics.

# Table of Contents

### 1. Basket Options

* Initialize parameters
  
* Time required for gradient computation
  
* Space required for gradient computation
  
* Option value and gradient outputs, if interested
  
### 2. Asian Options

* Initialize parameters
  
* Time required for gradient computation
  
* Space required for gradient computation
  
* Option value and gradient outputs, if interested

### 3. Best of Asian Options

* Initialize parameters
  
* Time required for gradient computation
  
* Space required for gradient computation
  
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

In this experiment, these are the only two parameters to change. The goal is to find the time (sec) required and space (MB) required for different combinations of Monte Carlo (MC) instances and batch sizes. Batch size represents number of paths in each batch. In the structured test case below:

`Param.mc_insts` represents MC instances, i.e. MC instances = 10000

`Param.batch_size` respresents batch size, i.e. batch size = 100

![mcpath_batchsize](https://user-images.githubusercontent.com/31410379/29796222-01f72d1e-8c1e-11e7-80a9-da312f88ed15.PNG)

Note: When MC instances equals to batch size, the code is not exploiting structure, i.e. plain reverse mode. This is used as a control case to show the effect on time and space after exploiting structured AD. Below is an example of plain reverse mode AD:

`Param.mc_insts` represents MC instances, i.e. MC instances = 10000

`Param.batch_size` respresents batch size, i.e. batch size = 10000

### Step 2. Time required for gradient computation

#### Use tic toc and comment out the other two options in the function:

`tag_weighted` represents basket options in the function `test_basket_asian_bestof()`

1. For time required by basket options, put tic toc around `run_test(tag_weighted)`.

2. Comment out `run_test(tag_asian)` and `run_test(tag_best_of).

3. Run the function `test_basket_asian_bestofasian()`.

4. For `Param.mc_insts` = 10000 and `Param.batch_size` = 100, the total time (i.e. option pricing + gradient computation) required for the basket option is 13.27 seconds.


