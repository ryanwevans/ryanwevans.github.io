---
layout: post
title:      "Rails Project: A Hidden Validation Found"
date:       2019-02-07 05:52:15 +0000
permalink:  rails_project_a_hidden_validation_found
---


While working on my Rails Portfolio Project, I realized that I had one relationship that was fulfilling two different requirements.  I wasn't comfortable with that, so before submitting my project (and likely getting told that I'll need to revisit those specs), I decided to challenge myself by adding new models and relationships to my existing project.

It was quite an undertaking, more than I probably realized when I made the decision.  I had to figure out what the new models should be, how they would fit in with what I already had, and what purpose they would serve.  Some of the ideas I had that seemed good for the purpose of the application, were actually far more difficult to implement and weave into the current project in a reasonable amount of time.

I ultimately found two models that would work well.  One was a higher level model that some current models would `belong_to`, which would fulfill one of those requirements I had been doubled up on.

The other model was one that, although not needed if I used the first, I couldn't walk away from because it seemed like an obvious feature that the application needed.  It was the Comments model, which would allow users to share comments on Activities that they had signed up for.

So I kept going, adding the Comments model to the project, and it was fairly straightforward.  Just a couple subtle adjustments to the forms for adding comments so it could live on same page as the Activity 'show' page (rather than it's own separate page).
But then when I tested the functionality of adding and viewing comments on the Activity page, none of them were appearing on the page.  I couldn't find what was going on, because the all my code was correct.

So I opened up the Rails console and started poking around.  Creating, retreiving, and assigning comments and activities.  I was trying to confirm the functionality of my code against my expectations.  Doing this helped me find and confirm that the comments I was creating weren't being persisted.  I ran the following code in the console to see what errors were happening (the errors are returned in the console if you add the ! (bang) to `.create`, `.save`, etc.):

```
2.5.3 :001 > Comment.create!
   (0.1ms)  begin transaction
   (0.1ms)  rollback transaction
Traceback (most recent call last):
        1: from (irb):1
ActiveRecord::RecordInvalid (Validation failed: Title can't be blank, Content can't be blank, Activity must exist, CampCounselor must exist)
```


Notice in the list of validation failures, that the user (CampCounselor) "must exist".  But wait, I didn't have any validations set up for this in my Comment model??  So to figure out why this was happening... I googled it!
Here's what my Comment model looked like:


```
class Comment < ApplicationRecord
  validates_presence_of :title
  validates_presence_of :content

  belongs_to :activity
  belongs_to :camp_counselor

end
```


What I learned from StackOverflow and a couple programmer's blogs, and the Rails GitHub page was that, implemented in Rails 5, whenever you define a `belongs_to` association, it is required to have the associated record present by default.  Which means that validation fails without it, and your instance won't save.  I also learned on the [Rails GitHub](https://github.com/rails/rails/pull/18937) page that this behavior is intended by Rails developers:


>"don't even need to talk about optional here. What they wanted to do is now being done for them." - Rails creator, David Heinemeier Hansson


Now that I knew what the problem was, I knew that I needed to add `optional: true` to the belongs_to in my Comment model.  Now it looks like this:


```
class Comment < ApplicationRecord
  validates_presence_of :title
  validates_presence_of :content

  belongs_to :activity
  belongs_to :camp_counselor, optional: true

end
```

Problem solved!  Finally things were working as expected.  Although it was such an easy fix, it had a pretty big impact on the functionality of my application.  I find this is commonly the case.

I am so thankful that Flatiron teaches those tricks like `rake routes`, `rails c`, `binding.pry` and how to read and understand the errors that we encounter as programmers.  Not to mention the wealth of resources on the internet.  The more I search for answers, the better I get at finding them.

