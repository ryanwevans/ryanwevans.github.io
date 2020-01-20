---
layout: post
title:      "Nested For Loops and Big O"
date:       2020-01-20 00:44:18 -0500
permalink:  nested_for_loops_and_big_o
---


When comparing two strings or arrays, we tend to take the easy route which is to nest `for` loops, comparing each element from the first object to all the elements of the second object in a nested loop.
<br/>
<br/>
The problem with this approach, is that the time complexity is O(n^2).  So, as your input grows, the runtime required gets significantly larger.
<br/>
<br/>
So, how can we still accomplish the comparison, but with a more reasonable, smaller time complexity?
<br/>
<br/>
<br/>
Let's look at an example.  Let's determine if two strings are anagrams.  Remember what an anagram is? Here's the definition from [Wikipedia](An anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.[1] For example, the word anagram can be rearranged into nag a ram, or the word binary into brainy or the word adobe into abode.):
<br/>
<br/>
*An anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.[1] For example, the word anagram can be rearranged into nag a ram, or the word binary into brainy or the word adobe into abode.*
<br/>
<br/>
<br/>
Here's an approach to comparing two strings that doesn't utilize nested `for` loops.  Instead, we'll create two separate `for` loops.
<br/>
<br/>
We'll use the first loop to add each character of the first string (`str1`) to an object (`obj1`).  The character (`char`) will be the key, and we'll set it's value to 1.  If a character is already in the object, we'll increment it's value by 1.
<br/>
<br/>
Now let's move on to the second loop.  This time, we'll check the object (which holds the counts of each character from string1) to see if each character from string2 (`str2`) is there.  If it isn't, then we can return false, because both strings must have the same characters in order to be an anagram.
<br/>
If the character *is* there, we'll decrement it's value by 1.  By the end of the loop through string2, if all characters have been found and decremented in the object, we can return `true`... right?
<br/>
<br/>
Well, almost.  We can if, before we begin the character comparisons, we verify that the lengths of both the strings are the same.  This way, we won't miss any extra characters that don't get caught by comparing characters in string2 to those in object1.
<br/>
<br/>
Take a look at the example code:
<br/>
<br/>
```
function isAnagram(str1, str2){

    // check that both strings have the same number of characters first!
    if (str1.length !== str2.length) {
        return false;
    }
    
    let object1 = {};
    
	// Add or increment each character from string1 to object1
    for (let char of str1) {
        object1[char] ? object1[char]++ : object1[char] = 1;
    }
    
	//Check for existence and decrement each character from string2 in object1
    for (let char of str2) {
        if (!object1[char]) {
            return false
        } else {
            object1[char] --;
        }
    }
    return true;
}
```
	
<br/>
So, let's review the time complexity of this approach.
<br/>
<br/>
A `for` loop has to check every character in it's string argument, so that is a complexity of O(n).  Since we have two `for` loops, the complexity is O(2n).  We can remove the multiplier of 2, because it's irrelevant.
<br/>
<br/>
So that means that the time complexity is O(n).  O(n) is much better than where we started with O(n^2).  And we acheived this major improvement in complexity with a minor adjustment to our approach!
<br/>
<br/>
Happy coding!
<br/>



