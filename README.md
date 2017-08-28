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

For this example, we will initialize 10 underlying assets and 5 baskets. The number of assets and number of baskets will be keep constant for this experiment. 

![n_asset](https://user-images.githubusercontent.com/31410379/29795930-8fdb63b8-8c1c-11e7-8a18-357006292e74.PNG)
Number of underlying assets


Nuber of baskets
