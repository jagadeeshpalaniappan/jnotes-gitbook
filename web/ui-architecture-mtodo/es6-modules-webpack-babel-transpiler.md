# ES6 Modules, Webpack, Babel, Transpiler

## ES6 Modules:

{% tabs %}
{% tab title="0.Detailed" %}
* [https://www.valentinog.com/blog/es-modules/](https://www.valentinog.com/blog/es-modules/) `****`
* [https://javascript.info/modules-intro](https://javascript.info/modules-intro) `****`
{% endtab %}

{% tab title="1.Intro" %}
**From ES6, Javascript natively supports "modules"**

* Browser
* Node.js \(from v12.17.0 - with no extra flag\)

**Why?** 

* Initially scripts were small and simple, so there was no need for modules.
* Now with SPA, scripts became more and more complex
* As our application grows bigger, complexity increases
  * we want to modularize the code
  * we want to split it into multiple files,
  * split class/functions/variables for a specific purpose

**How did we use "modules" - before ES6**

* JavaScript community has invented a variety of ways to organize code into modules
  * [AMD](https://en.wikipedia.org/wiki/Asynchronous_module_definition) \(Ancient Module Systems\) // initially implemented by the library [require.js](http://requirejs.org/).
  * [CommonJS](http://wiki.commonjs.org/wiki/Modules/1.1) // the module system created for Node.js server
  * [UMD](https://github.com/umdjs/umd) – universal one, compatible with AMD and CommonJS
* There had been a lot of attempts to standardize this aspect

**What is a module?**

* A module is just a file. One script is one module. As simple as that.
* Modules can load each other and use special directives `export` and `import` to interchange functionality, call functions of one module from another one:
  * `export` keyword labels variables and functions that should be accessible from outside the current module.
  * `import` allows the import of functionality from other modules.

\*\*\*\*
{% endtab %}

{% tab title="2. Example Code" %}
## How to import 'ES6 Modules'

```javascript
// utils.js
export function funcA() {
  return "Hello named export!";
}

export default function funcB() {
  return "Hello default export!";
}
```

```javascript
// consumer.js
import { funcA } from "./util.js";
import funcB from "./util.js";
funcA();
funcB();

// or
// consumer.js
import funcB, { funcA } from "./util.js";
funcA();
funcB();


// or
// consumer.js
import * as myModule from "./util.js";
myModule.funcA();
myModule.default();
```

## How to import 'Dynamic Modules'

* ES modules are static, meaning we cannot change imports at runtime. 
* Dynamic imports, landed in 2020, we can dynamically load our code in response to user interactions 
* \(webpack offered dynamic imports long before this feature shipped in ECMAScript 2020\).

```javascript
// <script src="main.js"></script>

// main.js


// Dynamic Import: (JS File)
const btn1 = document.getElementById("btn1");

btn1.addEventListener("click", () => {

  // import 'utils.js' only after 'user clicks - btn1'
  import("./util.js").then((module) => {
    module.funcA();
    module.default();
  });
  
});



// Dynamic Import: (JSON File)

// user.json // { "name": "Jules", "age": 43 }

const btn2 = document.getElementById("btn1");

btn2.addEventListener("click", () => {

  // import 'user.json' only after 'user clicks - btn2'
  import("./user.json").then((module) => {
    const { name, age } = module.default;
    console.log(name, age);
  });
  
});


```
{% endtab %}

{% tab title="3.Module Features" %}
**Module features**

* Module-level scope // each module has its own scope
* A module code is evaluated only the first time when imported // singleton
* In a module, “**this**” is undefined
* Always “**use strict”**
* import.meta



**Module-level scope**

* we cannot access `user` variable in other module

```markup
<!DOCTYPE html>
<html lang="en">
<head>...</head>
<body>...</body>

<script type="module">
  // The variable is only visible in this module script
  let user = "John";
</script>

<script type="module">
  alert(user); // Error: user is not defined
</script>

</html>
```

* only if the module exports user, we can use it in other module.

```markup
<!DOCTYPE html>
<html lang="en">
<head>...</head>
<body>...</body>

<script type="module">
  export let user = "John";
</script>

<script type="module">
  import {user} from './user.js';
  document.body.innerHTML = user; // John
</script>

</html>
```

----



...

```text
import { createStore } from "https://unpkg.com/redux@4.0.5/es/redux.mjs";
const store = createStore(/* do stuff */)
```
{% endtab %}

{% tab title="4.Browser-specific features" %}
**Browser-specific features**

* Module scripts are deferred
* Async works on inline scripts
* External scripts
* No “bare” modules allowed
* Compatibility, “nomodule”



**External scripts**

```text
import { createStore } from "https://unpkg.com/redux@4.0.5/es/redux.mjs";
const store = createStore(/* do stuff */)
```
{% endtab %}
{% endtabs %}



## Webpack:

{% tabs %}
{% tab title="First Tab" %}
* [https://www.valentinog.com/blog/webpack/\#should-you-learn-webpack](https://www.valentinog.com/blog/webpack/#should-you-learn-webpack)
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

## Babel:

{% tabs %}
{% tab title="First Tab" %}
* ....
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

## Polyfills

{% tabs %}
{% tab title="First Tab" %}

{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

## Create Custom 'create-react-app'

{% tabs %}
{% tab title="" %}
{% embed url="https://www.youtube.com/watch?v=dOU4FBNVnl8" %}
{% endtab %}

{% tab title="First Tab" %}
* Why do we need a module bundler like Webpack? 
  * Because some people still use older browsers that don't support ES6 modules \(e.g. IE11\), and because HTTP/2 is yet to fully replace HTTP 1.1. - 
* Why do we need a transpiler like Babel? 
  * For cross-browser support, because older browsers don't support ES6+ features natively. 
* Why do we need a source map? 
  * Because it's very hard to debug `minified`, `uglified`, and `transpiled` code. 
  * To fix a bug in production, you need to trace it back to its original source.
* Why not create-react-app? 
  * If you need to change a small setting, are you comfortable ejecting and sifting through its 100s LOC config? 
  * It's worthwhile to bootstrap the workspace yourself so you can tailor it towards your app.
{% endtab %}

{% tab title="More" %}
* Modern JavaScript Explained For Dinosaurs
  * [https://medium.com/the-node-js-collection/modern-javascript-explained-for-dinosaurs-f695e9747b70](https://medium.com/the-node-js-collection/modern-javascript-explained-for-dinosaurs-f695e9747b70)
* Webpack:
  * [https://www.valentinog.com/blog/webpack/](https://www.valentinog.com/blog/webpack/)
  * [https://www.freecodecamp.org/news/javascript-modules-part-2-module-bundling-5020383cf306/](https://www.freecodecamp.org/news/javascript-modules-part-2-module-bundling-5020383cf306/)
* TC39:
  * [https://2ality.com/2015/11/tc39-process.html](https://2ality.com/2015/11/tc39-process.html)
{% endtab %}
{% endtabs %}

