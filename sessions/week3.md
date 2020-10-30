---
layout: single
author_profile: false
title: "Introduction to Python"
classes: wide

sidebar:
  nav: "sessions"

---

**Zoom Link:** [https://ualberta-ca.zoom.us/j/95912630136](https://ualberta-ca.zoom.us/j/95912630136)

## Week 3
This week will discuss further some important programming skills often missing from the toolkits of biologists. Now that we've talked about the fundamentals of programming (if statements, loops, functions), we can move on to a discussion of how to do those things, and indeed all other programming tasks, **better**. Please keep in mind that each of these sections could comprise entire workshop series and full undergraduate/graduate courses in computer science are taught on these topics, particularly the later three. We are giving you the tiniest taste of each of these topics, and we hope that this helps you learn more on your own to make your analysis more robust.

### Pseudocoding

Pseudocode is essentially a plain language description of a computer program that leaves out the unnecessary details of syntax etc., and simply acts to communicate the basic premise of the program, while outlining how that task will be accomplished. Writing pseudocode is actually incredibly important, and while it's not a staple in biological programming, incorporating it would save many a biologist valuable hours spent troubleshooting glitchy code.

{% include video id="lo-Sc8zgteU" provider="youtube" %}

### Syntax  

We define syntax as the set of rules that defines how statements inside a script or program need to be structured in order for the code to execute properly. While syntax errors are very important, the fact that the code is interrupted by their presence makes them easy to spot and deal with. Even if your code runs properly, there may still be issues related to some of the "unwritten" syntax rules that govern Python and other programming languages. While these rules technically need not be followed for code to execute properly, they often make things easier for both the programmer and other users of the code.

{% include video id="mSvy_KN34lQ" provider="youtube" %}

### Efficiency

At the high levels of computer science, whether or not a script works is not as important as how quickly it works. This is because the most pressing problems in computer science and increasingly in biology often involve very large data sets or very computationally intensive algorithms. In other words, if an algorithm is too slow, it doesn't matter if it's correct - it simply can't be used. Our situation isn't quite as drastic, but we still need to think carefully about how the things we're asking our program to do will work alongside the computer's hardware. Increasing the efficiency of your code will only be beneficial in the long run.

{% include video id="3bQeNlrEfrY" provider="youtube" %}

### Code Testing  

It's not enough to *think* our code works, we have to *know* it works. Scientist's papers and even careers have been sunk by careless coding errors and honest mistakes. Mistakes in code don't always mean the code breaks, often the code will run just fine, but will spit out the wrong answer. When we as scientists then report those false results, this is fraud, and a very serious form of academic misconduct. It is absolutely our responsibility as scientists to be sure the results we report are accurate. Testing our code can help us avoid some of these pitfalls.

{% include video id="JWNyfsmzoRw" provider="youtube" %}


# Content Summary

# Pseudocode

This is an extremely important part of programming that is often neglected by biologists in two very important ways. I'm going to discuss the concept of pseudocoding in both of these contexts.

## Analysis Planning for Domain Scientists

The reason we're all in this virtual room right now is that we are domain scientists. That is, we have our primary research interests outside the realm of computer science, and we simply apply tools and software from computer science to solve our 'domain' problems.

Because first and foremost our goal is to solve a biological problem, we need to keep this in mind when beginning our analysis. Far too often in biology, we start an analysis by coding. We jump right in and figure out how we're going to do it as we go. This might be tempting and we've all done it, but it is actually bad practice. More often than not, this leads to an ineffcient and error-prone process of developing an analysis. There are also a series of problems that can arise when you start analyzing your data prior to coming up with a plan for how to do so (i.e. p-hacking). Far more appropriate is to figure out how we're going to solve our problem, and then determine how to make our computer do as we want.

Often when domain scientists jump into their analysis without adequate planning they run into the following problems:
1. An unorganized file structure with file paths and code files in random locations and with poor names.
2. Poorly written code that is ineffcient and is full of errors
3. Non-reproducible methods
And other more specific issues. So, an optimal solution to this problem is analysis planning, which is more broad than just pseudocoding, but we'll focus on that component here.

As a domain scientist, you should typically follow the following **pseudocode pipeline**:
1. Solve and plan your biological problem first.
  *   Determine what you need your computer program to tell you about the biology of whatever it is you're working on.
    *  *Warning*, this might actually be very difficult  
  *   Ask yourself the questions:
    *  How will I translate my biological problem into a discrete piece of analysis that I can program in my computer?
    *  How will I know if the computer is answering the problem *correctly*? (more on this later)
    *  Will this be sufficient to answer the overall question my analysis is trying to get at? If not, what other programs may I need to write?
2. Write pseudocode to display your domain (biological) problem in plain english
3. Implement the pseudocode in whatever language you want

## Pseudocoding

So, you've realized you shouldn't be starting an analysis by sitting down at your computer, so you've made a plan, split up your analysis into discrete pieces. Now what? For each piece, you're going to have to figure out how you want your computer to give you the answer.

This is a common process in computer science, and is meant to achieve two things. In our case, it is first and foremost to help us write efficient code that works the first time, rather than continually testing our broken code that we just wrote off the top of our head. Secondly, and more importantly in the software world, it's to allow anyone else to understand what your program is doing without necessarily knowing the specifics of the given languages/methods.

When we're beginning to write a program, **we don't really care about the specific *language* or *syntax*, we care about the logic of the program.**

Let's look at an example using a piece of Python code we've already written. Recall the function from last class where we wanted to know if a gene passed to a function was famous (one of the top 10 most studied genes) or not.



```python
def gene_famous(gene: str) -> str:
  """Return whether or not a given 'gene' is in the list of most studied genes.
  Parameters:
              gene (str): a character string of a gene

  Returns:
              (str): one of two string options

              'Yes, this gene is famous!'
              OR
              'No one cares about this gene.'  

  >>> gene = 'KBM7'
  >>> gene_famous(gene)
  'No one cares about this gene.'
  >>> gene = 'APOE'
  >>> gene_famous(gene)
  'Yes, this gene is famous!'
  """
  top_ten_genes = ['TP53', 'TNF', 'EGFR', 'VEGFA', 'APOE',
                 'IL6', 'TGFBI', 'MTHFR', 'ESR1', 'AKT1']
  if gene in top_ten_genes:
    return 'Yes, this gene is famous!'
  else:
    return 'No one cares about this gene.'
```

So this is well documented, but when we wrote this, we just started with the function, which is not actually how we should be going about this. **Instead, we should have written pseudocode first.**

How would we do that? Well, we want to keep the general structure of how code is written in this language (Python), and we can still use general programming terms like 'loop', 'if-statement' etc.

It will likely be a somewhat iterative process, that is, we won't start at the beginning, write to the end and call it a day. We'll add skeleton pieces, and then flesh it out as need be. Let's start by putting the most basic things we need:

```
define function(INPUT) -> OUTPUT TYPE:
  docstring
  examples
  define list of top ten genes as TYPE
  if INPUT in list of top ten genes:
    return POSITIVE OUTPUT
  else:
    return NEGATIVE OUTPUT
```

So for this example, since it's a relatively simple function, we find that doing the very basic pseudocode has pretty much written most of our function for us. What do we still need to add? Well, because this is just how I like to type my pseudocode, I've put capitals on things I want to expand on once I think about them more. So let's thing critically about what the input and output may need to be.

```
define function(input object: string) -> string:
  docstring
  examples
  define list of top ten genes as list of strings
  if input object in list of top ten genes:
    return positive output string
  else:
    return negative output string
```


Now like we said before, this is an extremely basic function, and thus an extremely basic docstring. In fact, we've managed to write almost all the function. Now we would just go through and make sure our syntax is correct for the language we're using (Python) and come up with our examples and docstrings.

Most importantly, we've gone over the basics of writing pseudocode.

### NOTE:

There is no **one** way to write psuedocode. Professional software engineers will have their own way of doing it or companies/organizations will have their own best practice preferences for writing it, but there is no perfect way. Write your pseudocode with the following things in mind:

1. Who will read this in the future and need to interpret my code?
2. What will their approximate level of experience be?

If you keep these two question in mind, that will help you write effective psuedocode that does the job you need it to.


Often times, it is easy to assume that as long as a program works, no matter how it looks or how easy it is to understand, it does not need to be modified. Unfortunately, for a variety of reasons, this is not traditionally true. Many of these small tips and tricks for making code easy to understand and read lie under the umbrella of **syntax**. We define syntax as the set of rules that defines how statements inside a script or program need to be structured in order for the code to execute properly. Some of the issues we will discuss can be thought of more as **best practices** while other issues can lead to fatal errors in your code.

# Syntax

You may notice that sometimes, when your code isn't working, the message "`Syntax error`" may appear. As the message would suggest, this happens when your code does not correctly follow the syntax of the language you are using. A simple example in Python can be seen below:


```python
for (x in range(10)):
  print(x)
```


      File "<ipython-input-1-791ac13c30de>", line 1
        for (x in range(10)):
                            ^
    SyntaxError: invalid syntax



When trying to run this example, the code will be interrupted by a syntax error, because there is an unnecessary set of parentheses around the statement `x in range(10)`. While some languages require parentheses around the `for` condition, the code above is in violation of Python's syntax, and as a result it cannot run. While these errors can be easy to fix, it is important to pay attention to the syntax of any language you are using; when switching back and forth between different programming languages (e.g., Python and R) it is easy to get your syntax mixed up!

# Best Practices

While syntax errors are very important, the fact that the code is interrupted by their presence makes them easy to spot and deal with. Even if your code runs properly, there may still be issues related to some of the "unwritten" syntax rules that govern Python and other programming languages. While these rules technically need not be followed for code to execute properly, they often make things easier for both the programmer and other users of the code. We detail a few of these rules below.

## Variable naming

While the name of a variable has no bearing on the role it will play in a block of code, this name can drastically affect how easily your code is understood. This is important because within long scripts of code, there may be dozens of variables in action, each with its own unique function. It is critical to ensure that each variable can immediately be identified and associated with its function in the code, which is mediated by its name. For example, naming a variable `a` might seem convenient in the sense that it is short and easy to type, but what does this name tell us about the function of this variable? The answer is almost nothing. Unless this variable is a place holder for the character `'a'`, this is probably not a very good variable name. Generally, we want to strike a balance between name length and name clarity. Incredibly long variable names are OK, but they can also make the code overly cumbersome, and should be avoided if possible. As we have already discussed, short character names make the code look shorter, but they give very little detail as to the function of the variables.

Often times, because we want variable names to give detail about their functions, our variable names may include multiple words. As an example, a variable detailing the number of eggs in a basket may be given the name `num_eggs_in_basket`. Notice a few things here: first of all, the word "number" is abbreviated to "num" so as to save space; this is a commonly accepted practice. Additionally, the word "a" is eliminated to save space; obviously, the word "a" does little to actually describe what the variable is doing. Most importantly, notice the way the words are separated in the variable name. Since spaces are not allowed in variable names (this would result in a syntax error), we use what is known as **snake case** to delineate words. Snake case is identified by words in all lower case separated by underscores rather than spaces. For Python, snake case is generally agreed upon as the best practice, but other formats (such as camel case, where new words are identified by capitalization, as in `numEggsInBasket`) are more generally accepted in other languages.

## Commenting

Another best practice that in no way affects the functionality of your code, but is still very important, is **commenting**. Comment lines are lines of code that are excluded from the actual execution process but can be used to add information about a block of code for the benefit of the user. An example of a comment is seen below:


```python
x = 3
# We have just instantiated a new variable x (which is a horrible name, by the way!) and given it the value 3.

print(x + 2)
# The print function prints x + 2, which is 5 here, to the screen.
```

    5


Notice the syntax for commented lines. The number sign (#) is used to signify the beginning of a comment, with one number sign being sufficient to classify the entire line as a comment. Once the line is "commented out" of your code, you can write whatever you want in there. Traditionally, especially for larger scripts with many variables, it is expected for programmers to provide a comment at the instantiation of each variable giving additional detail of what the variable does. Think of comments as an opportunity to explain why you wrote a line of code the specific way you did, or what function a block of code serves. Comments can also be used to break up long scripts into sections, which can be useful if a script contains multiple processes. At the extreme level, some programmers may provide comments every line, and these comments can become rather lengthy in some cases. Either way, commenting is always recommended, especially in parts of your code that are not immediately straightforward; remember to always write code in a way that anyone else would be able to understand!

To refer to a more comprehensive guide on best practices in Python, visit [this page](https://docs.python-guide.org/writing/style/). There are some Python constructs we have not gone over yet, but in general this provides a solid blueprint for coding best practices.

# Documentation

We have already discussed how to write docstrings for your functions in Session 2. Much like commenting, this is an important step in making your code understandable and easy to read. This is especially important when you are writing code that will eventually be viewed by other people. Just like traditional writing, keeping your audience in mind is always very important and can drastically affect how you document your code. For example, in some cases your code may only be viewed by you, if it is just a small inconsequential script that you are writing. In this case, you might still want to comment and document your code, especially if you are going to have to revisit this script in the future (it is alarming how easy it is to forget how you wrote a script in even a few months). That being said, the comments only need to be understood by you, so you may be able to get away with more abbreviated documentation.

As code becomes a more and more integral part of science as a whole, it is important to remember that you will often be writing code that needs to be reviewed in the same manner as the associated manuscript itself. Science is becoming more and more open, with freely accessible code from existing studies becoming a much more common practice at many journals. This means that the scripts you write for your publications may one day be viewable to anyone who reads your papers. Additionally, this means your scripts may be submitted for review along with your manuscripts. While this trend towards open science promotes collaboration and transparency in the field, it stresses the importance of documentation on scientists writing code. Reviewers are viewing your work from an outside perspective, and depending on the journal you are submitting to, may not be familiar with the methods you are implementing in your code. This stresses the need for documentation as it will help expedite the review process. In addition, if your code is published along with your manuscript, writing well-documented scripts that are easy to interpret will encourage other scientists to follow up on your method, which among other things can lead to important collaborative networking opportunities.

To put it briefly, documentation is always important, but how you document your code depends wholly on your audience. More information on this topic is simply a Google search away; as we could discuss documentation for a very long time, we instead encourage you to research best practices for code and code documentation individually, as it is an integral part of effective and open science.

# Efficiency

At the high levels of computer science, whether or not a script works is not as important as how quickly it works. This is because the most pressing problems in computer science often involve very large data sets or very computationally intensive algorithms. In other words, if an algorithm is too slow, it doesn't matter if it's correct - it simply can't be used. While computer engineers are constantly pushing to increase the efficiency of the hardware itself, computer scientists are also tasked with writing code that is efficient as possible. This field, known generally as **algorithmic complexity**, is a hot topic in computer science, and most computer science students are required to take at least one course on algorithms in their undergraduate education. A lot of this theory becomes very mathematically intensive, so we will simply introduce the problem and summarize how computer scientists think about complexity and efficiency.

As mentioned earlier, issues of efficiency and complexity are most pressing with large data sets. In general, if your script involves performing an operation on a list of 5 objects, it will probably not take very long no matter what the task is. In other words, it is not necessarily required to maximize efficiency in this case - the code will probably be pretty fast no matter what. But now imagine doing this same process for a list of a thousand or a million objects - it quickly begins to add up. Sometimes, the rate at which the time "adds up" is linear, and sometimes it is worse. The rate at which this time adds up is of primary concern to computer scientists, rather than the actual time it takes to execute. This is because simply using a stopwatch to measure how long a process takes neglects many other variables, including the strength of the computer itself as well as any other processes that computer may be running at the same time.

## Big-O Notation

Computer scientists have a mathematical name for this "rate at which time adds up", and it is known as **big-O**. We use big-O notation to explain how, when data size gets very large, a block of code executes. A simple example can be seen below:


```python
def print_numbers(n):
  for i in range(n):
    print(i)

print_numbers(5)
```

    0
    1
    2
    3
    4


As you can see, the function above prints every integer less than the input parameter `n` including 0. Here, the line `print(i)` was executed 5 times, as evidenced by the five unique print outputs, which corresponds to the input parameter `n` being instantiated at 5. If `n` were set to 10000, the `print(i)` line would be executed 10000 times. In other words, the speed of this code grows linearly with `n`, and from an algorithmic complexity standpoint, we say that it is **$O(n)$** (spoken out loud as "big O of n"). This is because as `n` gets very large, the speed at which `print_numbers` is executed is proportional to `n`. The example below is also $O(n)$:


```python
def print_numbers_twice(n):
  for i in range(n):
    print(i)
    print(i)

print_numbers_twice(5)
```

    0
    0
    1
    1
    2
    2
    3
    3
    4
    4


In all reality, this function probably takes about twice as long as `print_numbers` no matter how large `n` is, because it simply does twice the work, printing each number twice. However, the reason it is still $O(n)$ is because as `n` gets very large, the number of tasks for the computer to execute is still proportional to `n` (put rather simply, it's about `2n` here since there two print statements for each for loop). Here's an example of a block of code that isn't $O(n)$:


```python
def print_numbers_a_lot(n):
  for i in range(n):
    print_numbers(i)

print_numbers_a_lot(5)
```

    0
    0
    1
    0
    1
    2
    0
    1
    2
    3


As you can see from the number of print statements, when `n` is equal to 5, this one takes about as much time as `print_numbers_twice`, printing something to the screen 10 times. However, when `n` gets very large, this will be a very slow function. This is because it is essentially a nested for loop; for each value less than `n`, we call `print_numbers` for that value `n`, which in itself is $O(n)$. This function is $O(n^2)$. Code like this may not take very long when `n` is small, but as `n` increases, this block of code becomes much slower than anything that is $O(n)$.

There are many examples of different big-O notations, with the emphasis being that each one is compared to another based on their performance with large data sizes. This is something to keep an eye on when you write your code; using lots of loops nested inside of each other can occasionally cause large bottlenecks in your code. Having an eye to big-O notation can often times improve code efficiency in massive ways, especially when working with big data sets. Often times, code-related problems can be solved in a variety of ways, and even if each of these solutions yields the same result, they are not necessarily equal in their effectiveness due to efficiency.

As biologists, the data sets we work with can be quite large. As a result, it is important for you to think about code problems in terms of algorithmic efficiency, since one "level" of efficiency may be the difference between a script that takes a few hours to run and one that takes a few days. Being aware of potential efficiency bottlenecks in your code could vastly improve the effectiveness of the programs you write and speed up the scientific process for you.

Below are a couple links that provide more information on the math behind big-O notation as well as some additional examples. [This article](https://blog.bitsrc.io/algorithms-efficiency-big-o-in-simple-english-adbaedbcdfcf) does a nice job explaining why algorithmic efficiency is important (however, the examples here are in JavaScript, so the syntax is slightly different!). [This article](https://towardsdatascience.com/algorithmic-complexity-101-28b567cc335b) uses Python and also discusses some intricacies about the importance of code efficiency.

# Testing Your Code

## Why Test?

Writing tests of your code is part and parcel of any robust program. However the vast majority of biologists have barely ever heard of testing, and further, even if they have, they likely do not take the time to perform rigorous testing.

This is understandable as testing your code is a sometimes difficult and irritating task. I can understand that a busy scientist might think that there is some type of exception that applies to them since their full time job is not as a programmer.

However, you would be horrified at the number of scripts I've seen that have no tests, and as a result, produce incorrect results without even raising an error in the code. Code that runs with no error but gives an incorrect result is not only innaccurate but possibly incredibly dangerous as it could lead us to reporting incorrect results in our paper.

Testing is a whole subfield of study in the world of programming, and our goal is neither to overwhelm you, nor to spend too much time on this topic. We won't go into the vast majority of the details regarding testing generally nor in python, but our goal here is to make you aware of testing, and introduce you to the idea that you should be testing your code. If you move on further in programming, you will inevitably learn more about testing.

## How to Test?

You can test a multiple levels in code. The most common format is to perform 'unit tests', where the basic notion is to write independent tests for the smallest units of code. That is, when you write a function, you write a small piece of code to test it. This way, it's all run automatically so when you change the function, it will test automatically.

How to best write unit tests? When you write your code in plain .py files, you divide functions into different files (modules) so that similar functions are in the same file (i.e. one to deal with stats, one with all the data input, one with all the simulations etc.) You then have a 'main' program which imports all these modules and runs them. This way, you can test each module individually, and tell when there is an error immediately after making a change.

The simplest way to implement this is through `doctest` which tests using docstrings (THIS IS WHY ITS IMPORTANT TO WRITE EXAMPLES IN YOUR DOCSTRINGS!!!).

**A quick aside.** Unit testing in Jupyter is harder than a straight .py file being run through a shell/ console/ text editor. So, the version that we write here is slightly modified version for the .ipynb file, but that's okay.

So, testing in .ipynb files. The first thing we will do is steal one of our functions from last week to have an example.



```python
def prime_number(n: int) -> bool:
  """Return whether n is prime or not in the form of a boolean.
  Parameters:
              n (int): A whole integer greater than zero

  Returns:
              True/False (bool): A boolean

  >>> prime_number(4)
  False
  >>> prime_number(7)
  True
  """

  div = 2
  while (div <= n / 2):
    if (n % div == 0):
      return False
    div = div + 1
  return True
```

So this is our prime number function, and it will be relatively easy to test, however there are some caveats. When testing, you ideally want to test a few 'general' examples, and then any 'corner cases'.

Corner cases are specific inputs where your function might behave differently than expected, particularly if you happen to change something about how it's written, and so you want to ensure that you have a working function over ALL possible values.

Using the `doctest` module, let's test our prime number function above.


```python
def prime_number(n: int) -> bool:
  """Return whether n is prime or not in the form of a boolean.
  Parameters:
              n (int): A whole integer greater than zero

  Returns:
              True/False (bool): A boolean

  >>> prime_number(4)
  False
  >>> prime_number(7)
  True
  """

  div = 2
  while (div <= n / 2):
    if (n % div == 0):
      return False
    div = div + 1
  return True

import doctest
doctest.testmod()
```




    TestResults(failed=0, attempted=2)



So we can see that our test results are good! We attempted 4 tests, and none of them failed. We can see what happens when we do have a failed test by changing one of the expected outcomes


```python
def prime_number(n: int) -> bool:
  """Return whether n is prime or not in the form of a boolean.
  Parameters:
              n (int): A whole integer greater than zero

  Returns:
              True/False (bool): A boolean

  >>> prime_number(4)
  False
  >>> prime_number(7)
  True
  """

  div = 2
  while (div <= n / 2):
    if (n % div == 1): ##### NOTE THAT THIS IS WHERE WE MADE THE CHANGE
      return False
    div = div + 1
  return True

import doctest
doctest.testmod()
```

    **********************************************************************
    File "__main__", line 9, in __main__.prime_number
    Failed example:
        prime_number(4)
    Expected:
        False
    Got:
        True
    **********************************************************************
    File "__main__", line 11, in __main__.prime_number
    Failed example:
        prime_number(7)
    Expected:
        True
    Got:
        False
    **********************************************************************
    1 items had failures:
       2 of   2 in __main__.prime_number
    ***Test Failed*** 2 failures.





    TestResults(failed=2, attempted=2)



Keep in mind when writing these tests, that they are NOT exhaustive by any means, they simply document the use of the function in a few small cases. However, in this example, we still need to deal with our only corner case, which is zero.

Now without getting too pedantic, zero *technically* cannot be prime nor composite, so in theory, this function will work if it prints out `False` for zero, since we are only asking if the number if prime, not if the number is prime or composite. So let's add a test for zero.  


```python
def prime_number(n: int) -> bool:
  """Return whether n is prime or not in the form of a boolean.
  Parameters:
              n (int): A whole integer greater than zero

  Returns:
              True/False (bool): A boolean

  >>> prime_number(4)
  False
  >>> prime_number(7)
  True
  >>> prime_number(0)
  False
  """

  div = 2
  while (div <= n / 2):
    if (n % div == 0):
      return False
    div = div + 1
  return True

import doctest
doctest.testmod()
```

    **********************************************************************
    File "__main__", line 13, in __main__.prime_number
    Failed example:
        prime_number(0)
    Expected:
        False
    Got:
        True
    **********************************************************************
    1 items had failures:
       1 of   3 in __main__.prime_number
    ***Test Failed*** 1 failures.





    TestResults(failed=1, attempted=3)



So we notice that our test actually fails here! Well, remember that this function isn't currently written to handle zero. And we even noted this in our docstring. We can fix this in one of two ways. I'll show you both. The first would be to ensure the function returns `False` for zero, the other would be to reinforce the docstring and have the function throw an error when zero is passed. First let's rewrite it for `False`.


```python
def prime_number(n: int) -> bool:
  """Return whether n is prime or not in the form of a boolean.
  Parameters:
              n (int): A whole integer greater than zero

  Returns:
              True/False (bool): A boolean

  >>> prime_number(4)
  False
  >>> prime_number(7)
  True
  >>> prime_number(0)
  False
  """
  if n == 0:
    return False

  div = 2
  while (div <= n / 2):
    if (n % div == 0):
      return False
    div = div + 1
  return True

import doctest
doctest.testmod()
```




    TestResults(failed=0, attempted=3)



And we see now all three tests pass. We could also throw an exception, so let's write the function that way:


```python
def prime_number(n: int) -> bool:
  """Return whether n is prime or not in the form of a boolean.
  Parameters:
              n (int): A whole integer greater than zero

  Returns:
              True/False (bool): A boolean

  >>> prime_number(4)
  False
  >>> prime_number(7)
  True
  >>> prime_number(0)
  'ERROR: cannot pass zero. Zero is neither prime nor composite.'
  """
  if n == 0:
    return 'ERROR: cannot pass zero. Zero is neither prime nor composite.'

  div = 2
  while (div <= n / 2):
    if (n % div == 0):
      return False
    div = div + 1
  return True

import doctest
doctest.testmod()
```




    TestResults(failed=0, attempted=3)



And all our tests pass. Note we changed the doctest accordingly.

# Why is this important?

You'll have noticed in the process of testing our function for prime numbers, that we've actually improved the function! We had a function that previously, required the user to have read the docstring and know how to use it appropriately. That's not necessarily always going to happen, and so to avoid having the function throw an incorrect answer, we changed the function to better reflect the reality of our corner cases.

In sum, testing your function, often leads you to a more robust final version of the function itself.
