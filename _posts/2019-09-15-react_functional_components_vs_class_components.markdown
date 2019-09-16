---
layout: post
title:      "React Functional Components vs. Class Components"
date:       2019-09-16 00:44:22 +0000
permalink:  react_functional_components_vs_class_components
---


React allows you to define components as functions or classes.  So, when creating components in React, how do you know whether to create a functional component or class component?  Let's take a look at the differences between the two.

<br/>
**Functional components** are just as their name implies, they are written as simple JavaScript functions and return a React element.  They also accept the 'props' (short for 'properties') argument passed to them from the parent component.  They are meant to be simple and concise:
```
function Greeting(props) {
 return (
  <div>
   <h1>Hello {props.name}!</h1>
  </div>
 );
}
```

<br/>
**Class components** are more complex because they allow us to have access to features like local state and lifecycle methods (i.e. `componentDidMount` and `componentWillUnmount`).  In order to access these additional features, their syntax is a little different from functional components because they are a subclass of React.Component:
```
class Greeting extends React.Component {
 render() {
   return (
	  <div>
	   <h1>Hello {this.props.name}!</h1>
	  </div>
	 );
  }
}
```

*That `class` and `extends React.Component` is what gives this component access to additional features.

<br/>
Some people create all their components as functional components, then change them to class components as the need arises within the component (like to add state or utilize lifecycle methods).
Yet others create all their components as class components, because class components work for both situations (therefore safer), then refactor the ones that don't need access to state or lifecycle methods into functional components later (creating more work).

Since functional components are relatively fast and easy to implement, I would suggest starting here.  Then, depending on what each component does, it'll be easy to know when to create/change a functional component to a class component, because your component needs the additional features of a class component.

Or if you think about it from another angle, all components *can* be class components and your app will work just fine, although it'll be more complex than it needs to be.  On the other hand, not all components can be functional components, because they may need access to more features.

<br/>
The cleanest approach is to plan ahead and determine what each component's purpose is (does it need state?). But if that isn't possible, then the *next* cleanest approach is to only do the extra work of creating a class component when the purpose of the component warrants it.  This way, you're not doing any extra work, and your components will appropriately reflect their intended purpose.

<br/>
*Additional resources:*

* [React.Component](https://reactjs.org/docs/react-component.html) page on reactjs.org - describes additional features of class components in detail
* [Function and Class Components](https://reactjs.org/docs/components-and-props.html#function-and-class-components) page on reactjs.org

