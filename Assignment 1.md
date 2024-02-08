
# A1.data.csv
| Length | Width |
| ---- | ---- |
| 5.099 | 2.936 |
| 5.325 | 2.701 |
| 5.263 | 2.84 |
| 6.563 | 3.991 |
| 5.279 | 2.687 |
| 5.413 | 2.716 |
| 5.978 | 3.594 |
| 5.872 | 3.472 |
| 6.183 | 3.902 |
| 5.105 | 2.941 |
| 5.176 | 2.719 |
| 5.314 | 2.777 |
| 5.236 | 2.975 |
| 5.09 | 2.715 |
| 6.303 | 3.791 |
| 5.204 | 2.96 |
| 5.477 | 3.465 |
| 5.927 | 3.438 |
# Part 1

## (a) Calculate the mean, median, and standard deviation of *length*.

### **Calculating the Mean:**
The formula for the mean is: 
$\bar{x} = {{\sum_{i=1}^{N}x_i} \over N} = {{x_1+x_2+...+x_N}\over{N}}$

Therefore the mean for the attribute *length* is: 
$\bar{x} = {{\sum_{i=1}^{N}x_i} \over N}$
$= {{5.099 + 5.325 + 5.263 + 6.563 + 5.279 + 5.413 + 5.978 + 5.872 + 6.183 + 5.105 + 5.176 + 5.314 + 5.236 + 5.09 + 6.303 + 5.204 + 5.477 + 5.927}\over{18}}$
$= {99.807 \over 18} = 5.54483333333 \approx 5.545$
**Therefore the mean is approximately $5.545$**.
### Calculating the Median
The median is the middle value of the data set. 
In order to find the middle value, we need to make sure our data set is *ordered*. Below is the data set for length with *ordinal* values: 
$[5.09, 5.099, 5.105, 5.176, 5.204, 5.236, 5.263, 5.279, 5.314, 5.325, 5.413, 5.477, 5.872, 5.927, 5.978, 6.183, 6.303, 6.563]$
The number of data values in the attribute *length* is 18, which means that the median will be mean of the two middlemost values which are $5.314$ and $5.325$. 
$median = {5.314+5.325 \over 2} = {10.639 \over 2} = 5.3195 \approx 5.319$ 
**Therefore the median is approximately $5.319$**.

### Calculating the Standard Deviation
The standard deviation is the square root of the *variance* of a data set. The *variance* of a data set can be calculated using the following formula: 
$\sigma^{2} = {1 \over N}\sum^{N}_{i=1}x^{2}_{i}-\bar{x}^{2}$
where $\sigma^{2}$ represents the *variance*, $\bar{x}$ represents the mean, $N$ represents the number of values in the attribute, and $x_{i}$ is the value in the attribute that corresponds with index $i$ in the attribute.

Therefore the *variance* is:
$\sigma^{2} = {1 \over N}\sum^{N}_{i=1}x^{2}_{i}-\bar{x}^{2}$
$= {1\over 18}\sum^{18}_{i=1}x^{2}_{i}-5.545^{2}$
$\sum^{18}_{i=1}x^{2}_{i} = 557.093$
$\sigma^{2} = {1 \over 18}557.093-30.747 = 0.202611111$

The standard deviation is the square root of the *variance* i.e. the standard deviation is $\sqrt{\sigma^{2}} = \sigma$.

$\sigma = \sqrt{\sigma^{2}} = \sqrt{0.202611111} = 0.450123439 \approx 0.45$
**Therefore the Standard Deviation is approximately $0.45$.**
### Commenting on these Calculations
We have a mean value of $5.545$, a median value of $5.319$, and a standard deviation of $0.45$. These values give us insight on the central tendency of the attribute *length*. The difference between the mean and the median is very small as $5.545 - 5.319 < 1$, which indicates that the data is almost symmetric.  The standard deviation of $0.45$ is also very small, which indicates that there is not a great amount of variability within the data set rather the values tend to be very close to the mean. 
## (b) Draw the boxplot for *length* and *width*.

