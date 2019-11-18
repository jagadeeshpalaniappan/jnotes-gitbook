# React Core Concepts

## What is ReactJS ?

Key points to answer this question are that it’s a UI library and not a framework. Here interviewer can ask you the difference of a library and framework. Another question related to this can be the comparison of Angular and ReactJS.

## State and Props :

Questions related to state and props are commonly asked in ReactJS interviews. You should know that state stores the object values which are native to a component and props are the ones which are passed between components \(normally from parent to child components\) in ReactJS.

## Functional and Class Components :

Main difference between functional and class components is in the syntax. In functional components props are passed as arguments to component name. While, in class components, props are passed as arguments to constructor. Before ReactJS v16.8, it was not possible to manipulate ‘state’ and use ‘lifecycle’ methods in functional components but now we can use both through hooks. Questions related to useState and useEffect hook are also asked.

## Lifecycle methods :

Lifecycle methods are used to perform different actions in ‘life’ of a component. The interviewer might ask you about a particular lifecycle function and how it works.

## Hooks :

Hooks are used to implement state changes and lifecycle in functional components. To change state you can use useState\(\) hook and to implement lifecycle you can use useEffect\(\) hook. The interviewer might ask you about internal workings of useState\(\) and useEffect\(\) hook.

## State Management :

State Management is another concept which is commonly asked in ReactJS interviews. Most popular library in this regard is ‘react-redux’. Redux is based on flux architecture. There are other alternatives as well like ‘react-unstated’ and others.

## Necessary modules :

Routing is needed in web-applications to navigate between components. In ReactJS, we can use react-router and similar packages for routing. Interviewer can ask you about these packages. If you have worked on two packages used for same problem, then he may ask you about core difference between them and which one did you find useful and why?

## Data binding :

ReactJS follows the concept of one-way data binding. So, in this regard, props are passed from parent to child component. Interview may ask you comparison of Angular’s two-way data binding with React’s data binding.

## Virtual DOM and Actual DOM :

This is another important concept. You should know that how virtual DOM works in the ReactJS’ context. Additionally, interviewer might ask you about how ‘diffing’ algorithm works.

## Event handlers :

Event handlers in ReactJS are used similarly like JavaScript. But events fired by those handlers are ‘synthetic’ in nature. It means that events in ReactJS are actually wrappers around the browser’s native events in order to fix issues related to cross-browser compatibility.

## Memoization :

Memoization is a new concept in ReactJS through which we can store a computationally heavy functional component in memory. We can reuse that component again calling it from cache.

