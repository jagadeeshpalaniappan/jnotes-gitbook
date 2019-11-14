# Sass

## Quick Intro

{% tabs %}
{% tab title="Sass" %}
```css
/* --------------------Import Other Stylesheets-------------------- */
// @import 'partials/_fileName1';
// @import 'partials/_fileName2';

/* -------------------- Variable-------------------- */
$myColorVariable: #46EAC2;
a {
  color: $myColorVariable;
}

/* --------------------Interpolation-------------------- */
$wkAlias: -webkit-;
.item {
  #{$wkAlias}border-radius: 4px;
}

/* --------------------Nesting-------------------- */
.list {
  list-style-type: none;
  .list-item {
    color: black;
    &:hover {
      color: red;
    }

    &--active {
      color: blue;
    }
  }
}

/* --------------------Inheritance-------------------- */
.error {
  background: black;
  color: red;
}

.specialError {
  @extend .error;
  background: yellow;
}

/* --------------------Mixins (Custom Functions)-------------------- */
@mixin getDefaultBox($padding, $color) {
  padding: 5px $padding;

  $myLocalVariable: $color;
  border: 1px solid $myLocalVariable;
}

header {
  @include getDefaultBox(2px, #666);
}

footer {
  @include getDefaultBox(10px, #999);
}

/* --------------------Functions (Built-In Functions)-------------------- */
/* TODO */

```
{% endtab %}

{% tab title="CSS" %}
```css
/* --------------------Import Other Stylesheets-------------------- */
/*
    ....... imported css content goes here ....
*/

/* --------------------Import Other Stylesheets-------------------- */
/* -------------------- Variable-------------------- */
a {
  color: #46EAC2;
}

/* --------------------Interpolation-------------------- */
.item {
  -webkit-border-radius: 4px;
}

/* --------------------Nesting-------------------- */
.list {
  list-style-type: none;
}
.list .list-item {
  color: black;
}
.list .list-item:hover {
  color: red;
}
.list .list-item--active {
  color: blue;
}

/* --------------------Inheritance-------------------- */
.error, .specialError {
  background: black;
  color: red;
}

.specialError {
  background: yellow;
}

/* --------------------Mixins (Custom Functions)-------------------- */
header {
  padding: 5px 2px;
  border: 1px solid #666;
}

footer {
  padding: 5px 10px;
  border: 1px solid #999;
}

/* --------------------Functions (Built-In Functions)-------------------- */
```
{% endtab %}
{% endtabs %}



{% embed url="https://sass-cheatsheet.brunoscopelliti.com/" %}

{% embed url="https://devhints.io/sass" %}



Sass Functions \(Built-In Functions\)

* [https://sass-lang.com/documentation/modules](https://sass-lang.com/documentation/modules)

