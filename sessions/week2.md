---
layout: single
author_profile: false
title: "Introduction to Python"
classes: wide

sidebar:
  nav: "sessions"

---

**Zoom Link:** [https://ualberta-ca.zoom.us/j/98289884440](https://ualberta-ca.zoom.us/j/98289884440)

## Week 2
This week we will cover the **essential** skills of reading and writing if-statements, looping actions, and functions. Please watch the below videos and follow along in your own Google Collab notebook, writing code and/or taking notes when appropriate. The point of the in-person session will be to practice the skills you'll get an overview of in these videos. As with all these videos, please feel free to pause to digest when you need or watch on a different speed using the YouTube playback speed functionality. These videos will give you an *introduction* to these topics, and during our synchronous session, we'll cement the ideas introduced here with lots of examples and exercises for you to complete.

### If-statements

A near-universal programming concept is to ask your computer to do something (i.e. complete a `statement`), but only `if` a particular condition applies. This simple but powerful concept allows us to control exactly when particular actions occur in a script, and can be used in tandem with the other concepts covered this week to achieve a particular programming task in a robust, and consistent manner.

{% include video id="tLE62t9neH8" provider="youtube" %}

### Looping actions

Asking Python to iterate (or 'loop') over a particular set of functions a number of times is a basic and important functionality that is used commonly. There are a variety of looping actions, and they can involve a series of more complex sub-arguments, but here we cover the broad concept of loops, as well as some of the most common structures, like the *while loop* and the *for loop*.

{% include video id="HUXH9tBh4G0" provider="youtube" %}

### Functions

Functions are the building blocks of well-written programs in Python, and indeed most other OOP languages. A function allows you to perform the same actions over and over again with different inputs, while maintaining a consistent method, and avoiding error propagation that comes with copying and pasting code.

{% include video id="axYX8QMG34A" provider="youtube" %}

------------------------------------------------------------------------------

Please [click here](https://forms.gle/S2KXiVkFZhnHqooQ6) to fill out the post-session feedback form here! We take your feedback into account in real time, so any changes we can make to help you learn better next week we will make!


#**`if` statements**

One of the most valuable aspects of programming is the ability for a program to function differently with a different set of inputs. This is accomplished most effectively using ```if``` statements. Using an ```if``` statement, we can allow a program to return a different function based on a boolean condition. As expressed below, an ```if``` statement relies on a boolean condition and if the condition is true, the block of code inside the ```if``` statement is executed.


```python
x = 3
if (x > 2):
  print('x is greater than 2')
if (x < 2):
  print('x is less than 2')
```

    x is greater than 2


As you can see, the code inside an ```if```statement (denoted by a colon and an indent) only executes if the condition inside the parentheses is true. This allows our mini-program here to tell us something about x, no matter the value that x takes on.

To streamline things even more, we can use the ```else``` clause, which works seamlessly with ```if``` statements. If an else clause is included after an ```if``` statement, the code inside this clause is automatically executed if the condition inside the ```if``` statement is false. This comes in handy quite often, and makes code easier to read and interpret.


```python
x = 1;
if (x > 2):
  print('x is greater than 2');
else:
  print('x is less than or equal to 2');
```

    x is less than or equal to 2


In fact, we can even generate code that can have more than two different outcomes. This is accomplished using the ```elif``` (short for else if) statement. We can use as many ```elif``` statements as we want, as long as they begin with an ```if```. An example can be seen below.




```python
x = 3;

if (x % 2 == 0 and x < 6):
  print('x is even and is less than 6');
elif (x % 2 != 0 and x < 6):
  print('x is odd and is less than 6');
elif (x % 2 == 0):
  print('x is even and is greater than or equal to 6');
else:
  print('x is odd and is greater than or equal to 6');
```

    x is odd and is less than 6


Here, we take advantage of a lot of shortcuts available in Python. We use the **modulus operator**, which returns the integer remainder when one number is divided by another (e.g., ```10 % 3 = 1``` because ```10 / 3 = 3``` with a remainder of ```1```), to identify whether a number is odd or even. If any number modulo 2 is 0, that means the number is even, hence the statement ```x % 2 == 0```. We then use the ```and``` statement to check whether two booleans are true, making a new boolean representing the intersection of the first two. Notice that in the second ```elif``` statement, we do not check whether ```x``` is less than 6; this is because we have already checked it in the first two statements. If the code has made it to line 7, this means that the conditions on lines 3 and 5 are false, because **within a set of combined ```if```, ```elif```, and/or ```else``` statements, only one of the code blocks will execute for any given set of conditions.** If the condition in line 3 is true, the rest of the clause will not execute - only the code on line 4. This is also the reason why we only need to use an ```else``` statement on line 9; if the first three conditions are all false, then we know that ```x``` is odd and is greater than or equal to 6. Note that cascading ```if/elif``` statements do not need to end with an ```else```, but the ```else``` at the end guarantees that at least some code will be executed no matter the conditions.

#**Loops**

Arguably the most valuable asset that computer programming gives to scientists is the ability to iteratively evaluate a chunk of code over and over again without the need for the user to explicitly repeat this chunk in their script. When working with large data sets, this iterative style of programming is necessary, and it is accomplished using **loops**. A loop is a chunk of code that is evaluated many times, based on a condition that is specified by the user.

###**`while` Loops**

The most simple form of loop is the ```while``` loop. A ```while``` loop is similar to an ```if``` statement in many ways, with the main difference being that the code inside the statement is evaluated **as long as** the condition is true.


```python
x = 0;

while (x < 10):
  print(x);
  x = x + 1;
```

    0
    1
    2
    3
    4
    5
    6
    7
    8
    9


Notice that we begin by defining a variable `x` and instantiating it with the value 0. When the code gets to line 3, it first checks if `x` is less than 10. Because 0 is less than 10, it executes the indented chunk of code, printing `x` (0) and reassigning `x` to its old value plus 1 (meaning `x` is now equal to 1). Each time the code inside the loop runs, `x` increases by 1, preventing this loop from becoming infinite (if we didn't have the statement on line 5, we would be printing out 0 forever!), since eventually `x` will become 10 and the condition on line 3 will be false. Keep in mind that the loop will end the first time the `while` condition is false.

###**`for` Loops**

A `while` loop can be very useful at times, but they are often more difficult to write because of the ambiguity of the condition. It is rather easy to mistakenly write an infinite loop when writing a while loop. The other commonly used loop in Python, the `for` loop, provides a remedy for this problem. Here, we explicitly state the set of values for which we would like to iterate on, saving us a couple lines of code that are necessary in a `while` loop. Pay attention to the syntax below; although it looks a bit different from the `while` loop above, it does the exact same thing!


```python
for x in [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]:
  print(x)
```

    0
    1
    2
    3
    4
    5
    6
    7
    8
    9


Many things are different here, but overall the code looks much more elegant - after all, it's only two lines! The first line makes good sense; it is telling the indented code below to execute for each value of x in the array `[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]`. Notice that instead of manually declaring a variable `x` as we did in the `while` loop, we can save a line of code by having the computer declare this variable automatically. Note also that this array can be anything - it can print out numbers, strings, or booleans! That being said, there is one way that this loop can be improved, and this is done using the `range()` function. This function is used primarily in loop conditions, because it automatically generates an array from 0 to any number you would like. In other words, the value returned from `range(10)` is the same as the array we explicitly stated above.


```python
for x in range(10):
  print(x)
```

    0
    1
    2
    3
    4
    5
    6
    7
    8
    9


Very nice, isn't it? With loops we can greatly minimize the amount of human overhead that is required when it comes to data processing and other time-intensive tasks; instead of doing it all ourselves, why not let the code do it for us automatically? This becomes even more apparent when the concept of **loop nesting** is introduced. We nest one loop inside another by writing a loop inside the indented block of another loop. This may seem confusing, but the example below is still rather streamlined:


```python
for x in ['c', 'd']:
  for y in ['a', 'b']:
    print(x + y)
```

    ca
    cb
    da
    db


Notice the order in which the loops were executed. Each iteration over `x` results in the entire `y` loop being executed, which is why `ca` and `cb` are printed first. Nested loops can become much more complicated, as you can theoretically nest as many loops as you want in Python. However, too many layers of loop nesting will drastically slow down a program as the number of individual executions increases very quickly.

#**Functions**

Functions are essentially a group of statements put together in a specific way that perform a specific task. Functions are one of the foundational aspects of any programming language, and good programming scripts will always make use of functions to perform tasks. They are especially useful for keeping code clean and only writing things once that may need to be replicated many times.

A good principle of *Clean Code* is that if you catch yourself copying and pasting multiple lines of code to perform the same operation with different input, it's likely that you should consider writing a for loop or a function to perform the task.

Writing good functions is premised on the **essential** concept that functions can be formatted the same way every single time, and that their construction is consistent across programs, and that they are well documented.

The basic structure of a function is as follows:


```python
def function_name(parameters) -> return_type:
	"""docstring"""
	statement(s)
 return
```

There are five main components of a function, which we'll go through now.

###**Function Name**

Function names should ALWAYS be clear and structured in the same way. Words should be separated using and underscore (_), and the name should be descriptive of what the function does. This is important as the function "call" (aka, where the function is actually used to perform an operation, can be done much later in the code, and as someone reading the code, it's nice to be able to guess roughly what the function is doing just by the name.

For example, a function that checks to see if a number is a prime number or not, should not be called `pr_nm()` as that's effectively illegible. Instead, an acceptable alternative could be `prime_number()`. Always err on the side of a slightly longer function name that is useful than a shorter name that is unhelpful.


```python
def prime_number(parameters) -> type:
	"""docstring"""
	statement(s)
 return
```

###**Parameters**

Inside the brackets of the function name, you'll see the `parameters` argument, which, while technically optional in python, is good to include. We could teach a whole workshop series on writing good functions and spend an entire day or two on just parameters, but in brief, this space is used to define what the function will take in to perform it's task. That is, if a function is checking whether a number is prime, it will need to take in a number, let's call it `n`, and ideally as an integer. This can be specified in the parameters ection, and would be done as follows:


```python
def prime_number(n: int) -> type:
	"""docstring"""
	statement(s)
 return
```

Note here that the `n` is followed by a colon and then the type. This tells the reader that the function `prime_number()` takes in an object of type `int` to perform it's calculation, and thus gives a warning to both other users as well as future you, that the function may not work well or at all with other types.

###**Docstrings**

Docstrings are an **incredibly** important concept, and one that is often skipped by those writing functions in favour of some time saved. This is to their detriment. Using docstrings is a specific use case of the broader concept of documenting your code. Documenting code is done again both for others and future you, to show what each bit of code is supposed to be doing. In biology, we often skip over this part of programming, but it is essential, and cannot be overstated in important. An article on the entire topic, with a subsection on docstrings is here, and is recommended reading: https://realpython.com/documenting-python-code/#documenting-your-python-code-base-using-docstrings

Much can also be said about docstrings, but to be brief, there are two essential functions:


1.   The docstring for a function must describe the functions behavior and document its arguments and return values.

2.   It should also list all the exceptions that can be raised and other optional arguments.

Good docstrings tell readers what the function should do, what it takes, what it returns, and when it will not work properly.




```python
def prime_number(n: int) -> type:
	"""Return whether n is prime or not in the form of a boolean.
  Parameters:
              n (int): A whole integer greater than zero

  Returns:
              True/False (bool): A boolean

  >>> n = 4
  >>> prime_number(n)
  False
  >>> n = 7
  >>> prime_number(n)
  True
  """
	statement(s)
 return
```

We'll discuss the return statement below, but note that both the parameters and what the function returns is defined here. A good docstring should always have the following:


1.   A sentence or two describing the fuction's use
2.   A description of the parameters and the returns
3.   One or more examples of how the function should work, and if the function is complicated, sometimes it's useful to include important 'corner cases' or examples where the function may work differently than expected (i.e. if that value is zero)



###**Statements**

This is the 'meat' of the function definition, where we actually tell Python what to do with the value `n` that we give it. While there are almost *always* multiple ways to achieve the same result in how we write our statements in Python, it's good practice to try and keep them as concise as possible. Here is how we could write the statements for our `prime_number()` function.


```python
def prime_number(n: int) -> type:
  """Return whether n is prime or not in the form of a boolean.
  Parameters:
              n (int): A whole integer greater than zero

  Returns:
              True/False (bool): A boolean

  >>> n = 4
  >>> prime_number(n)
  False
  >>> n = 7
  >>> prime_number(n)
  True
  """

  div = 2
  while (div <= n / 2):
    if (n % div == 0):
      return False
    div = div + 1
  return True

```

Here we used a while loop, which we covered previously, and performed our calculation by iteratively dividing by other numbers < n/2, (recall that the simple definition of a prime number is is a natural number greater than 1 that is not a product of two smaller natural numbers), thus checking if the statement holds.

Spend some time with this function and walk yourself through it until you understand each line.

In addition, we've included the `return` statements, which we'll cover next.

***NOTE:*** Those of you who are mathematically inclined may already know that zero is not a prime number, nor a composite number (a natural number that is the product of two smaller natural numbers). In our function, however, if we passed `n=0` to the function, note it would return `True` indicating that zero is in fact prime. If we were writing this function to be used by others, we would use the concept of exceptions (the interested student may learn more here: https://docs.python.org/3/tutorial/errors.html) to write a case to the function such that it returned either `False` (which is technically true since the function asks only whether or not a number is prime, not if the function is prime or composite), or it returned an error. However, we will not cover exceptions here. Note that to solve this problem, we were explicit in our docstring that the value `n` must be a whole integer greater than zero. Thus, we made it clear in the function definition that zero is not an acceptable value to pass to the function `prime_number()`. This is not a robust solution, but it is valid for our use here.



###**Return Statements**

Return statements in Python functions are optional. A function that does not return anything is valid, but less commonly used, particularly in our case.

Note that within a function, one has the option to `return` an object, or `print` an object. These seem the same on the surface but are fundamentally different.

Using `print` simply shows us what is going on inside the computer. The computer cannot make use of that printing. That is, as far as the computer is concerned, the print is not stored in any way. `return` is how a function gives back a value that can be saved as a variable or used by the computer. This value is often unseen by us as users, but it can be used by the computer in further functions.

`return` is the main way that a function returns a value. All functions will `return` a value, and if there is no `return` statement, it will return `None`. This could be specified in the The value that is returned by a function can then be further used as an argument passed to another function, stored as a variable, or just printed for the benefit of the human user.

Note that the `type` of the expected return value, in addition to being in the docstring, should also be in the definition line.

Therefore, the final function, would look like this:


```python
def prime_number(n: int) -> bool:
  """Return whether n is prime or not in the form of a boolean.
  Parameters:
              n (int): A whole integer greater than zero

  Returns:
              True/False (bool): A boolean

  >>> n = 4
  >>> prime_number(n)
  False
  >>> n = 7
  >>> prime_number(n)
  True
  """

  div = 2
  while (div <= n / 2):
    if (n % div == 0):
      return False
    div = div + 1
  return True
```

###**Calling a Function**

So now that we've written our function, we want to actually call it! Either to test it or to use it in our code. To do so, we simply use the function name, and pass in the value we want to use. There are a few ways to do this, and you'll see how they differ:


```python
prime_number(3)
```




    True




```python
n = 4
prime_number(n)
```




    False




```python
prime_number(n = 8)
```




    False




```python
n = 7
is_prime = prime_number(n)
```


```python
is_prime
```




    True
