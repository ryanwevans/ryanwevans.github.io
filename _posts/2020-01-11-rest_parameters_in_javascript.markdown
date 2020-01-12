---
layout: post
title:      "Rest Parameters in JavaScript"
date:       2020-01-12 03:12:42 +0000
permalink:  rest_parameters_in_javascript
---


If you're writing ES6 compatible code, using rest parameters is preferred over using the `arguments` object ([MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/arguments)).   If you remember, the `arguments` object represents all the arguments passed to a function that accepts an unspecified number of arguments.  It is like an Array in that it has a `length` property and indexes, but doesn't have the same built-in methods as an array.
<br/>
<br/>
Here's an example (from [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/arguments)) of how you would use `arguments` with a function:
<br/>
```
function func1(a, b, c) {
  console.log(arguments[0]);
  // expected output: 1

  console.log(arguments[1]);
  // expected output: 2

  console.log(arguments[2]);
  // expected output: 3
}

func1(1, 2, 3);
```

<br/>
In order to operate on the arguments passed into your function as a group like an array, you'll need to create an array from them.  That's where the rest parameter becomes handy, as it lets us represent an indefinite number of arguments as an array ([MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/rest_parameters)).
<br/>
Here's an example (from MDN) of how you would use the rest parameters syntax with a function:
<br/>
```
function sum(...theArgs) {
  return theArgs.reduce((previous, current) => {
    return previous + current;
  });
}

console.log(sum(1, 2, 3));
// expected output: 6

console.log(sum(1, 2, 3, 4));
// expected output: 10
```

<br/>
Because rest parameters use the spread syntax, you can use rest parameters to capture any remaining parameters beyond specified arguments.  So, in the example below, the first two arguments would not be included in the rest parameters array of arguments:
<br/>
```
function printArgs(a, b, ...theArgs) {
  console.log(a)
  console.log(b)
  console.log(theArgs)
}

print("first", "second", "third", "fourth", "fifth")

// Console will log:
// first
// second
// [third, fourth, fifth]
```

<br/>
So, to keep your code ES6 compatible, and to be able to work with an unspecified number of arguments as an Array, use the rest parameter syntax, and life will be much easier.
<br/>
<br/>
<br/>
Resources:
* [The arguments object (MDN)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/arguments)
* [Rest parameters (MDN)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/rest_parameters)
* [Rest Parameters and Spread Syntax (JavaScript.info)](https://javascript.info/rest-parameters-spread)
* [JavaScript | Rest parameter (Geeks for Geeks)](https://www.geeksforgeeks.org/javascript-rest-operator/)
* [Understanding the JavaScript Rest Parameter (Codeburst.io)](https://codeburst.io/understanding-the-javascript-rest-parameter-a2a465606d13)

<br/>