### Creating the Boxplots
We can generate a boxplot in Python using the following code:
```
def get_list(col_name):
	data = pandas.read_csv(file_name, usecols=[col_name])
	return data[col_name].tolist()

def boxplot(length_values, width_values):
    data = {"length": length_values, "width": width_values}
    df = pandas.DataFrame(data)
    df.boxplot()
    plt.show()

def main():
	length = get_list("length")
	width = get_list("width")
	boxlpot(length, width)

main()

```
![[Figure_1.png]]
### Commenting on the Boxplots
The whiskers of the boxplot correspond to the minimum and maximum values for their respective data sets. The top and bottom edges of the boxes represent the $Q_{1}$ and $Q_{3}$ values. The line in the middle of each box represents the respective median values. 

We can clearly see that the boxplot for *length* is much higher than the boxplot for *width*, indicating that the values for *length* are always greater than those for *width*.  When looking closely are the boxplot for *length*, we see that the median is closer to the minimum $Q_{1}$ value This indicates that there is a positive skew in the distribution for *length*. This is the same case for the boxplot for *width*. Since they are both positively skewed, it indicates that their data distributions take similar shapes. The height of each box also appears to be the same, which indicates that both attributes have the same inter-quartile range or $IQR$.  This implies that both data distributions have the same central tendency.


## (c) Draw a scatter plot and a q-q plot based on these two variables.
### Creating the Scatter Plot
The scatter plot will show us the relationship between the two attributes *length* and *width*.
Using the following Python code, we can create this scatterplot:
```
import pandas, statistics
import matplotlib.pyplot as plt

def get_list(col_name):
	data = pandas.read_csv(file_name, usecols=[col_name])
	return data[col_name].tolist()

def scatterplot(length, width):
	data = {"length": length, "width": width}
	df = pandas.DataFrame(data)
	df.plot.scatter(x='length', y='width')
	plt.show()

def main():
	length = get_list("length")
	width = get_list("width)
	scatterplot(length, width)

main()
```

![[Figure_2 1.png]]
### Commenting on the Scatter Plot
The values for *length* are plotted against their respective values for *width*. When all of these values are put together in a scatterplot, this shows us the relationship that the two attributes *length* and *width* have. 

We can see that the data values on the scatter plot does tend to follow the straight line, but it definitely does not follow the line perfectly. This indicates that there is a correlation between *length* and *width* but it is not an extremely strong correlation. This correlation suggests that the length is, the larger the width tends to be as well. However since the correlation is not perfect, we cannot say that the length and width will always be similar values. 

Within the first quarter of the scatter plot, it seems to indicate that when the length is a lower value, the width can vary far from the length. However, in the second half of the scatter plot, it seems to indicate that the width tends to get closer to the length as the length values are high values.
### Creating the Quantile-Quantile Plot
A Quantile-Quantile plot or Q-Q plot is a graphical representation which can help us determine whether or not if two data sets share a common distribution. First we will sort length and width in ascending order to create quantiles for each data value.

*length* in quantiles: 
$[5.09, 5.099, 5.105, 5.176, 5.204, 5.236, 5.263, 5.279, 5.314, 5.325, 5.413, 5.477, 5.872, 5.927, 5.978, 6.183, 6.303, 6.563]$
*width* in quantiles:
$[2.687, 2.701, 2.715, 2.716, 2.719, 2.777, 2.84, 2.936, 2.941, 2.96, 2.975, 3.438, 3.465, 3.472, 3.594, 3.791, 3.902, 3.991]$
We will then plot these quantiles against each other, using Python:
```
import pandas, statistics
import matplotlib.pyplot as plt

def get_list(col_name):
	data = pandas.read_csv(file_name, usecols=[col_name])
	return data[col_name].tolist()

def scatterplot(x, y):
	data = {"length": x, "width": y}
	df = pandas.DataFrame(data)
	df.plot.scatter(x='length', y='width')
	plt.show()

def qqplot(x, y):
	data = {"length": sorted(x), "width": sorted(y)}
	df = pandas.DataFrame(data)
	df.plot.scatter(x="length",y="width")

	plt.plot([min(df["length"]), max(df["length"])], [min(df["width"]), max(df["width"])], color='red', linestyle='--')

	plt.show()

def main():
	length = get_list("length")
	width = get_list("width)
	qqplot(length, width)

main()
```
![[Figure_3 1.png]]

