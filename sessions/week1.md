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

## Week 1

**Zoom Link:** [https://ualberta-ca.zoom.us/j/93864717351](https://ualberta-ca.zoom.us/j/93864717351)


Welcome to the first week of content! Topics of this week will be an introduction to this series, an overview of Object-Oriented Programming (OOP) and some of the basic programming skills that will form the basis of what we'll learn from here on out.

{% include video id="dZAUalQOjIk" provider="youtube" %}

Please watch the below videos **before** coming to the synchronous lecture - they are relatively short. Follow along when asked, and write down any questions or difficulties you have that we can discuss in lecture.

In future weeks, we'll have a few videos for you to watch that have programming concepts or ideas presented, that we will then practice in our synchronous session. This week, we are just getting you set up to be ready to code, and we'll do everything else together in our session! Looking forward to seeing you all soon!

### Introduction to Google Collab

Before we get started doing any coding, we'll need to get familiar with the actual tool we'll use to write and run our Python programs.

Some of you who have programmed before may recognize the terms IDE (Integrated Development Environment) or text editor. These are tools often used by programmers to write and run their code, and typically they are applications installed on one's local computer. While we encourage you to research and set up your own IDE if you plan on programming much past this workshop series (some useful links in the [Resources](/python-for-biology/resources/) section), we ask that you all use Google Collab for this series, just so we're all on the same page technology-wise. This video will walk you through the very basics of using [Google Collab](https://colab.research.google.com/notebooks/intro.ipynb).

{% include video id="AG0gMuy_i-M" provider="youtube" %}


-----------------------------
Please [click here](https://forms.gle/4RCiyEQWxAP9jVDz7) to fill out the post-session feedback form here! We take your feedback into account in real time, so any changes we can make to help you learn better next week we will make!




# ***Python Basics***
**Authors:** Cole Brookson & Peter Thompson

Python is a programming language commonly used by mathematicians, biologists, and data scientists. It has excellent capabilities for data manipulation and mathematical calculation. Python is also an example of an object-oriented programming language. Object-oriented programming (or OOP for short) is a style of computer programming that relies heavily on the classification of every variable as an “object”. In Python, an object can be many things, from a number to a matrix containing thousands of entries. The rigorous classification of objects in object-oriented languages such as Python makes coding much more streamlined and easy to understand. At the center of any programming language (including OOP languages) are variables. A variable is a unique instance of an object, containing unique data and being assigned a unique name. When we assign a variable to a name, we are simultaneously generating an address in our computer’s memory where the data for this variable will be stored. We will discuss other hallmarks of OOP, such as classes, further in today’s and future sessions.

Here, we are using Python through Google Colab, which allows users to seamlessly incorporate Python code and text into one notebook. This is accomplished through Jupyter Notebooks, a widely used method for writing Python scripts that are easy to read and interpret. Writing Python through Google Colab alleviates some of the difficulties that may arise from installing and running Python on your own computer, although this can be done through clients such as Anaconda.

# **Types in Python**

Like any programming language, in order to execute the proper operations on different variables and objects, python assigns every single object a ‘type’. That is, a type typically defines the set of possible values and a set of operations for an object. In compiled languages, often every single object or variable needs to be declared (such as in C/C++), and types are explicitly assigned by the user at the time of variable declaration. However, in an interpreted language like Python, often the type is defined implicitly by the machine. However, that makes it important to understand, as the user, what types you’re working with and how you can ask them to behave in Python. There are a series of basic types that have concepts you’ll likely recognize:


*   Integers
*   Floating-point numbers
*   Complex numbers
*   Strings
*   Boolean Types







### **Integers**

An integer (whole number) is the simplest type in python, and basic mathematical operations can be performed on it. This leads us to our first exercise with Python, where we essentially use it as an overly complex calculator! *Python as a calculator:*


```python
#Integers
2 + 2
```




    4



And note here that when we don't have to wrap our calculation in anything to get it to run. This is because we're using the interactive platform Jupyter as opposed to a traditional Python script in a text editor, where the equivalent would be done with:


```python
print(2+2)
```

    4


More generally, if we ever need to check if certain variables or objects are of a particular type we can use the handy `type()` built-in function:


```python
type(10)
```




    int




```python
type(10000000000000000000000000)
```




    int



### **Floating-Point Numbers**

Floating-point or `float` numbers in Python are decimal values.




```python
0.001
```




    0.001




```python
0.3 + 0.33
```




    0.63




```python
type(0.8765)
```




    float



However, keep in mind that as with manual addition of floating point numbers, there is often a rounding process that needs to take place, which results in a loss of accuracy as far as the computer is concerned.

It is not essential to understand the intricacies of `floats` for our purposes in Python, but if you are interested, here is a link that will tell you more about the dangers of `floats` and how to avoid common pitfalls:
https://docs.python.org/3.7/tutorial/floatingpoint.html


```python
#Floats can also be expressed in Scientific notation
2e2
```




    200.0




```python
type(2e2)
```




    float



### **Complex Numbers**

We won't work much with complex numbers in this workshop series, but it's important to know they exist. For those of you who recall high school math classes, complex numbers are specified as `real`+`imaginary` `j`:


```python
4+6j
```




    (4+6j)




```python
type(9+10j)
```




    complex



### **Strings**

Strings, or `str` for short, are one of the most essential types in Python, as they allow us to pull together a series of `characters` (`characters` would be each of `a`, `b`, `2`, all specified as characters) into a concatenated group, called a string.


```python
'This is a string'
```




    'This is a string'




```python
print('This is also a string')
```

    This is also a string



```python
type('Also this thing is a string')
```




    str



***A Very Important Note***: anything can be a string!! This is both very useful, and dangerous. See this following example:


```python
'a string' + 'another string'
```




    'a stringanother string'




```python
#let's make the above example prettier:
'a string' + ' another string'
```




    'a string another string'




```python
#Essentailly,
'a string' + ' another string' + ' means' + ' you can make a sentence'
```




    'a string another string means you can make a sentence'




```python
#adding strings and numeric values in the following manner doesn't work
'a string' + 2
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-25-7cb42658fd34> in <module>()
          1 #adding strings and numeric values in the following manner doesn't work
    ----> 2 'a string' + 2


    TypeError: must be str, not int


This above message is an error. You will get very familiar with seeing errors. That's okay, because they're helpful and they're there to a) prevent you from doing something that won't work, and b) help you fix the problem.

Looking carefully at what the error says, we see the arrow points us to the location in the code cell where the error happens (aka, where Python stops running because it doesn't know what to do), and then below we see the message `TypeError: must be str, not int`, which we now know means that to add two strings, both must be strings.


```python
#but can be achieved this way
'a string' + '2'
```




    'a string2'



There are TONS of things that can be done with strings in Python, few if any of which we will cover here. Strings are incredibly useful for those working with text data (i.e. those scraping information from actual paper, or from the internet), but we won't be doing much of that here. However, know that there are a whole series of methods and tricks that are applied to strings, and working them in Python is highly customizable.

If you are curious:
https://www.w3schools.com/python/python_strings.asp



**Boolean Type**

In Python, objects of Boolean type, or `bool` only have two values - `True` and `False`. A value that is `True` in Boolean context is sometimes said to be “truthy,” and one that is `False` in Boolean context is said to be “falsy.” (You may also see “falsy” spelled “falsey.”).


```python
type(True)
```




    bool




```python
type(False)
```




    bool



You'll most commonly see Boolenas used to evaluate statements in a framework of decision making such that the computer being able to make decisions about equivalencies, which determine outcomes.

# **Operators in Python**

The term 'operator' is essentially a fancy term for the method that programmers designed to perform arithmetic or logical computation on a series of objects. There are a large number of operators which we will not cover. Many of the arithmetic operators are exactly what you would expect from normal (or near-normal) mathematical notation.

There are lots of comparisons that one can do in Python, but there are a few basic ones that are worth noting here. They are the common mathematical operators `"greater than" >`, `"less than" <`, `"equal to" ==`, and `"not equal to" !=`. There are the combinations of these four basic comparisons as well. `>=`, `<=`. Typically making a comparison results in a Boolean return type.

One thing to be conscious of is that **comparisons act differently on objects of different types** and it is important to take that into account when writing code.


```python
2 < 3
```




    True




```python
2 > 3
```




    False




```python
2 == 3
```




    False




```python
2 != 3
```




    True



Another thing to note is that there are logical operators that also return Boolean types and are used in computational decision makeing. The logical operators are: `and`, `or`, and `not`. Their usage will become more clear later in these sessions.

There are many more operators that you  will eventually need to use in your programming journey. Here is a more comprehensive list:
[https://www.programiz.com/python-programming/operators](https://www.programiz.com/python-programming/operators)


# **Assignment Statements**

Assignment statements are exactly what they sound like - they assign a value to a named variable. = is Python’s assignment operator, which you'll notice is similar but *different* from the mathematical operator.


```python
#this is an assignment
x = 2
```

You'll notice that there is no output from the above cell, but that's just because Python has assigned the value and stored it away for our future use without bothering to tell us about it. We can call the value (termed 'printing') of x to see what the value is.


```python
print(x)
```

    2


Note that assignments can be made easily incorporating other named objects, and even themselves. The following operation for example is very common:


```python
x = x + 1
```

Guess what the print statement of `x` will be now?


```python
print(x)
```

    3


# **Data structures**

While assigning a single integer or string to a variable may be useful in some cases, it is often necessary to store data in large collections. Python has a strong functionality for this problem, with many options for efficiently storing large amounts of data. More generally, these functionalities are known as data structures. A *data structure* is any format or method in which multiple data values are stored such that they can be efficiently accessed or modified again. There are many data structures available to Python users, with the most simple data structure in Python being the *array*, a simple ordered list of objects. Arrays are easy to make and modify, especially when they are being used with basic types such as integers.


```python
array = [3, 2, 1]
print(array)

#Notice that the brackets appear when the array is printed to signify that it is an array
```

    [3, 2, 1]


Arrays can be used to store objects of any type (including strings, as seen below). They can even handle multiple types at once, a feature that is quite convenient and unavailable in many other OOP languages.


```python
stringArray = ["Hello", "there"]
print(stringArray)

# Trying to generate an array with an integer and a string

multiTypeArray = [2, "two"]
print(multiTypeArray)
```

    ['Hello', 'there']
    [2, 'two']


In fact, we can even generate arrays that store other arrays. We call these structures two-dimensional arrays. When each sub-array contains the same number of elements, we call this a *matrix*. Storing data as a matrix often makes it easier to access the values inside the data structure. We can make arrays with three or more dimensions, but this takes us out of the scope of this workshop.

Declaring a matrix works just how you might expect it, by using the square brackets and separating each element of the array with a comma. The only difference here is that the elements of this array are arrays themselves!


```python
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
print(matrix)
```

    [[1, 2, 3], [4, 5, 6], [7, 8, 9]]


# **Indexing**

To be able to take advantage of many data structures, including arrays, one must be familiar with *indexing*. Arrays are easy to manipulate because their values are stored linearly, meaning that there is a concrete order to the items in an array. In Python, we use square brackets to access a certain value of an array. Because Python uses *0-based indexing*, the first item of an array is actually item 0 in memory. While this is a tad confusing, it is cleaner and more efficient from a memory perspective.


```python
array = [3, 2, 1]
print(array)

#view only the first element of the array

print(array[0]) # remember, the 0 index represents the first value of the array

#re-assign the second value of the array to 5

array[1] = 5
print(array)
```

    [3, 2, 1]
    3
    [3, 5, 1]


We can access the length of an array using the built-in `len()` function. This easy-to-use function returns the number of elements in any array. Notice that we can now access the last value of any array easily, as seen below.



```python
array = [6, 5, 4, 3, 2, 1]
print(len(array))

print(array[len(array) - 1]) # because we are using 0-based indexing, we have to subtract 1 from the length to get the last element
```

    6
    1


With matrices or other multidimensional arrays, we now have to index on more than one level. This is fairly intuitive in Python, because a matrix is just an array of arrays. In other words, getting the first element of an array gives us an array that we can once again index to get a single integer. This is detailed below.


```python
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9], [10, 11, 12]]

print(matrix[0]) # this is the first row of the matrix

print(matrix[0][0]) # matrix[0] is an array, so we get values from it the same way we normally would

matrix[1][2] = 15 # reassigning just one value of the matrix
matrix[2] = [10, 10, 10] # reassigning an entire row by filling it with a new array

print(matrix)
```

    [1, 2, 3]
    1
    [[1, 2, 3], [4, 5, 15], [10, 10, 10], [10, 11, 12]]


Notice also that we can still use `len()` for matrices. Here, it can be used to tell us about the length of any dimension of the array. If `M` is a matrix, `len(M)` will not tell us the number of total elements in the matrix, because `M` is technically an array of arrays. In other words, `len(M)` tells us the number of arrays inside `M`; this can be thought of as the number of rows in the matrix. Once again, any element of `M` is an array that we can access, so we can identify the number of elements in any row of `M` using `len(M[0])`. This can be thought of as the number of columns in a matrix. Keep in mind that if the elements of `M` have different lengths, then `len()` will return different numbers for different elements of M.


```python
print(len(matrix)) # number of rows

print(len(matrix[0])) # number of columns

print(len(matrix[1])) # here these last two lines are the same; this is not always the case!
```

    4
    3
    3
