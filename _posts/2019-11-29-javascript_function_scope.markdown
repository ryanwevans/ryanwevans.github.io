---
layout: post
title:      "JavaScript Function Scope"
date:       2019-11-29 20:42:45 +0000
permalink:  javascript_function_scope
---

When learning JavaScript, scope can be confusing to understand.  Without understanding scope, you can experience unexpected behavior in your code.
<br/>
<br/>
Take a look at the following code snippet.  What do you think will be logged to the console?
<br/>
<br/>
```
let word = ‘outside';
function logWord(){
    console.log(word);
    let word = ‘inside';
};
logWord();
```
<br/>
I’ll give you a hint: it won’t log ‘outside’.  It won’t log ‘inside’.  And guess what, it won’t throw an error.
<br/>
What’s the answer? It will log ‘undefiined’ to the console.  This is because of functions create their own, or a new, scope.
<br/>
<br/>
```
let word = ‘outside’;
// global scope
function logWord(){
    // new scope starts here, so variables declared inside won’t be available outside the function
    console.log(word);
    let word = ‘inside';
};
```
<br/>
To understand this better, we should go over declaration vs. assignment.
<br/>
<br/>
<br/>
<br/>
**Declaration vs. Assignment**
<br/>
<br/>
Declaration is simply that, declaring that a variable exists. This does not include the assignment of its value.  It only initializes the variable and by default sets its value to 'undefined'.
<br/>
<br/>
```
let word
// word is assigned a value of 'undefined' by default
```
<br/>
We could also declare the variable and assign its value at the same time:
<br/>
```
let word = ‘outside’
```
<br/>
In JavaScript, variable declarations are hoisted to the top of their scope, but their assignments are not, so their values are set to 'undefined' by default.
<br/>
Let’s rewrite our code to reflect the way it is read:
<br/>
```
let word = ‘outside’;
function logWord(){
    let word  // word is declared and assigned a value of ‘undefined'
    console.log(word);
    word = ‘inside’;  // word is assigned a value of ‘inside’
};
```
<br/>
<br/>
So when we hit the console.log() line in our function, the value of word is ‘undefined’, until the next line in the function which assigns the value of word to ‘inside’.  Therefore, the console statement will log ‘undefined’.
<br/>
<br/>
The best way to avoid unexpected behavior in your code is to declare your variables at the top of their scope.
<br/>
