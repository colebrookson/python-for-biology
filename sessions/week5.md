---
layout: single
author_profile: false
title: "Introduction to Python"
classes: wide

sidebar:
  nav: "sessions"

---

## Week 5

**ZOOM LINK:** [https://ualberta-ca.zoom.us/j/94223003604](https://ualberta-ca.zoom.us/j/94223003604)

Well, you made it! This is the last week! So far you've learned how to use Python in Google Colab, we've talked about data types and structures, loops, function, programming best practices, and how to work with data in Python. Now, it's time to put all that knowledge together and challenge yourself. Below is a problem set that we encourage you to work through independently. As with all programming, unfortunately the only way to truly begin to master a language is by practicing. We encourage you to take the time to try and answer each question. There is nothing here that we haven't covered in class, but the data that you were provided via email are unique. Refer back to previous weeks to refresh your knowledge if need be.

The last in person session, Thurs. Nov. 5th, will be a drop-in help session where both Peter and Cole will be in the ZOOM during the usual time slot to assist you if you have problems. By Sunday, Nov. 08, there will be a series of videos posted here that will walk you through each question in terms of how to do it. We strongly encourage you to try the exercises yourself before you watch the videos. If you get stuck on a particular problem, feel free to watch the video for that problem, then continue trying the problems yourself.

If you have questions, please do not hesitate to [contact us](/Contact/).

## Problem Set:

A quick note before we jump in: **THE INTERNET IS YOUR FRIEND!!** You will likely find there are small pieces of code you need to write that we have not covered explicitly. That is okay, and we encourage you to take advantage of the wide variety of internet resources that exist (i.e. [Stack Overflow](https://stackoverflow.com)) to look up solutions to your problems. It is almost never that you sit down as a programmer and just know off the top of your head to how write every single piece of code that goes into a larger program. You will need to look up pieces here and there, so getting practice doing that here is important. 

As our final task for this workshop, we are going to call on the principles that we have discussed in the first four sessions. Here we provide you with a large fake raw data set about flu cases, one that is too large to edit manually. The data were (hypothetically) collected at different times, so you will notice that it comes in two different files. **Please note these data are fake and are purely for the purposes of you to practice on**. To ready the data for the analysis, begin by doing the following:

**Question 1** Download and read in both CSV files to your Colab Notebook. Feel free to take a peek at the data using some of the functions we have discussed.

**Question 2** Bind the data frames together, adding a new column that delineates observations from the first data frame from observations from the second.

**Question 3** Clean up the data by removing any rows that contain NA values.

To cement the best practice use of functions, we’ll be writing two functions to help us perform some summary statistics on our data. To do this, we’ll note here that a ‘helper’ function is the name of a function that is usually embedded inside another, larger and more general function, for the purposes of streamlining the function writing process, and breaking the entire operation into manageable chunks.

**Question 4** Write a helper function that takes in a level (type string) of the 'Location' column and returns the mean of ANY numeric column (type float) subset to only that level. **NOTE:** this helper function has to be able to work no matter the numeric column passed

**Question 5** Write a larger function that uses the helper function and produces 3 lists:

  **a)** A list with all the unique values of the 'location' column *hint:* you can do this with: `df.column_name.unique()`

  **b)** Two lists with all the mean values of the numeric columns 'patient_age' and 'severity' at each level of the categorical column

  Once the three lists are created, *inside the function*, using the code provided, coerce these lists into a Pandas dataframe. Have the function as a whole return the dataframe.

  `dataframe = pd.Dataframe(list(zip(list_1, list_2, list_3)),
                            columns = ['column_name_1', 'column_name_2', 'column_name_3'])`

  **NOTE**: you will need to change the column names and list names to represent what you called those objects in your function.

**Question 6** Once the functions are written, write a minimum of three doctests for the helper function. **NOTE**: reminder that for each test, the function will need some values to 'test', so you will need to include the lines of code providing those values in the actual test. Refer to the provided content summary on testing if you need a refresher on this.

When writing your functions, make sure to adhere to coding best practices, and don't forget to write docstrings and comments within all your functions. Additionally, pay attention to the efficiency of your code. We are working with semi-large data, and this code should not take overly long to run.
