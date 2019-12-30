---
layout: post
title:      "Big O Notation"
date:       2019-12-30 07:29:26 +0000
permalink:  big_o_notation
---


In a recent post, I mentioned Big O notation:
<br/>
<br/>
Simply put, Big O notation is used to describe the running time or space requirements of executing an algorithm as the size of the input to the algorithm increases. The differences between two functions that do the same thing, but in different ways (like iteration vs. recursion), becomes very clear when you consider very large datasets passed into the algorithm.
<br/>
Big O focuses on the worst-case requirements of running an algorithm, which can be referred to as the upper-bound of the growth rate.
<br/>
<br/>
I thought I should expand on this and share some good resources for learning more about Big O.  It can be a bit confusing to understand at first.  I've found that different sites explain it differently, using different examples.  So some examples might make more sense to some people, which can help immensely when learning something like Big O.
<br/>
<br/>
<br/>
For the record, here's the definition of Big O  from [Wikipedia](https://en.wikipedia.org/wiki/Big_O_notation):
<br/>
<br/>
*Big O notation is a mathematical notation that describes the limiting behavior of a function when the argument tends towards a particular value or infinity.  In computer science, Big O notation is used to classify algorithms according to how their running time or space requirements grow as the input size grows.
<br/>
<br/>
Big O notation characterizes functions according to their growth rates: different functions with the same growth rate may be represented using the same O notation.
<br/>
<br/>
The letter O is used because the growth rate of a function is also referred to as the order of the function. A description of a function in terms of big O notation usually only provides an upper bound on the growth rate of the function.
<br/>*
<br/>
<br/>
The main point here is, what are the worst-case requirements (in terms of space or time) that will be needed to run an algorithm as the input gets huge.  If you remember to think in terms of huge amounts of data being fed to your algorithm to process, you'll understand why things like smaller exponents, multipliers and additions are simply ignored (because they become irrelevant as the data gets larger, compared to the lead exponent).
<br/>
<br/>
<br/>
Take a look at some of these references to find one that connects for you:
<br/>
* Big O Notation in JavaScript ([Cesar's Tech Insights](https://medium.com/cesars-tech-insights/big-o-notation-javascript-25c79f50b19b) on Medium.com)
* Big O Notation - Using not-boring math to measure code's efficiency ([Interview Cake](https://www.interviewcake.com/article/java/big-o-notation-time-and-space-complexity))
* Big-O notation ([Khan Academy](https://www.khanacademy.org/computing/computer-science/algorithms/asymptotic-notation/a/big-o-notation))
* Big O notation ([freeCodeCamp](https://guide.freecodecamp.org/computer-science/notation/big-o-notation/))
* A beginner's guide to Big O notation ([Rob Bell](https://rob-bell.net/2009/06/a-beginners-guide-to-big-o-notation/))
<br/>
<br/>

If you feel like you're struggling, this article may help improve your outlook (despite the ominous title):
* 10 Signs You Will Suck at Programming ([Noteworthy - The Journal Blog](https://blog.usejournal.com/10-signs-you-will-suck-at-programming-5497a6a52c5c) on Medium)
<br/>
<br/>

<br/>
Good luck!


