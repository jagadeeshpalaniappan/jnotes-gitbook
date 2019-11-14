# React Overview

## React LifeCycle

{% tabs %}
{% tab title="Old" %}
![](../../.gitbook/assets/image%20%28191%29.png)
{% endtab %}

{% tab title="Old vs New LifeCycle" %}
![](../../.gitbook/assets/image%20%2837%29.png)

![](../../.gitbook/assets/image%20%2821%29.png)

<table>
  <thead>
    <tr>
      <th style="text-align:left">Methods Deprecated in 16.4</th>
      <th style="text-align:left">New Methods introduced in 16.4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p></p>
        <ol>
          <li>component<b>WillMount</b>()</li>
          <li>component<b>WillReceiveProps</b>()</li>
          <li>component<b>WillUpdate</b>()</li>
        </ol>
      </td>
      <td style="text-align:left">
        <p></p>
        <ol>
          <li>getDerivedStateFromProps()</li>
          <li>getSnapshotBeforeUpdate()</li>
        </ol>
      </td>
    </tr>
  </tbody>
</table>Methods which are deprecated are provided with aliases methods for smooth updated.

#### Aliases Methods

1. ~~**componentWillMount**\(\)~~ **→**  UNSAFE\_componentWillMount\(\)
2. ~~**componentWillReceiveProps**\(\)~~ **→**  UNSAFE\_componentWillReceiveProps\(\)
3. ~~**componentWillUpdate**\(\)~~ **→**  UNSAFE\_componentWillUpdate\(\)

* React 16.3 All old methods, aliases and new lifecycle will work.
* React 16.4 All old methods, aliases and new lifecycle will work, 
  * but old methods will give deprecation warning in dev mode.
* **React 17.0** Only aliases and new lifecycle will work.
{% endtab %}

{% tab title="Migration" %}
1.component**WillMount** ---&gt; ****component**DidMount**

![just a name change](../../.gitbook/assets/image%20%2825%29.png)

2.component**WillReceieveProps** ---&gt; **get**Derived**State**FromProps

![since newFn  is static &apos;this&apos; is not accessible \(i.e. this.state.xxxx\)](../../.gitbook/assets/image%20%28172%29.png)

3.component**WillUpdate** ---&gt; **getSnapshot**BeforeUpdate

* whatever **getSnapshotBeforeUpdate** fn returns 
* we can get that `snapshot` value in **componentDidUpdate** fn as a 3rd arg

![](../../.gitbook/assets/image%20%2847%29.png)
{% endtab %}
{% endtabs %}



## React Code Styles

{% tabs %}
{% tab title="ES6+ \(class\)" %}
![](../../.gitbook/assets/image%20%28107%29.png)
{% endtab %}

{% tab title="Binding \'this\'" %}
![](../../.gitbook/assets/image%20%2856%29.png)
{% endtab %}
{% endtabs %}

