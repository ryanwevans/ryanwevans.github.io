---
layout: post
title:      "Rails/JavaScript Portfolio Project"
date:       2019-05-01 02:02:07 +0000
permalink:  rails_javascript_portfolio_project
---


As I planned out converting my Rails project to JavaScript, AJAX and JQuery, I started to realize that it could be a tall order to convert all the views, relationships and forms.  During office hours, we were talking about these challenges, which lead to the discussion that we didn't originally design our Rails projects intending to convert it to JS later.  That realization made me feel a little bit better about what I needed to do.

If you focus on the actual requirements of the Rails/JS project, you really only need to demonstrate the concepts (like using JavaScript to "repaint" the DOM instead of Rails refreshing the page).  We're not really being asked to convert *all* of our routes, views, forms and models to strictly JS.  We're only being asked to *demonstrate* these concepts using our Rails project as a starting point.

I felt relieved knowing that I didn't have to tackle every complex relationship, view, etc.  There are some fantastic videos out there (I watched ones recorded by Cernan Bernardo and Brad Smith) that were immensely helpful.  I treated them as a sort of code-along, but had to translate the concepts and syntax they were covering to my own project.  After that, I went ahead and formally worked on refactoring parts of my Rails project to JavaScript.  Eventually I had everything working, and you couldn't tell the difference between a Rails-rendered view and a JS-rendered view.  I had also utilized JS Model Objects to make my objects and their attributes and relationships available to the 'front end' of my project.

My next step was to do something that I've done before, that helps me really understand new concepts and syntax.  I made a local copy of my original Rails project, and re-coded my project to JS.  When I do this step, I try not to look at my completed project for hints if I get a little stuck.  I try to only use the internet as my resource, reading the documentation, stack overflow, etc..  This way, I have to really walk through line by line and understand what each line of code is doing.  I check results a lot in the browser, using the Chrome tools and console.log() to view what is being returned at different points of my code.  (By the way, there is a great demo on how to use the Chrome DevTools to debug a project, that my instructor shared with me.  You can view it [here](https://developers.google.com/web/tools/chrome-devtools/javascript/))

The other thing I thought would be a good idea, is to write a blog post about at least one of the concepts that I'll have to demonstrate knowledge of during my project assessment.  I figure that if I'm doing some research on a topic to better understand it, I should demonstrate that knowledge in a blog post.  I holds me more accountable to actually being able to explain (*in actual words*) the concept and not just tell myself that "I got it".

After doing the extra work, I feel much better about the project and concepts.  And now I can see how those more complex views I was originally worried about, could be converted to JS without much trouble.  Something I had a harder time seeing before.
