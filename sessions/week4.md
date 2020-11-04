---
layout: single
author_profile: false
title: "Introduction to Python"
#header:
    #og_image: /assets/images/cross-val-logo-v4.jpg
    #overlay_image: /assets/images/joel-filipe-small-warmer.jpg
    #caption: "Photo by [Joel Filipe](https://unsplash.com/@joelfilip) on [Unsplash](https://unsplash.com)"
classes: wide

sidebar:
  nav: "sessions"

---

## Week 4

**ZOOM LINK:** [https://ualberta-ca.zoom.us/j/94407584174](https://ualberta-ca.zoom.us/j/94407584174)

This week we're going to be doing a very brief introduction to working with data in Python. While there are lots of ways to deal with data in Python, the most common method is through the library Pandas. You can learn more about Pandas (here)[https://pandas.pydata.org] if you're interested.  We're going to go over some basic data operations and how to deal with larger datasets in Python.

In this video, Cole will walk you through how we'll be loading data into Google Colab so it's accessible to us to work with.
{% include video id="gZj7JSDfM5w" provider="youtube" %}

In this video Peter will go over how to use the Pandas library to manipulate data and move effectively when working with dataframes.
{% include video id="4rM_C9uWUn8" provider="youtube" %}


Please [click here](https://forms.gle/73FqUaYs1jnGogp26) to fill out the post-session feedback form here! We take your feedback into account in real time, so any changes we can make to help you learn better next week we will make!

-------------------------------------------------------------------------------
# Content Summary

# Importing Data

Importing data via Google Colab is slightly different than doing it in a desktop text editor. However, it's still very easy. We'll load in the file we need via the `google.colab` library.


```python
from google.colab import files
data_to_load = files.upload()
```



<input type="file" id="files-b3170271-c429-4c77-97b1-8f8cbe83aa11" name="files[]" multiple disabled
   style="border:none" />
<output id="result-b3170271-c429-4c77-97b1-8f8cbe83aa11">
 Upload widget is only available when the cell has been executed in the
 current browser session. Please rerun this cell to enable.
 </output>
 <script src="/nbextensions/google.colab/files.js"></script>


Now that we have mnaully navigated to our file and uploaded it, we'll use the `pandas` library and the `io` library to read in our csv so we can use it.


```python
import io
df = pd.read_csv(io.BytesIO(data_to_load['penguins.csv']))
```

We can check out our dataframe by just printing it in a cell.


```python
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>species</th>
      <th>island</th>
      <th>bill_length_mm</th>
      <th>bill_depth_mm</th>
      <th>flipper_length_mm</th>
      <th>body_mass_g</th>
      <th>sex</th>
      <th>year</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Adelie</td>
      <td>Torgersen</td>
      <td>39.1</td>
      <td>18.7</td>
      <td>181.0</td>
      <td>3750.0</td>
      <td>male</td>
      <td>2007</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Adelie</td>
      <td>Torgersen</td>
      <td>39.5</td>
      <td>17.4</td>
      <td>186.0</td>
      <td>3800.0</td>
      <td>female</td>
      <td>2007</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Adelie</td>
      <td>Torgersen</td>
      <td>40.3</td>
      <td>18.0</td>
      <td>195.0</td>
      <td>3250.0</td>
      <td>female</td>
      <td>2007</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Adelie</td>
      <td>Torgersen</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2007</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Adelie</td>
      <td>Torgersen</td>
      <td>36.7</td>
      <td>19.3</td>
      <td>193.0</td>
      <td>3450.0</td>
      <td>female</td>
      <td>2007</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>339</th>
      <td>Chinstrap</td>
      <td>Dream</td>
      <td>55.8</td>
      <td>19.8</td>
      <td>207.0</td>
      <td>4000.0</td>
      <td>male</td>
      <td>2009</td>
    </tr>
    <tr>
      <th>340</th>
      <td>Chinstrap</td>
      <td>Dream</td>
      <td>43.5</td>
      <td>18.1</td>
      <td>202.0</td>
      <td>3400.0</td>
      <td>female</td>
      <td>2009</td>
    </tr>
    <tr>
      <th>341</th>
      <td>Chinstrap</td>
      <td>Dream</td>
      <td>49.6</td>
      <td>18.2</td>
      <td>193.0</td>
      <td>3775.0</td>
      <td>male</td>
      <td>2009</td>
    </tr>
    <tr>
      <th>342</th>
      <td>Chinstrap</td>
      <td>Dream</td>
      <td>50.8</td>
      <td>19.0</td>
      <td>210.0</td>
      <td>4100.0</td>
      <td>male</td>
      <td>2009</td>
    </tr>
    <tr>
      <th>343</th>
      <td>Chinstrap</td>
      <td>Dream</td>
      <td>50.2</td>
      <td>18.7</td>
      <td>198.0</td>
      <td>3775.0</td>
      <td>female</td>
      <td>2009</td>
    </tr>
  </tbody>
</table>
<p>344 rows × 8 columns</p>
</div>



# Data manipulation with `pandas`

As data scientists, the `pandas` library in Python is incredibly important not just for reading in data but for manipulating and exporting said data using Python's computational power. Let's begin by reading in the file we worked with in the previous document:

We will quickly introduce you to a few functions that will be vital for viewing, organizing, and manipulating your data sets by performing them on the penguin data.

## Viewing data

One of the simpler function is the `head` function. Just like in R, this function allows you to take a quick peek at your data by viewing the first few entries. When you're working with very big data and would like to have a quick check on the structure of your data, this function is very useful.


```python
penguins.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>species</th>
      <th>island</th>
      <th>bill_length_mm</th>
      <th>bill_depth_mm</th>
      <th>flipper_length_mm</th>
      <th>body_mass_g</th>
      <th>sex</th>
      <th>year</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Adelie</td>
      <td>Torgersen</td>
      <td>39.1</td>
      <td>18.7</td>
      <td>181.0</td>
      <td>3750.0</td>
      <td>male</td>
      <td>2007</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Adelie</td>
      <td>Torgersen</td>
      <td>39.5</td>
      <td>17.4</td>
      <td>186.0</td>
      <td>3800.0</td>
      <td>female</td>
      <td>2007</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Adelie</td>
      <td>Torgersen</td>
      <td>40.3</td>
      <td>18.0</td>
      <td>195.0</td>
      <td>3250.0</td>
      <td>female</td>
      <td>2007</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Adelie</td>
      <td>Torgersen</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2007</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Adelie</td>
      <td>Torgersen</td>
      <td>36.7</td>
      <td>19.3</td>
      <td>193.0</td>
      <td>3450.0</td>
      <td>female</td>
      <td>2007</td>
    </tr>
  </tbody>
</table>
</div>



It is typical to use `head` as a quick sanity check whenever you import data to ensure it's been imported correctly. There is also a `tail` function that does the same, but with the end of your data. To get a more comprehensive summary of your data, you can use the `info` function, which gives a quick overview of every variable in your data frame. This is especially important if your data has any null values hiding in the file; you can quickly sniff them out using `info`.


```python
penguins.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 344 entries, 0 to 343
    Data columns (total 8 columns):
     #   Column             Non-Null Count  Dtype  
    ---  ------             --------------  -----  
     0   species            344 non-null    object
     1   island             344 non-null    object
     2   bill_length_mm     342 non-null    float64
     3   bill_depth_mm      342 non-null    float64
     4   flipper_length_mm  342 non-null    float64
     5   body_mass_g        342 non-null    float64
     6   sex                333 non-null    object
     7   year               344 non-null    int64  
    dtypes: float64(4), int64(1), object(3)
    memory usage: 21.6+ KB


As you can see, we have a few null values hiding in our penguin data here. We can deal with those later.

For continuous variables, we can get a more thorough statistical summary of the data using the `describe` function.


```python
penguins.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bill_length_mm</th>
      <th>bill_depth_mm</th>
      <th>flipper_length_mm</th>
      <th>body_mass_g</th>
      <th>year</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>342.000000</td>
      <td>342.000000</td>
      <td>342.000000</td>
      <td>342.000000</td>
      <td>344.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>43.921930</td>
      <td>17.151170</td>
      <td>200.915205</td>
      <td>4201.754386</td>
      <td>2008.029070</td>
    </tr>
    <tr>
      <th>std</th>
      <td>5.459584</td>
      <td>1.974793</td>
      <td>14.061714</td>
      <td>801.954536</td>
      <td>0.818356</td>
    </tr>
    <tr>
      <th>min</th>
      <td>32.100000</td>
      <td>13.100000</td>
      <td>172.000000</td>
      <td>2700.000000</td>
      <td>2007.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>39.225000</td>
      <td>15.600000</td>
      <td>190.000000</td>
      <td>3550.000000</td>
      <td>2007.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>44.450000</td>
      <td>17.300000</td>
      <td>197.000000</td>
      <td>4050.000000</td>
      <td>2008.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>48.500000</td>
      <td>18.700000</td>
      <td>213.000000</td>
      <td>4750.000000</td>
      <td>2009.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>59.600000</td>
      <td>21.500000</td>
      <td>231.000000</td>
      <td>6300.000000</td>
      <td>2009.000000</td>
    </tr>
  </tbody>
</table>
</div>



Notice that the `species`, `island`, and `sex` columns are automatically left out, as are any rows that contain null values. This can be quite handy for getting a quick summary of your continuous data before really diving into it.

## Manipulating variable names

For now, let's focus on one of the most important factors of data frames, something that makes them superior to arrays in Python. Notice when we took a quick look at our penguin data that each variable is given a string name. We can look at these names again using the `columns` command.


```python
penguins.columns
```




    Index(['species', 'island', 'bill_length_mm', 'bill_depth_mm',
           'flipper_length_mm', 'body_mass_g', 'sex', 'year'],
          dtype='object')



Renaming these columns is very easy, and we often might want to do so depending on our question. Let's just try a quick example; maybe we want to shorten the name "year" to "yr" for conciseness. We use the `rename` function to accomplish this:


```python
penguins.rename(columns = {'year': 'yr'}, inplace = True)

penguins.columns
```




    Index(['species', 'island', 'bill_length_mm', 'bill_depth_mm',
           'flipper_length_mm', 'body_mass_g', 'sex', 'yr'],
          dtype='object')



A couple quick notes here: the use of the `inplace = True` parameter modifies the object `penguins` automatically, without us needing to use an assignment statement anywhere in our code. In other words, it saves us a bit of writing as otherwise we would have to type `penguins = penguins.rename(columns = {'year': 'yr'})`. Additionally, the notation used to rename objects is known as a dictionary in Python; we won't get into dictionaries here because they are not easy to work with, but they are used for many things in Python.

We can also select variables individually using the column name for any variable. Here, the notation is similar to traditional arrays, as we use the square brackets and the name of the column we would like to select. We can use this to get the statistics for any variable, including discrete variables such as `species`.


```python
penguins["species"].describe()
```




    count        344
    unique         3
    top       Adelie
    freq         152
    Name: species, dtype: object



More thoroughly, we can get a frequency table for every value of `species`.


```python
penguins["species"].value_counts()
```




    Adelie       152
    Gentoo       124
    Chinstrap     68
    Name: species, dtype: int64



We can also very easily make new columns using the same notation. Let's say we want to know if a penguin is above average in size. Maybe we want to make a new boolean column displaying this. We can do that easily using the notation below.


```python
penguins["above_avg_mass_bool"] = penguins["body_mass_g"] > penguins["body_mass_g"].mean()

penguins.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 344 entries, 0 to 343
    Data columns (total 9 columns):
     #   Column               Non-Null Count  Dtype  
    ---  ------               --------------  -----  
     0   species              344 non-null    object
     1   island               344 non-null    object
     2   bill_length_mm       342 non-null    float64
     3   bill_depth_mm        342 non-null    float64
     4   flipper_length_mm    342 non-null    float64
     5   body_mass_g          342 non-null    float64
     6   sex                  333 non-null    object
     7   yr                   344 non-null    int64  
     8   above_avg_mass_bool  344 non-null    bool   
    dtypes: bool(1), float64(4), int64(1), object(3)
    memory usage: 22.0+ KB


## Dealing with bad data

Now, let's get back to those missing values. We did have some NAs in our data, and depending on what task you are looking to complete, these values can be dealt with in many different ways. Sometimes we want to set them to a different value (e.g., 0), but sometimes it is just best to leave them as is. More often though, it is customary to simply remove these rows from the data frame as a means to smooth out future analysis. This is done rather simply in Python, using the `dropna` command.


```python
penguins_good = penguins.dropna()

penguins_good.info()
```

    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 333 entries, 0 to 343
    Data columns (total 9 columns):
     #   Column               Non-Null Count  Dtype  
    ---  ------               --------------  -----  
     0   species              333 non-null    object
     1   island               333 non-null    object
     2   bill_length_mm       333 non-null    float64
     3   bill_depth_mm        333 non-null    float64
     4   flipper_length_mm    333 non-null    float64
     5   body_mass_g          333 non-null    float64
     6   sex                  333 non-null    object
     7   yr                   333 non-null    int64  
     8   above_avg_mass_bool  333 non-null    bool   
    dtypes: bool(1), float64(4), int64(1), object(3)
    memory usage: 23.7+ KB


Notice how the `inplace = True` argument is left out here; we could have included it in the call to `dropna` but we are already assigning this revised data frame to a new variable, and we don't want to modify `penguins` just yet. More importantly though, notice how we have 333 entries in total (based on the second line of the print output) and for each variable, all 333 are non-null!

As mentioned before, we don't always want to simply remove null values; we might occasionally want to replace them with something else. Here I think it would make the most sense to remove them given the data, but for pedagogical purposes, let's replace them instead.


```python
penguin_bill_length = penguins["bill_length_mm"]

penguin_bill_length.head()
```




    0    39.1
    1    39.5
    2    40.3
    3     NaN
    4    36.7
    Name: bill_length_mm, dtype: float64



Let's pretend we want to replace null values with the mean bill length from the entire database. First we need to get the mean, and then we need to replace these null values with that number. This takes a couple lines of code.


```python
mean_bill_length = penguin_bill_length.mean()

penguin_bill_length.fillna(mean_bill_length, inplace = True)

penguins.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 344 entries, 0 to 343
    Data columns (total 9 columns):
     #   Column               Non-Null Count  Dtype  
    ---  ------               --------------  -----  
     0   species              344 non-null    object
     1   island               344 non-null    object
     2   bill_length_mm       344 non-null    float64
     3   bill_depth_mm        342 non-null    float64
     4   flipper_length_mm    342 non-null    float64
     5   body_mass_g          342 non-null    float64
     6   sex                  333 non-null    object
     7   yr                   344 non-null    int64  
     8   above_avg_mass_bool  344 non-null    bool   
    dtypes: bool(1), float64(4), int64(1), object(3)
    memory usage: 22.0+ KB


Look closely - now the `bill_length_mm` column of the data frame doesn't have any null values anymore! That being said, I am going to remove all the null values going forward, using the same command as earlier but with `inplace = True` this time.


```python
penguins.dropna(inplace = True)

penguins.info()
```

    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 333 entries, 0 to 343
    Data columns (total 9 columns):
     #   Column               Non-Null Count  Dtype  
    ---  ------               --------------  -----  
     0   species              333 non-null    object
     1   island               333 non-null    object
     2   bill_length_mm       333 non-null    float64
     3   bill_depth_mm        333 non-null    float64
     4   flipper_length_mm    333 non-null    float64
     5   body_mass_g          333 non-null    float64
     6   sex                  333 non-null    object
     7   yr                   333 non-null    int64  
     8   above_avg_mass_bool  333 non-null    bool   
    dtypes: bool(1), float64(4), int64(1), object(3)
    memory usage: 23.7+ KB


## Manipulating rows of data

We discussed how to rename columns, but selecting specific rows (or observations) in your data frame can also be important. We do this using either the `loc` or `iloc` functions. The `loc` function is used to select rows by name (here, we do not have a row index so this function is not very useful), while `iloc` uses the index number.


```python
print(penguins.iloc[0])
#gets just one value

print(penguins.iloc[0:3])
#gets the values from index 0 to index 2; note that index 3 is not included
```

    species                   Adelie
    island                 Torgersen
    bill_length_mm              39.1
    bill_depth_mm               18.7
    flipper_length_mm            181
    body_mass_g                 3750
    sex                         male
    yr                          2007
    above_avg_mass_bool        False
    Name: 0, dtype: object
      species     island  bill_length_mm  ...     sex    yr  above_avg_mass_bool
    0  Adelie  Torgersen            39.1  ...    male  2007                False
    1  Adelie  Torgersen            39.5  ...  female  2007                False
    2  Adelie  Torgersen            40.3  ...  female  2007                False

    [3 rows x 9 columns]


This is helpful if we know the exact numerical order of our data, but often times we do not. Sometimes, we need to sift through an entire data set just to find a few rows with specific conditions that we are interested in. How do we do this without manually scrolling through the entire data set on Excel? Since this is nearly impossible with large data sets, we are lucky to have a tool for conditional selection in Python. We do this by using the square brackets once again, but this time, we include a boolean condition inside the brackets.


```python
adelies = penguins[penguins["species"] == "Adelie"]

adelies["species"].describe() # The only value is "Adelie" now!
```




    count        146
    unique         1
    top       Adelie
    freq         146
    Name: species, dtype: object



As you can see, this refined data frame only includes the Adelie penguins. This subset behaves just like any other data frame, so we can call all the same functions on it. We can now subset even further to conduct additional analyses.


```python
mean_adelie_bill_size = adelies["bill_length_mm"].mean()

small_billed_adelies = adelies[adelies["bill_length_mm"] < mean_adelie_bill_size]

small_billed_adelies.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>species</th>
      <th>island</th>
      <th>bill_length_mm</th>
      <th>bill_depth_mm</th>
      <th>flipper_length_mm</th>
      <th>body_mass_g</th>
      <th>sex</th>
      <th>yr</th>
      <th>above_avg_mass_bool</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>4</th>
      <td>Adelie</td>
      <td>Torgersen</td>
      <td>36.7</td>
      <td>19.3</td>
      <td>193.0</td>
      <td>3450.0</td>
      <td>female</td>
      <td>2007</td>
      <td>False</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Adelie</td>
      <td>Torgersen</td>
      <td>38.6</td>
      <td>21.2</td>
      <td>191.0</td>
      <td>3800.0</td>
      <td>male</td>
      <td>2007</td>
      <td>False</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Adelie</td>
      <td>Torgersen</td>
      <td>34.6</td>
      <td>21.1</td>
      <td>198.0</td>
      <td>4400.0</td>
      <td>male</td>
      <td>2007</td>
      <td>True</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Adelie</td>
      <td>Torgersen</td>
      <td>36.6</td>
      <td>17.8</td>
      <td>185.0</td>
      <td>3700.0</td>
      <td>female</td>
      <td>2007</td>
      <td>False</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Adelie</td>
      <td>Torgersen</td>
      <td>38.7</td>
      <td>19.0</td>
      <td>195.0</td>
      <td>3450.0</td>
      <td>female</td>
      <td>2007</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
</div>



Notice how here we used the comparison operator `<` for numerical values, which we can do easily in addition to comparing strings. We can also filter for multiple variables at once if we want to using the `&` and `|` operators, which correspond to "and" and "or" respectively. For example, what if we only wanted to analyze data for the female Adelie penguins? We can do so below.


```python
female_adelies = penguins[(penguins["species"] == "Adelie") & (penguins["sex"] == "female")]

female_adelies.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>species</th>
      <th>island</th>
      <th>bill_length_mm</th>
      <th>bill_depth_mm</th>
      <th>flipper_length_mm</th>
      <th>body_mass_g</th>
      <th>sex</th>
      <th>yr</th>
      <th>above_avg_mass_bool</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>Adelie</td>
      <td>Torgersen</td>
      <td>39.5</td>
      <td>17.4</td>
      <td>186.0</td>
      <td>3800.0</td>
      <td>female</td>
      <td>2007</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Adelie</td>
      <td>Torgersen</td>
      <td>40.3</td>
      <td>18.0</td>
      <td>195.0</td>
      <td>3250.0</td>
      <td>female</td>
      <td>2007</td>
      <td>False</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Adelie</td>
      <td>Torgersen</td>
      <td>36.7</td>
      <td>19.3</td>
      <td>193.0</td>
      <td>3450.0</td>
      <td>female</td>
      <td>2007</td>
      <td>False</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Adelie</td>
      <td>Torgersen</td>
      <td>38.9</td>
      <td>17.8</td>
      <td>181.0</td>
      <td>3625.0</td>
      <td>female</td>
      <td>2007</td>
      <td>False</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Adelie</td>
      <td>Torgersen</td>
      <td>41.1</td>
      <td>17.6</td>
      <td>182.0</td>
      <td>3200.0</td>
      <td>female</td>
      <td>2007</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
</div>



A small note - we actually need to use the parentheses around each boolean condition here so the order of operations works. If you get an error in your code when trying to do this, that might be why!

One last helpful function is the `append` function. This function will add the rows of one data frame onto another, assuming the data frames both have the same column dimensions. Let's pretend we didn't get the penguin data all at once, and instead got it in species groups. Maybe we want to bind all the data frames together so the data is all in one place. We can do that below:


```python
chinstraps = penguins[penguins["species"] == "Chinstrap"]
gentoos = penguins[penguins["species"] == "Gentoo"]
#Pretend you didn't see these! :)

penguins_bound = adelies.append(chinstraps.append(gentoos))

penguins_bound.info()
```

    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 333 entries, 0 to 275
    Data columns (total 9 columns):
     #   Column               Non-Null Count  Dtype  
    ---  ------               --------------  -----  
     0   species              333 non-null    object
     1   island               333 non-null    object
     2   bill_length_mm       333 non-null    float64
     3   bill_depth_mm        333 non-null    float64
     4   flipper_length_mm    333 non-null    float64
     5   body_mass_g          333 non-null    float64
     6   sex                  333 non-null    object
     7   yr                   333 non-null    int64  
     8   above_avg_mass_bool  333 non-null    bool   
    dtypes: bool(1), float64(4), int64(1), object(3)
    memory usage: 23.7+ KB


Using the `append` function inside itself is a bit of a slick programming manuever, but it's completely allowed.

`pandas` has a ton of useful functions, and while what we've covered here may seem a bit overwhelming, there is in fact even more that we chose not to get in to. In all honesty, you may not ever need to use some of the things covered here, but in our eyes the most important thing is being familiar with the basics of the library as well as understanding how to learn about the other functions yourselves. That being said, there are some great resources to aid you into your `pandas` introduction; [this website](https://www.learndatasci.com/tutorials/python-pandas-tutorial-complete-introduction-for-beginners/) does a particularly nice job of summarizing all the important points, but a simple Google search of "python pandas tutorial" will return a vast array of helpful results.