### Commenting on the Quantile-Quantile Plot
The quantiles of *length* are plotted against the quantiles of *width*, which shows us the relationship between the distributions of *length* and *width*. 

We can clearly see that the data points tend to follow a straight line, which suggests that the distributions of *length* and *width* are very similar. However, there does appear to be one data point which is places quite far from the line which indicates that there is an outlier. 
## (d) Can you find (roughly) the first quartile (Q1) and the third quartile (Q3) of *length*?
We have already previously established that $median = 5.319$.
To find the rest of the variables, we will sort the data set for *length* in ascending order:
$[5.09, 5.099, 5.105, 5.176, 5.204, 5.236, 5.263, 5.279, 5.314, 5.325, 5.413, 5.477, 5.872, 5.927, 5.978, 6.183, 6.303, 6.563]$
From this we can easily find that $min = 5.09$ and $max = 6.563$.

$Q_{1}$ is the median of the lower half of the original data set. This data set can be reduced to:
$[5.09, 5.099, 5.105, 5.176, 5.204, 5.236, 5.263, 5.279, 5.314]$
The lower half of the data consists of 9 data values, so $Q_{1}$ must fall on the fifth data value which is $5.204$ therefore $Q_{1} = 5.204$.
$Q_{3}$ is the median of the upper half of the data set which can be reduced to:
$[5.325, 5.413, 5.477, 5.872, 5.927, 5.978, 6.183, 6.303, 6.563]$
From this we can see that $Q_{3} = 5.927$.

## (e) How is a q-q plot different from a quantile plot?

A Q-Q plot shows the quantiles of one data set being plotted against the quantiles of another data set. A quantile plot shows the quantiles of one data set being plotted against the respective percentiles that the particular quantile corresponds to.  Quantile plots allow us to observe which data values correspond to a particular percentage of the total amount of data values i.e. a quantile plot shows us how a data set's values correspond to the number of data values the data set contains or its **distribution**. Q-Q plots allow us to directly compare two different sets of quantiles i.e. a Q-Q plot shows us how one distribution compares to another distribution.

## (f) Calculate the correlation coefficient (Pearson’s product moment coefficient). What is the correlation between two attributes?

The formula for Pearson's Product Moment Coefficient is as follows:
$r_{A,B} = {\sum_{i=1}^{n}(a_{i}b_{i}) - n\bar{A}\bar{B} \over (n-1)s_{A}s_{B}}$
- $a_{i}$ and $b_{i}$ are the data values in the data sets $A$ and $B$.
- $\bar{A}$ and $\bar{B}$ are the mean values for their respective data sets.
- $n$ is the number of tuples ($a_{i},b_{i}$) that exists for the data sets $A$ and $B$.
- $s_{A}$ and $s_{B}$ are the standard deviations for their respective data sets.

For this question, our data sets are *length* and *width*. 
$\bar{A} = 5.545$ as we have already established the mean of *length* in **1.a**.
$s_{A} = 0.45$ as we have already established the standard deviation of *length* in **1.a**.
$\bar{B} = {\sum_{i=1}^{N}(b_{i}) \over N} = 56.62/18 = 3.145$  

$s_{B} = \sqrt{{1 \over N}\sum^{N}_{i=1}b^{2}_{i}-\bar{B}^{2}}$
$\sum{b_{i}^{2}} = 181.638398$
$\bar{B}^{2} = 3.145^{2} = 9.891025$
$s_{B} = \sqrt{{1 \over 18}181.638398 - 9.891025} = \sqrt{0.199997111} = 0.44$
$n = 18$ because there are 18 tuples when *length* and *width* are paired together.

$r_{A,B} = {\sum_{i=1}^{n}(a_{i}b_{i}) - n\bar{A}\bar{B} \over (n-1)s_{A}s_{B}}$
$\sum_{i=1}^{n}(a_{i}b_{i}) = 317.272426$
$r_{A,B} = {\sum_{i=1}^{n}(a_{i}b_{i}) - n\bar{A}\bar{B} \over (n-1)s_{A}s_{B}}$
$= { 317.272426 - (18)(5.545)(3.145)\over (18-1)(0.45)(0.44)}$
$= {3.369976 \over 3.366}$
$= 1.001181224 \approx 1$
Therefore the Pearson's Product Moment Coefficient is approximately $1$. This shows us that the two attributes of *length* and *width* are strongly positively correlated with each other as $r_{A,B} > 0$.

