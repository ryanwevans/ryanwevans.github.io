---
layout: post
title:      "Common Error When Calling Dispatch Actions in Redux"
date:       2019-11-10 04:24:53 +0000
permalink:  common_error_when_calling_dispatch_actions_in_redux
---


I recently met with a senior developer and we got on the topic of calling dispatch actions in Redux.
<br/>
<br/>
He said that, even for developers with more experience, it's a frequent mistake to forget to call a dispatch action correctly by appending `this.props` to the function call.  So simple, but apparently he sees it actually happen pretty often.
<br/>
<br/>
So, instead of a correct call like this inside a container (or 'smart') component:
<br/>
`this.props.getFetchedData()`
<br/>
<br/>
Your call will look like this:
<br/>
`getFetchedData()`
<br/>
<br/>
The way you'll know that you've made this mistake is when it appears that your dispatch action just doesn't execute ( possibly without any generated error).  If you `console.log()` at different points inside your function, you'll see that the action function will be called and will execute, but it stops executing at the line that contains the  `dispatch` .
<br/>
I've had this happen to me without any error to give me a hint at my mistake.  It simply stopped executing when it hit the `dispatch()` .  It was strange.
<br/>
<br/>
<br/>
Remember that when you `mapDispatchToProps()` , or use the `connect()` helper function from react-redux, you've made your dispatch actions available as `props`, and therefore have to call them appropriately.  Otherwise, you're calling it as just a function, because you imported it into your component.
<br/>
<br/>
So hopefully if you understand why it happens, you'll be more likely to remember the fix if (or *when*, apparently) it happens to you.
<br/>
<br/>
Here are some additional reading resources on the subject:
* [Implementing Container Components](https://redux.js.org/basics/usage-with-react#implementing-container-components) (Redux.js.org)
* [How to get simple dispatch from this.props using connect w/ Redux?](https://stackoverflow.com/questions/34458261/how-to-get-simple-dispatch-from-this-props-using-connect-w-redux) (Stackoverflow)
* [Connect: Dispatching Actions with mapDispatchToProps](https://react-redux.js.org/using-react-redux/connect-mapdispatch#connect-dispatching-actions-with-mapdispatchtoprops) (React-Redux.js.org)
<br/>




