---
layout: post
title:      "Deploying a React App with Rails API to Heroku"
date:       2019-09-09 03:52:04 +0000
permalink:  deploying_a_react_app_with_rails_api_to_heroku
---


Deploying a single app to Heroku can be tricky, filled with trial-and-error steps to try and get it working.  Deploying a React front-end application that uses a Rails API for data persistence, is like trying to deploy two apps at the same time.  It's not easy, but it can be done.
For this tutorial, you'll need to have a Heroku account and be logged in.  You'll also need to have the Heroku CLI installed (Heroku's instructions for installation are [here](https://devcenter.heroku.com/articles/heroku-cli#download-and-install))

Something that can make this process much easier, is if you create your Rails API app using PostgreSQL as the database from the start, instead of SQL:

```rails new myapp --database=postgresql```

If you create your app with SQL as the database, you'll have to change it to PostgreSQL before deploying to Heroku because Heroku doesn't support using SQL.  As part of the Heroku docs, they'll walk you through [how to do this](https://devcenter.heroku.com/articles/getting-started-with-rails5#add-the-pg-gem), but I still ran into a couple of issues.

It's also a good idea to duplicate your project into a new repository, and use this separate git repo for deploying to Heroku.  Give it a name like 'my-app-heroku'.  By doing this, you can preserve your original project and not worry about breaking it if you go into 'trial-and-error' mode to figure out the bugs.

My project had a file structure of one main root directory, with two sub-directories for each "app", the Rails API app and  the React client (front-end) app:
```
my-project-root-directory
    /my-app-api
    /my-app-client
```

With this structure, you're going to deploy each directory (api and client) to Heroku as if each is it's own project. But you'll `push` to Heroku from the main root directory, and the `push` command will be a little different (I'll explain when we get to that step).

Before we do anything, let's add a couple things so that when we we're ready to deploy to Heroku, we'll already be set up for our Heroku client app to talk to our Heroku api app.

So, your api and client will live on different url's on Heroku, so you'll need to direct your api calls from your client app to the new url of the heroku api app.  In development mode, you were probably making your api calls to 'localhost:3001'.  So you'll need to change that location to the actual Heroku url in a few steps.  I'll let you know when it's time.

Also, because you'll be making cross-origin api calls, you'll need to avoid Cross-Origin Resource Sharing (CORS) issues.  You can do this by uncommenting the gem `rack-cors` in your gemfile (then run `bundle install`) and then uncommenting the CORS lines in your cors.rb file (inside the directory my-app-api/config/initializers/cors.rb).  The part you need to uncomment should look something like this:

```
Rails.application.config.middleware.insert_before 0, Rack::Cors do
  allow do
    origins 'https://my-heroku-client-app-name.herokuapp.com'

    resource '*',
      headers: :any,
      methods: [:get, :post, :put, :patch, :delete, :options, :head]
  end
end
```

Next, you'll also want to tell Heroku to do two things when it runs your api app:
* Start your API server (so it's available for api calls from the client app)
* Run your database migrations each time you release/update your app

To set these tasks up, create a new file called Procfile (no file extension) in the root directory of your api app.  Add the following lines of code to this file:

```
web: bundle exec rails server -p $PORT
release: bin/rake db:migrate
```
Heroku reads this file each time it starts up your app.
</br>

Okay, you're doing great! Now we're ready to deploy to Heroku...

So let's get started and first change directories into your api directory (if you aren't already there).  From here, to create a new Heroku app for your api app, run:
```
heroku create
```
---
*Or, if you already created a new app from your dashboard on Heroku's website for the api, you can add it to your api app by running:*
```
heroku git:remote -a my-heroku-api-app-name
```
---
</br>
Next, change directories back to your main root directory.  You have to push to Heroku from here, because Heroku will not run your app from a sub-directory.  The command to do this is:
```
git subtree push --prefix my-app-api heroku master
```
You can probably see what's happening here.  From your main root directory, you're pushing a subtree to `heroku master`, and the `--prefix` is changing directories to the subtree `my-app-api`. 

</br>
Now the only steps left are to do the same process from your client directory.  From your root directory:

```
cd my-app-client
heroku create
cd ..
git subtree push --prefix my-app-client heroku master
```

</br>
NOTE: I'm using VS Code as my text editor, so this could be specific to it, but if I tried to push to Heroku after making any changes to my api or client directories, it tried to push to the most recent Heroku app (not usually the correct one).
So if this happens to you, whenever you need to push any updates to Heroku, you'll need to re-add your Heroku app to your sub-directory again (api or client).
But now, because you already have a Heroku app for each directory, you'll *add* it each time before you push to Heroku:

```
heroku git:remote -a my-heroku-app-name
```
then change back to your root folder and:
```
git subtree push --prefix my-app-api heroku master
```
As you update your app, you'll get used to this set of commands.  You'll be going back and forth between directories, re-adding the correct Heroku app before each push to Heroku from the main root directory.

Now, as you probably already know, Heroku issues random, unique app names.  Since you'll need to remember the Heroku app names for both your api and client apps, you may want to [rename your Heroku apps](https://devcenter.heroku.com/articles/renaming-apps) to something easier to remember.  To do this, from within the appropriate directory (my-app-api, or my-app-client) you can run the following, where 'newname' is the new name of your choice:
```
heroku apps:rename newname
```
Now that you've changed your app directory, you'll need to go through the steps (above) to push the change to Heroku.

</br>
</br>
And once you've done that... your done!  

To open your app, run:
```
Heroku open
```
Or open the client app from your dashboard on Heroku.com.

Don't forget that Heroku puts it's dyno's (aka, your app) to sleep when it isn't in use, that's how it affords to offer limited free hosting.  So this will slow down the loading of your app, that's normal.  When you open the client app, once it starts up, the content from your API will be blank for a few moments while Heroku is starting up the API app.  But don't worry, once the API app starts, your React components should re-mount and display the information from your Rails API.

</br>
Now celebrate!!

![](https://media.giphy.com/media/LSNqpYqGRqwrS/giphy.gif)


If you follow this process and feel there is room for improvement, or find anything that you feel should be added for clarity or completeness (or changed!), *please* be sure to contact me and let me know.  Deploying to Heroku can be an arduous task, so I'm hoping this post will be helpful for others.  -Thank you!
