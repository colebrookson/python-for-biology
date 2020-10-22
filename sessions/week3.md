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
