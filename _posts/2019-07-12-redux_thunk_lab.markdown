---
layout: post
title:      "Redux Thunk Lab"
date:       2019-07-12 20:05:46 +0000
permalink:  redux_thunk_lab
---


### This lab is the last lab before starting your final project with Flatiron.  It's exciting to get this far and have only one lab left!

The *problem* is that this lab isn't one to breeze through.  It has some vague instructions which can leave you with questions before you even start.  Some of the questions I had were:

* Since we are dispatching 'LOADING_CATS' in the action creator, is there something specific we're supposed to do with it?

* Why are we using combineReducers if we only have one reducer?

* Why is there an empty link to 'CatBook' in App.js?


I proceeded with building my app, but wasn't feeling confident.  My plan was to build out the basic functionality to meet what I understood the specs to be, then focus on the tests to make the necessary changes.  This worked, for a while.  But then I had some problems.  I had two tests that held me up for a long time.  I got help from a technical coach on the first, and it took us a good twenty minutes just to figure out what we needed to do, but it didn't seem to make the much sense.  
The second test had me and two technical coaches totally stumped for about a day.  One coach continued to work on it on her own to see what she could find, and connected with me when she figured it out.  So here's what happened and hopefully this will help others avoid the same challenges...


First, to pass the tests, the formatting of the state in your reducer needs to be very specific.  Be sure to read the failing test to see what your formatting needs to be.  In your action creator, the code probably looks something like this:

```
export function fetchCats() {
    return (dispatch) => {
        dispatch({ type: 'LOADING_CATS' });
        return fetch('http://localhost:4000/db')
        .then(res => res.json())
        .then(catsData => dispatch({ type: 'FETCH_CATS', payload: catsData.images})
        )
    };
}
```

Notice that you're dispatching to LOADING_CATS, then again dispatching to FETCH_CATS.  Pay attention to what you return as your new state in your LOADING_CATS action, because that new state will then be part of your return statement updating your state in FETCH_CATS, too.
Since there were no specs about what the LOADING_CATS was supposed to do, I set it to simply return `false`, thinking I was leaving it the same.  My action looked like this:

```
case 'LOADING_CATS':
            return false;
```

That actually changed my state incorrectly.  That incorrect state was then included in my new state returned by FETCH_CATS, which was where I thought the problem was, and spent a while trying to fix the return statement in my FETCH_CATS action.

What my return statement should have looked like, inside LOADING_CATS, is a mirror of what it was inside state:
```
case 'LOADING_CATS':
            return {
                ...state, loading: false
            }
```

This fixed the problem, and I later decided to change it to `loading: true` while my fetchCats() action creator is retreiving the data from the cats api.  This way, I could use it to trigger a message to the user in the view ( `<h2>Loading cats....</h2>` )


My next failing test had everyone stumped!  For some reason, after my state was successfully updated/populated with cat objects, my CatList component wasn't re-rendering.  We narrowed it down to mapStateToProps, and that it wasn't assigning my new array of pictures from state to props in App.js, which then should have been passing those props down to my CatList component.

In my first round with a technical coach, my original index.js file looked like this:

```
const rootReducer = combineReducers({
    catsReducer
});
```

Since I only had one reducer, I didn't assign a key (I had found this syntax online, oops!).  They suggested a small change to add the  `cats:`  key to my combineReducers helper function, like so:

```
const rootReducer = combineReducers({
    cats: catsReducer
});
```

At first, this didn't change anything in regards to the failing test, so we continued to search for the answer.  But later, when stepping through the code in debugger again, a coach noticed that the format of the state included  `cats` .  So it turns out that the  `cats`  key was needed, and if we hadn't added it in there, we wouldn't have seen the new formatting of state it created.
Now, if we changed mapStateToProps from this:

```
const mapStateToProps = (state) => {
    //debugger
  return {
    loading: state.loading,
    pictures: state.pictures
  }
}
```

To this (notice the addition of `cats` ):

```
const mapStateToProps = (state) => {
    //debugger
  return {
    loading: state.cats.loading,
    pictures: state.cats.pictures
  }
}
```

Everything worked great!  Whew!!

In regards to the last question I had when I started this lab, I have no idea why the empty link was there.  Neither did any of the technical coaches.  I went ahead and changed the html tags and kept going....

If you get stuck on this lab, and there's no intuitive answer (check for typos, too), I would suggest asking for help sooner than later... :)

I hope that this is helpful to others out there that have challenges with this lab!

Congratulations to you, too, for getting this far!!  ...and good luck!