## (g) Normalize the *length* based on z−score normalization.

The formula for z-score normalization is:
$v_{i}^{'} = {v_{i}-\bar{A} \over \sigma_{A}}$
where $v_{i}$ is the value to be normalized, $\bar{A}$ is the mean of the data set, and $\sigma_{A}$ is the standard deviation of the data set.

The values in the attribute *length* are $[5.09, 5.099, 5.105, 5.176, 5.204, 5.236, 5.263, 5.279, 5.314, 5.325, 5.413, 5.477, 5.872, 5.927, 5.978, 6.183, 6.303, 6.563]$
We have established the mean as $3.545$ and the standard deviation $0.45$ for $\bar{A}$ and $\sigma_{A}$ respectively, in **part 1.a**
$\bar{A} = 5.545$
$\sigma_{A} = 0.45$

Since there are many values, we will speed up the normalization calculations using Python:
```
def normalize(mean, sd, value):
	return round((value-mean)/sd,3)

def main():
	mean = 5.545
	sd = 0.45
	values = [5.099, 5.325, 5.263, 6.563, 5.279, 5.413, 5.978, 5.872, 6.183, 5.105, 5.176, 5.314, 5.236, 5.09, 6.303, 5.204, 5.477, 5.927]
	normalized_values = [normalize(mean,sd,value) for value in values]
	print(normalized_values)
	
main()
```
This code prints the z-score normalized values:
$[-0.991, -0.489, -0.627, 2.262, -0.591, -0.293, 0.962, 0.727, 1.418, -0.978, -0.82, -0.513, -0.687, -1.011, 1.684, -0.758, -0.151, 0.849]$
## (h) Normalize the length by z−score normalization using mean absolute deviation instead of standard deviation

The formula for the mean absolute deviation is:
$s_{A} = {1 \over n} \sum{ |v_{i} - \bar{A}|}$
$\bar{A} = 3.545$
$n = 18$

To calculate $\sum{|v_{i} - \bar{A}|}$ quickly we can use Python:
```
def mean_abs_deviation_summation(values, mean):
    values = [abs(value - mean) for value in values]
    return round(sum(values),3)
    
def main():
    values = [5.09, 5.099, 5.105, 5.176, 5.204, 5.236, 5.263, 5.279, 5.314, 5.325, 5.413, 5.477, 5.872, 5.927, 5.978, 6.183, 6.303, 6.563]
    mean = 5.545
    
    print(mean_abs_deviation_summation(values, mean))
    
main()   
```
This code returns $35.997$ so $\sum{|v_{i} - \bar{A}|} = 7.115$
$s_{A} = {1 \over n} \sum{ |v_{i} - \bar{A}|} = {1 \over 18}\times 7.115 = 0.395277777 \approx 0.395$  

Since there are many values, we will speed up the normalization calculations using Python:
```
def normalize(mean, sd, value):
	return round((value-mean)/sd,3)

def main():
	mean = 5.545
	mean_abs_deviation = 0.395
	values = [5.099, 5.325, 5.263, 6.563, 5.279, 5.413, 5.978, 5.872, 6.183, 5.105, 5.176, 5.314, 5.236, 5.09, 6.303, 5.204, 5.477, 5.927]
	normalized_values = [normalize(mean,mean_abs_deviation,value) for value in values]
	print(normalized_values)
	
main()
```
This code prints the normalized values using the mean absolute deviation:
$[-1.129, -0.557, -0.714, 2.577, -0.673, -0.334, 1.096, 0.828, 1.615, -1.114, -0.934, -0.585, -0.782, -1.152, 1.919, -0.863, -0.172, 0.967]$
## (i) Comment on the methods you used in (g) and (h).
1.g involved calculating the z-scores with the standard deviation as a key variable whereas 1.h involved calculating the z-scores with the mean absolute deviation as a key variable replacing the standard deviation. Z-score normalization is valuable for making data sets more robust for data analysis. 

1.g utilized z-scores with the standard deviation as a key variable but because standard deviations are susceptible to outliers, using the standard deviation can affect the z-score normalization. We have already seen in our scatter plot and Q-Q plot that there are outliers present, so this can be problematic. 1.h utilized z-scores with the mean absolute deviation instead, which is far less susceptible to the effects of outliers. Using the mean absolute deviation instead tends to result in a data set that is more robust for data analysis as opposed to using the standard deviation when calculating z-scores. 

# Part 2

## Textbook Question 2.11
##### It is important to define or select similarity measures in data analysis. However, there is no commonly accepted subjective similarity measure. Results can vary depending on the similarity measures used. Nonetheless, seemingly different similarity measures may be equivalent after  some transformation
|  | $A_{1}$ | $A_{2}$ |  
| ---- | ---- | ---- | 
| $x_{1}$ | $1.5$ | $1.7$ |  
| $x_{2}$ | $2$ | $1.9$ |  
| $x_{3}$ | $1.6$ | $1.8$ |  
| $x_{4}$ | $1.2$ | $1.5$ |  
| $x_{5}$ | $1.5$ | $1.0$ |  
###### (a) Consider the data as 2-D data points. Given a new data point, x = (1.4, 1.6) as a query, rank the database points based on similarity with the query using Euclidean distance, Manhattan distance, supremum distance, and cosine similarity.

First we will determine the Euclidean distance, Manhattan distance, supremum distance, and cosine similarity for each value in the database and for the new data point. The new data point will be denoted as $x_{new}$, Euclidean distance will be denoted as $ED$, Manhattan distance will be denoted as $MD$, supremum distance will be denoted as $SD$, and cosine similarity will be denoted as $CS$.

The formula for $ED$ is:
$d(i,j) = \sqrt{(|x_{i_{1}} - x_{j_{2}}|^{2} + |x_{i_{2}} - x_{j_{2}}|^{2} + ... + |x_{i_{p}} - x_{j_{p}}|^{2})}$

The formula for $MD$ is:
$d(i,j) = |x_{i_{1}} - x_{j_{2}}| + |x_{i_{2}} - x_{j_{2}}| + ... + |x_{i_{p}} - x_{j_{p}}|$

The formula for $SD$ is:
$d(i,j) = max^{p}_{f}|x_{if} - x_{jf}|$

The formula for $CS$ is:
$cos(i,j) = {x_{i} \cdot x_{j} \over ||x_{i}|| \times ||x_{j}||}$ 

We will calculate these values using Python:
```
import pandas, statistics, math
import matplotlib.pyplot as plt

def ED(point, new_point):
    sum = abs(new_point[0] - point[0])**2 + abs(new_point[1] - point[1])**2
    distance = math.sqrt(sum)
    return round(distance, 5)

def MD(point, new_point):
    distance = abs(new_point[0] - point[0]) + abs(new_point[1] - point[1])
    return round(distance, 5)

def SD(point, new_point):
    return round(max(abs(new_point[0] - point[0]), abs(new_point[1] - point[1])), 5)

def CS(point, new_point):
    numerator = (new_point[0]*point[0]) + (new_point[1] * point[1])
    denominator = math.sqrt(point[0]**2 + point[1]**2) * math.sqrt(new_point[0]**2 + new_point[1]**2)
    return round(numerator / denominator, 5)

def main():
    data = [(1.5,1.7),(2,1.9),(1.6,1.8),(1.2,1.5),(1.5,1.0)]
    new_point = (1.4, 1.6)

    ED_values = []
    MD_values = []
    SD_values = []
    CS_values = []

    for value in data:
        ED_values.append(ED(value, new_point))
        MD_values.append(MD(value, new_point))
        SD_values.append(SD(value, new_point))
        CS_values.append(CS(value, new_point))

    print("ED: " + str(ED_values))
    print("MD: " + str(MD_values))
    print("SD: " + str(SD_values))
    print("CS: " + str(CS_values))

main()
```
The above code will print out these values:
$ED: [0.14142, 0.67082, 0.28284, 0.22361, 0.60828]$
$MD: [0.2, 0.9, 0.4, 0.3, 0.7]$
$SD: [0.1, 0.6, 0.2, 0.2, 0.6]$
$CS: [0.99999, 0.99575, 0.99997, 0.99903, 0.96536]$

|  | $A_{1}$ | $A_{2}$ | ED | MD | SD | CS |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| $x_{1}$ | $1.5$ | $1.7$ | $0.14142$ | $0.2$ | $0.1$ | $0.99999$ |
| $x_{2}$ | $2$ | $1.9$ | $0.67082$ | $0.9$ | $0.6$ | $0.99575$ |
| $x_{3}$ | $1.6$ | $1.8$ | $0.28284$ | $0.4$ | $0.2$ | $0.99997$ |
| $x_{4}$ | $1.2$ | $1.5$ | $0.22361$ | $0.3$ | $0.2$ | $0.99903$ |
| $x_{5}$ | $1.5$ | $1.0$ | $0.60828$ | $0.7$ | $0.6$ | $0.96536$ |
Now that we have all of the data values, we will rank the data base points in ascending order respective to their distance measure.
$ED: x_{1}, x_{4}, x_{3}, x_{5}, x_{2}$
$MD: x_{1}, x_{4}, x_{3}, x_{5}, x_{2}$
$SD: x_{1}, x_{4}, x_{3}, x_{5}, x_{2}$
$CS: x_{1}, x_{3}, x_{4}, x_{2}, x_{5}$

###### (b) Normalize the data set to make the norm of each data point equal to 1. Use Euclidean distance on the transformed data to rank the data points

Let $x_{new}^{'}$ be the normalized version of the $x_{new}$.
$x_{new}^{1} = ({1.4 \over \sqrt{1.4^{2} + 1.6^{2}}}, {1.6 \over \sqrt{1.4^{2} + 1.6^{2}}}) = (0.658, 0.752)$
Let $A_{1}^{'}$ and $A_{2}^{'}$ be the normalized data sets.

|  | $A_{1}$ | $A_{2}$ | $A_{1}^{'}$ | $A_{2}^{'}$ | $ED$ |
| ---- | ---- | ---- | ---- | ---- | ---- |
| $x_{1}$ | $1.5$ | $1.7$ | ${1.5 \over \sqrt{1.5^{2} + 1.7^{2}}} = 0.662$ | ${1.7 \over \sqrt{1.5^{2} + 1.7^{2}}} = 0.75$ | $\sqrt(\|0.658 - 0.662\|^{2} + \|0.752-0.75\|^{2}) = 0.0047$ |
| $x_{2}$ | $2$ | $1.9$ | ${2 \over \sqrt{2^{2} + 1.9^{2}}} = 0.725$ | ${1.9 \over \sqrt{2^{2} + 1.9^{2}}} = 0.689$ | $\sqrt(\|0.658 - 0.725\|^{2} + \|0.752-0.689\|^{2}) = 0.1$ |
| $x_{3}$ | $1.6$ | $1.8$ | ${1.6 \over \sqrt{1.6^{2} + 1.8^{2}}} = 0.664$ | ${1.8 \over \sqrt{1.6^{2} + 1.8^{2}}} = 0.747$ | $\sqrt(\|0.658 - 0.664\|^{2} + \|0.752-0.747\|^{2}) = 0.008$ |
| $x_{4}$ | $1.2$ | $1.5$ | ${1.2 \over \sqrt{1.2^{2} + 1.5^{2}}} = 0.625$ | ${1.5 \over \sqrt{1.2^{2} + 1.5^{2}}} = 0.781$ | $\sqrt(\|0.658 - 0.725\|^{2} + \|0.752-0.689\|^{2}) = 0.044$ |
| $x_{5}$ | $1.5$ | $1.0$ | ${1.5 \over \sqrt{1.5^{2} + 1^{2}}} = 0.832$ | ${1 \over \sqrt{1.5^{2} + 1^{2}}} = 0.555$ | $\sqrt(\|0.658 - 0.832\|^{2} + \|0.752-0.555\|^{2}) = 0.263$ |

Now that we have all of the data values, we will rank the data base points in ascending order respective to $ED$.
$ED: x_{1}, x_{3}, x_{4}, x_{2}, x_{5}$
