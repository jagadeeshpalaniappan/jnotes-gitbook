# React Performance

{% tabs %}
{% tab title="1" %}
![](../../../.gitbook/assets/image-8.png)
{% endtab %}

{% tab title="shouldComponentUpdate" %}
### shouldComponentUpdate

![](../../../.gitbook/assets/image-119.png)

![](../../../.gitbook/assets/image-92.png)

![](../../../.gitbook/assets/image-82.png)

![](../../../.gitbook/assets/image-124.png)
{% endtab %}

{% tab title="shouldComponentUpdate \(in hooks\)" %}
#### How do I implement `shouldComponentUpdate`? <a id="how-do-i-implement-shouldcomponentupdate"></a>

You can wrap a function component with `React.memo` to shallowly compare its props:

```text
const Button = React.memo((props) => {
  // your component
});
```

It’s not a Hook because it doesn’t compose like Hooks do. `React.memo` is equivalent to `PureComponent`, but it only compares props. \(You can also add a second argument to specify a custom comparison function that takes the old and new props. If it returns true, the update is skipped.\)

`React.memo` doesn’t compare state because there is no single state object to compare. But you can make children pure too, or even [optimize individual children with `useMemo`](https://reactjs.org/docs/hooks-faq.html#how-to-memoize-calculations).

####  <a id="how-to-memoize-calculations"></a>
{% endtab %}
{% endtabs %}

## React Scalability

{% tabs %}

{% embed url="https://vimeo.com/168648012" caption="" %}

![](../../../.gitbook/assets/image-1.png)

![](../../../.gitbook/assets/image-10.png)

![](../../../.gitbook/assets/image-154.png)

![](../../../.gitbook/assets/image-203.png)

![](../../../.gitbook/assets/image-2.png)

![](../../../.gitbook/assets/image-169.png)

![](../../../.gitbook/assets/image-19.png)

