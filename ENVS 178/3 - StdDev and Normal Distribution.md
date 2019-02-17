[TOC]

**CHAPTER 5**

# The Standard Deviation as a Ruler and the Normal Model

## Standardizing with z-Scores

To **standardize** a value, we subtract the mean and then divide this difference by the SD

- these values are called **standardized values**
- commonly denoted as **z-scores**

$$
z = \frac{y - \bar{y}}{s}
$$

### z-Scores

- measure the distance of a value from the mean in SDs
  - **Positive** z-score of 2 says that a data value is 2 SDs above the mean
  - **Negative** z-score of -1.6 says that a data value is 1.6 SDs below the mean



### Benefits of Standardizing

- compare values from the same data set, or two values measured on different variables or with different scales
- standardized values have been converted from original units to the unit of SDs from the mean
  - easier to understand and read



### Shifting and Scaling

- two steps to find a z-score:

  1. Data are **shifted** by subtracting the mean

     - when we shift the data by adding/subtracting a constant to each value, all measures of position (center, percentiles, min, max) will increase/decrease by the same constant
     - BUT this leaves measures of spread unchanged

     ![](C:\Users\Anugra Shah\OneDrive\University of Waterloo\Winter 2019\notes\ENVS 178\screenshots\shifting.png)

  2. Data are **rescaled** by dividing by the SD

     - divide by a constant to change the units of measurement
     - now interpret Zi as standard deviations relative to mean

![](C:\Users\Anugra Shah\OneDrive\University of Waterloo\Winter 2019\notes\ENVS 178\screenshots\scaling.png)

### Z-scores

1. Does not change the **shape** of the distribution of a variable
2. Changes the **center** by making the mean 0
3. Changes the **spread** by making the standard deviation 1

Standardizing data into z-scores **shifts** the data by subtracting the mean and **rescales** the values by dividing by the standard deviation.



> Example 1: Class exam scores:
>
> Mean = 75.00
>
> SD = 14.25
>
> Calculate the z-scores for students scoring:
>
> a) 75.00
>
> **Step 1:**  SHIFT - subtract the mean: 
> $$
> 75.00 - 75.00
> $$
> **Step 2: ** RESCALE -  divide by the SD:
> $$
> 0 / 14.25 = 0
> $$
> **z-score = 0**
>
> 
>
> b) 82.50
>
> **Step 1:**  SHIFT - subtract the mean: 
> $$
> 82.50 - 75.00 = 7.500
> $$
> **Step 2: ** RESCALE -  divide by the SD:
> $$
> 7.50 / 14.25 = 0.526
> $$
> **z-score = 0.526**



## Normal Models

A smooth curve may fit on the histogram and such curves are called **density curves**

### Density Curves

Any density curve has to satisfy the following conditions:

- always positive or zero
  - otherwise, we'd have negative percentages
- total area under the curve above the x-axis is equal to 1.00

![](C:\Users\Anugra Shah\OneDrive\University of Waterloo\Winter 2019\notes\ENVS 178\screenshots\densitycurve.png)

### Normal Model

**Model:** generalizable and simplifies the understanding of data

#### Rules of the normal model density curve:

1. Always positive or zero
2. Area under the curve = 1



Bell-shaped: symmetric and unimodal 

Controlled by two **parameters**:

**Mean** - "Mu"

**Standard Deviation** - "Sigma"
$$
N(\mu, \sigma)
$$

#### The 68-95-99.7 Rule0.9



In a Normal model:

- about 68% of the values fall within one SD of the mean
- about 95% of the values fall within two SDs of the mean
- about 97.5% of the values fall within three SDs of the mean



![](C:\Users\Anugra Shah\OneDrive\University of Waterloo\Winter 2019\notes\ENVS 178\screenshots\normalmodel.png)



#### Working with Normal Models

1. Plot histogram to check normality (unimodal, symmetrical)
2. Calculate z-scores of observations
3. Loop up **Normal Percentiles**

##### Finding Normal Percentiles

- Table Z is the *standard Normal* table

> Example
>
> ![](C:\Users\Anugra Shah\OneDrive\University of Waterloo\Winter 2019\notes\ENVS 178\screenshots\normalexample.png)
>
> ![](C:\Users\Anugra Shah\OneDrive\University of Waterloo\Winter 2019\notes\ENVS 178\screenshots\normalexample2.png)
>
> 



