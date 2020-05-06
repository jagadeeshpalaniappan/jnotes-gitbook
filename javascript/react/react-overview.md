# Quick: React Overview

## React LifeCycle

{% tabs %}
{% tab title="Quick" %}
```csharp

----------------------------------- Keywords -----------------------------------

# Class Component

# Functional Component

----------
# Smart Component
- has a state

# Dump Component
- doesn't have a state

----------
# Container vs Component

# Container

# Component
----------
    
# Higher Order Components vs Mixins

# Higher Order Components (HOCs) vs Render Props vs Hooks

// https://medium.com/simply/comparison-hocs-vs-render-props-vs-hooks-55f9ffcd5dc6
```
{% endtab %}

{% tab title="Old" %}
![](../../.gitbook/assets/image-191.png)
{% endtab %}

{% tab title="Old vs New LifeCycle" %}
![](../../.gitbook/assets/image-37.png)

![](../../.gitbook/assets/image-21.png)

| Methods Deprecated in 16.4 | New Methods introduced in 16.4 |
| :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">
        <ol>
          <li>component<b>WillMount</b>()</li>
          <li>component<b>WillReceiveProps</b>()</li>
          <li>component<b>WillUpdate</b>()</li>
        </ol>
      </th>
      <th style="text-align:left">
        <ol>
          <li>getDerivedStateFromProps()</li>
          <li>getSnapshotBeforeUpdate()</li>
        </ol>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>### Aliases Methods

1. ~~**componentWillMount**\(\)~~ **→**  UNSAFE\_componentWillMount\(\)
2. ~~**componentWillReceiveProps**\(\)~~ **→**  UNSAFE\_componentWillReceiveProps\(\)
3. ~~**componentWillUpdate**\(\)~~ **→** UNSAFE\_componentWillUpdate\(\)
4. React 16.3 All old methods, aliases and new lifecycle will work.
5. React 16.4 All old methods, aliases and new lifecycle will work, 
   * but old methods will give deprecation warning in dev mode.
6. **React 17.0** Only aliases and new lifecycle will work.
{% endtab %}

{% tab title="Migration" %}
1.component**WillMount** ---&gt; **\*\*component**DidMount\*\*

![just a name change](../../.gitbook/assets/image-25.png)

2.component**WillReceieveProps** ---&gt; **get**Derived**State**FromProps

![since newFn is static &apos;this&apos; is not accessible \(i.e. this.state.xxxx\)](../../.gitbook/assets/image-172.png)

3.component**WillUpdate** ---&gt; **getSnapshot**BeforeUpdate

* whatever **getSnapshotBeforeUpdate** fn returns 
* we can get that `snapshot` value in **componentDidUpdate** fn as a 3rd arg

![](../../.gitbook/assets/image-47.png)
{% endtab %}
{% endtabs %}

## React Code Styles

{% tabs %}
{% tab title="ES6+ \(class\)" %}
![](../../.gitbook/assets/image-107.png)
{% endtab %}

{% tab title="Binding \'this\'" %}
![](../../.gitbook/assets/image-56.png)
{% endtab %}
{% endtabs %}



