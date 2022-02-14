# Quick guide on cleaning a dataset using pandas

## Table of content
- The good world of data
- 

# Introduction
Data is said to be true

## The good world of data
It's evident all around us that data is now driving every single decision we make as indiviuals or corporate bodies. With every activity performed we are dishing tones of data either structured or unstructured. However means the data is given, one common factor is that insight can be generated from any collected data but our insight won't be clear if the data is not cleaned and well prepared to provide the insight we want.When using data, most people agree that your insights and analysis are only as good as the data you are using.

## The Art of data cleaning
There are currently may apporach for cleaning a dataset and it depends on the type of dataset. A general apporach to data cleaning will be to:
- Remove any duplicate
- Fix structural errors
- Filter unwanted outliers
- Handle missing data
- Validate and QA

For this guide we will be working on handling missing data in our dataset using Jupyter Notebook. The full Jupyter notebook script can be downloaded from the github repo [here](https://github.com/RoyalVee/Quick-data-cleaning-guide-with-pandas.git)


## Step 1 : Import the needed packages
The first step is to import the packages needed for the cleaning operation.

```
import pandas as pd
import pickle as pk
import matplotlib.pyplot as plt
from PIL import Image
from IPython.display import display
```

## Step 2 : Read the Raw file into your script
Load all the files you need to clean into you notebook.
for this guide we will be using a food balance dataset. You can try out with another dataset.

The dataset used for this guide can be downloaded from my github repository [here](https://github.com/RoyalVee/Quick-data-cleaning-guide-with-pandas.git)

```
data  = pd.read_csv("Food Balance data.csv")
```
view the loaded data.

```
data
```
Output:
![](image1.png)

load the data into a dataframe
```
df = pd.DataFrame(data)
```

## Step 3 : Dectect missing values
Detect missing values and count missing values by columns.

- check the data type of each column in your dataset which will guide on how each column is cleaned.
```
df.dtypes
````

```
Output:
Area Code         int64
Area             object
Item Code         int64
Item             object
Element Code      int64
Element          object
Unit             object
Y2010           float64
Y2010F           object
Y2011           float64
Y2011F           object
Y2012           float64
Y2012F           object
Y2013           float64
Y2013F           object
Y2014           float64
Y2014F           object
Y2015           float64
Y2015F           object
Y2016           float64
Y2016F           object
Y2017           float64
Y2017F           object
Y2018           float64
Y2018F           object
Y2019           float64
Y2019F           object
dtype: object
```

- check for NaN and Detect missing values in the dataset. count the number of missing values in the dataset by columns.
```
df.isnull().sum()
```

```
Output:
Area Code           0
Area                0
Item Code           0
Item                0
Element Code        0
Element             0
Unit                0
Y2010           29045
Y2010F          25379
Y2011           29031
Y2011F          25367
Y2012           27723
Y2012F          23998
Y2013           27927
Y2013F          26741
Y2014           27646
Y2014F          25893
Y2015           27562
Y2015F          25799
Y2016           27646
Y2016F          25911
Y2017           27451
Y2017F          26582
Y2018           27302
Y2018F          27086
Y2019           27374
Y2019F          27366
dtype: int64
```

## Step 4 : Drop or Fill missing values
At this point, based on your understanding of what you intend to use your dataset for you can proceed to either drop of fill the missing vaules in the dataset.

### For this guide, we will do the follwoing:

- Drop all rows with any missing vaules, load the result to a new dataframe (cleaned_data1) and serialize the data.
- Drop all rows with all it's columns having missing values and load the result to a new dataframe (cleaned_data2) and serialize the data.
- Drop all rows with it's columns from Y2010 to Y2019 having missing values (cleaned_data2) and serialize the data.

