# React Interview Qstns \[TODO\]



{% tabs %}
{% tab title="Qstns" %}
```csharp
# What do you like and dislike about React? 
## Likes:
- Love 'unidrectional-flow' from parent to child and that 
- React is pretty much javascript

## DisLikes:
- Initially disliked JSX (felt MVC was better) // especially coming from Angular background
- But after researching more and more loved the concept // VirtualDOM 


# Conditional rendering and List rendering 
- What is the signifance of having the `key` prop when rendering a list of elements 
    - explain: how react compares the elements the under the hood (to avoid rerender)
- What is a potential bug that you can introduce when using `index` as key


# Class component's lifecycle methods
- There will always be legacy code that you need to maintain
- Learn 
    - mounting phase methods // componentDidMount
    - updation phase methods // componentWillUpdate, componentDidUpdate
    - unmounting phase methods // componentWillUnmount
    
- 'Order of invocation' and a brief description of when you'd use each one of them


# Context API
- What is 'prop drilling'
- how can you overcome that using context API


# Hooks
- What was the need for hooks?
- useState, useEffect and useContext


# Optimization
- Pure components
- memo
- useMemo and useCallback


# How to share logic across components?
- Higher order components
- Render props pattern
- Custom hooks


# What are some of the packages that you use along with React? 
- Styling // Material-UI, styled-components (emotionjs)
- Routing // React Router
- Form handling    // Formik, React Hook Form
- State management // Redux or ContextAPI

# CRA vs Custom webpack config
- What is Redux? // State management Lib // Single Store // uniDirectional State Update
- How do you decide whether to choose Context API
    - smallerApp: reactContext API
    - largerApp: Redux (better dev tooling)


# Redux
- What is the redux store?
- What are actions?
- What are action creators?
- What are reducers?
- How the control flows between these different parts 
- What exactly does the connect function do from the react-redux library? 
- What do mapStateToProps and mapDispatch ToProps actually do? 
- Why should you dispatch an action to update the state and not update store directly?
- In a reducer, why should you return a new object as state and not modify the existing state object?




```
{% endtab %}

{% tab title="Videos" %}
{% embed url="https://www.youtube.com/watch?v=tfPq0iCJioQ" %}
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

{% embed url="https://github.com/sudheerj/reactjs-interview-questions" %}

{% embed url="https://github.com/Pau1fitz/react-interview" %}





