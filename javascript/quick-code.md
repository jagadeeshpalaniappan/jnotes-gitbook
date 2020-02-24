# QUICK-CODE

## Sort Keys

{% tabs %}
{% tab title="1" %}
```javascript

var sortObjKeys = (obj) => Object.keys(obj)
	.sort()
	.reduce((res, key) => {
		const val = obj[key];
		res[key] = sortKeys(val);
		return res;
	}, {});

function sortKeys(item) {
	return typeof item === 'object' ? sortObjKeys(item) : item;
}

// copy(sortObjKeys(c1))
```
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

