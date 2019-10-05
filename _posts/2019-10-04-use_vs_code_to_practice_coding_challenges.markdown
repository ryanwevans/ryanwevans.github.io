---
layout: post
title:      "Use VS Code to Practice Coding Challenges"
date:       2019-10-05 02:52:50 +0000
permalink:  use_vs_code_to_practice_coding_challenges
---


In a previous post, I mentioned several resources to practice coding challenges to help prepare for technical interviews.  In this post, I'll explain why it's a good idea to use a code editing application like VS Code to code your solutions.
<br/>
<br/>
I think every practice coding site has a built-in code editor to use for typing and submitting your solution.  But, I've found that when submitting a solution through the built-in editor, getting a black-and-white pass/fail response doesn't help with learning.
<br/>
Oftentimes, your solution is run with several varied scenarios.  These scenarios include edge cases, where there is an unexpected or uncommon argument(s) passed to your function (like negative values, etc.) to see if it still produces the correct outcome.  If your function fails to return the correct outcome, you can't really test why and where it didn't work correctly.
<br/>
<br/>
This is where a code editor like VS Code comes in handy.  You're very likely already using it and familiar with it.  Which means you already have some tricks you're using to test your code at different points to see what is happening.  Throwing in a `console.log( )` can help you pinpoint what may be going wrong.
<br/>
In VS Code, create a new file and code your solution in it.  Name the file something very similar to the name of the practice question.  Don't forget to use the correct file extension to let VS Code know what language your using (i.e. 'ExampleFile.js' for Javascript).
<br/>
<br/>
Then, open the 'Output' tab (Shift+Command+U).  This is where you'll see you're code run.  Now, to run your code, simply click on the 'play' button in the top-righthand corner of the editor window.  You should see in the 'Output' tab the result of running your code.
If you only see something like this:
<br/>
`[Done] exited with code=0 in 0.083 seconds`
<br/>
<br/>
Then you need to wrap your function call in a `console.log( )`.  That should do the trick.
<br/>
If you want to clear the 'Output' tab, just click on the small logo that says 'Clear Output' when you hover your mouse over it.
<br/>
<br/>
Want another great idea?
<br/>
Create a local folder and create a new file for each practice coding question inside of it.  This way, you can go back and review questions you've already worked through.  Great idea for brushing up before a technical interview!
<br/>
<br/>
![.](https://media.giphy.com/media/JIX9t2j0ZTN9S/giphy.gif)
