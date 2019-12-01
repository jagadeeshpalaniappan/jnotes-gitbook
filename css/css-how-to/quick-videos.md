# Quick Videos

## CSS

{% tabs %}
{% tab title="display" %}
```javascript

display: block | inline | inline-block | none | flex | ...
// display property specifies how an element is displayed

/*
Block Element: 
 - <div>, <p>, <h1>, <form>, <header>,... // by default 'display:block'
 - starts on a 'new line' and takes up the 'full width' available

Inline Elements:
 - <span>, <a>, <img> // by default 'display:block'
 - keeps item inline // does NOT start on a 'new line and only takes necessary width
 - we cannot add width, height, margin-top/bottom, padding-top/bottom // marginOrPadding-left/right possible 
 
 Inline Block Elements:
 - <button>, <textarea>, <input>, <select> // by default 'display:inline-block'
 - keeps item inline // simmilar to 'inline'
 - but it also supports width, height, all margin, all padding
*/

/*
display: flex // keeps child item flexible
// TODO
*/

```
{% endtab %}

{% tab title="position" %}
```javascript
position: *static* | relative | absolute | fixed | sticky
// how the elements are then positioned -using the top, bottom, left, right props

/*
static: (default)
 - always positioned according to the normal flow of the page
 - top, bottom, left, right props DOES NOT WORK

relative:
 - it positions the elements relatively to its current place
 - setting top:100px // keeps the element away from top 100px to its current context
 - Other content will not be adjusted to fit into any gap top by the element

absolute:
 - it positions the elements from the nearest positioned 'relative' ancestor
 - if no positioned 'relative' ancestor found // it positions the elements from the document body
 - setting top:100px // keeps the element away from top 100px from the nearest 'relative' ancestor
 

fixed:
- positioned relative to the viewport
- which means it always stays in the same place even if the page is scrolled


sticky: 
 - it toggles between relative and fixed, depending on the scroll position. 
 - It is positioned relative until a given offset position is met in the viewport 
 - then it "sticks" in place (like position:fixed)


*/
```
{% endtab %}

{% tab title="float" %}
```markup
float: left | right <!-- float: specifies how an element should float -->
clear: both | left | right <!-- specifies what elements can float beside the cleared element and on which side.-->

<!-- ############# 1: ############# -->
<style>
    aside { float: left; width: 30% }
    main { float: left; width: 70% }
</style>
<div>
    <aside>.........</aside>
    <main>....</main>
    <footer>...doesn't show proper place..</footer>
</div>

<!-- ########### 1: [Fixed] ########### -->
<style>
    aside { float: left; width: 30% }
    main { float: left; width: 70% }
    .clearfix { clear: both }
</style>
<div>
    <aside>.........</aside>
    <main>....</main>
    <div class="clearfix"></div>
    <footer>...doesn't show proper place..</footer>
</div>



<!-- ############# 2: ############# -->
<style>
    aside { float: left; width: 30%; padding: 10px; }
    main { float: left; width: 70%; padding: 20px;  }
</style>
<div>
    <aside>.........</aside>
    <main>....</main>
</div>

<!-- ########### 2: [Fixed] ########### -->
<style>
    aside { float: left; width: 30%; padding: 10px; box-sizing: border-box; }
    main { float: left; width: 70%; padding: 20px; box-sizing: border-box; }
</style>
<div>
    <aside>.........</aside>
    <main>....</main>
    <div class="clearfix"></div>
    <footer>...doesn't show proper place..</footer>
</div>

```
{% endtab %}
{% endtabs %}

## CSS Tutorial

{% tabs %}
{% tab title="First Tab" %}
{% embed url="https://www.youtube.com/watch?v=yfoY53QXEnI&feature=emb\_title" %}

​​​
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

​​



## CSS Position

{% tabs %}
{% tab title="First Tab" %}


{% embed url="https://www.youtube.com/watch?v=NzjU1GmKosQ" caption="" %}
{% endtab %}

{% tab title="Second Tab" %}


{% embed url="https://www.youtube.com/watch?v=-vo0HzNHL3U" caption="" %}
{% endtab %}
{% endtabs %}





## CSS Display

{% tabs %}
{% tab title="First Tab" %}


{% embed url="https://www.youtube.com/watch?v=YS2bTVYBoK8" caption="" %}
{% endtab %}

{% tab title="Second Tab" %}


{% embed url="https://www.youtube.com/watch?v=fYq5PXgSsbE" caption="" %}
{% endtab %}
{% endtabs %}

CSS Flexbox

{% tabs %}
{% tab title="First Tab" %}
{% embed url="https://www.youtube.com/watch?v=fqNPSSoMO9Y" %}
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

## CSS Transition

{% tabs %}
{% tab title="First Tab" %}

{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

## [https://zellwk.com/blog/9-important-css-properties-you-must-know/](https://zellwk.com/blog/9-important-css-properties-you-must-know/)

## 

## 

