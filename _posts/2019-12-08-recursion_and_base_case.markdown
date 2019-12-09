---
layout: post
title:      "Recursion and Base Case"
date:       2019-12-09 04:56:55 +0000
permalink:  recursion_and_base_case
---


Recursive functions can certainly be confusing, and base case isn't always explained well, either.  Let's take a look at what a recursive function is, how it executes, and where the base case comes into play.
<br/>
<br/>
<br/>
Wikipedia's definition of **recursion** is:
<br/>
<br/>
*Recursion in computer science is a method of solving a problem where the solution depends on solutions to smaller instances of the same problem.*
<br/>
<br/>
... and their definition for **base case** is:
<br/>
<br/>
*A terminating scenario that does not use recursion to produce an answer*
<br/>
<br/>
<br/>
<br/>
A recursive function is one that calls itself repeatedly until it reaches the base case, then the base case simply returns an answer/value because it is evaluated after the last recursion.
<br/>
<br/>
Let's say that you want to add all the numbers from 1 to n.  This can be broken down into the same repeated step of adding each number to the next, repeated until you reach the last number.  When you reach the last number, you can just return the number.  This is your base case.
<br/>
<br/>
Let's look at an example:
```
function sumToN(n) {
    if (n > 1) {
        return n + sumToN(n - 1)
    } else {
        return n;
    }
}
```
<br/>
Now let's walk through calling this function and set n as 5.  As the function calls itself until it hits the base case, it would be the equivalent to the following steps:
```
1. return 5 + sumToN(4)
 2. return 4 + sumToN(3)
  3. return 3 + sumToN(2)
   4. return 2 + sumToN(1)
    5. return 1   // base case, just return the value here.
// Now that there is a value, the function then fills in the calculations going back up the stack:
   6. return 2 + 1   // equals 3
  7. return 3 + 3   // equals 6
 8. return 4 + 6   // equals 10
9. return 5 + 10   // equals 15
```
<br/>
<br/>
I hope that this helps simplify what recursion does, visually, and makes base case easier to understand!
<br/>

