# Web Accessibility \[TODO\]

Web Accessible Applications \(using guidelines from ADA Section 508 and WCAG\)



{% tabs %}
{% tab title="1" %}
![](../.gitbook/assets/image%20%2829%29.png)
{% endtab %}

{% tab title="2" %}

{% endtab %}

{% tab title="" %}
![](../.gitbook/assets/image%20%28141%29.png)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="A11y" %}
* [https://www.youtube.com/watch?v=z8xUCzToff8](https://www.youtube.com/watch?v=z8xUCzToff8)
* [https://www.youtube.com/watch?v=EFv9ubbZLKw&list=PLNYkxOF6rcICWx0C9LVWWVqvHlYJyqw7g&index=3](https://www.youtube.com/watch?v=EFv9ubbZLKw&list=PLNYkxOF6rcICWx0C9LVWWVqvHlYJyqw7g&index=3)

Full Course:

* [https://classroom.udacity.com/courses/ud891](https://classroom.udacity.com/courses/ud891)



```javascript
1. Use: 'Tab / Shift Tab' (navigate to different focus element)
2. Use 'DownArrow / UpArrow' to select appropriate item 
    - Dropdown, SideNav

3. For 'color-blindness' ppl, instead of colors use 'differnt patterns' // squares, traingles, circles pattern design to differentiate
```
{% endtab %}

{% tab title="" %}

{% endtab %}

{% tab title="First Tab" %}
```javascript
// Focus:
------------
Use: Native 'Tab Order'
    - input, select, button // bydefault (focusable)
    - h1, p, span, label // textNode (not-focusable) 
    // becoz screenreader, just reads those text and moves on
    // But, for 'input, select, button...' screenreader needs to wait for User Action
    // enterTextInInputField or selectItemFromDropDown or clickBtn


// Use: 'Native Tab Order' (as much as possible)
-------------------------------------------------

Problem:
<div>
    <button style="float:right">1</button>
    <button>2</button>
    <button>3</button>
</div>
// visually  // [  2  ]    [  3  ]    [  1  ]  
// but screenreader reads 1, 2, 3


// --- Fix for this is, ---
<div>
    <button>2</button>
    <button>3</button>
    <button style="float:right">1</button>
</div>

// visually  // [  2  ]    [  3  ]    [  1  ]  
// screenreader also reads 2, 3, 1

```



```javascript
How do you make the 'Non-Focusable Ele' --> 'Focusable' ?
Ans: Add 'tabindex' attribute to the ele // Not eleIsFocusable using Tab // also we can use JavaScript to $ele.focus()


<div tabindex="0"> 1 </div>
<div tabindex="0"> 2 </div>
<div tabindex="0"> 3 </div>
<div tabindex="-1"> skipThisInTabNavigation butFocuableUsingJS </div>
<div tabindex="5"> AlwaysFirst </div> // NOT-RECOMMENDED

// TabOrder: AlwaysFirst --> 1 --> 2 --> 3

// tabindex="0" // canMakeTheEle: focusable (using Tab) or (using JS)
// tabindex="-1" // canMakeTheEle: focusable (only using JS) // (can not use Tab for focus)

// Note: 'tabindex= >0' not recommended to use // very hard to manage different components in whole page
```

```javascript
3. Use: appropriate HTML Semantics (as much possible)

E.g: For 'Button' // use: <button> insteadOf: <div class="btn">CustomBtn</div>

// Native Button vs Custom Div Button
// Native Button:
- NativeTabOrder
- To click SpaceBarOrEnterBtn will work natively
- `disabled` attribute 'blocks the click behavior' and will not be 'focused'

// Custom Div Button
- CustomTabOrder // by using tabindex=0
- Need to add key-listener (and listen for SpaceBarOrEnterBtn click)
- `disabled` attribute will not block the click behavior and will be 'focused'

```



```javascript
...
```
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

