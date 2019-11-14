# Web Performance \[TODO\]



{% tabs %}
{% tab title="" %}
1. Optimize: **CRP** \(Critical Rendering Path\)
2. Optimize: **Code**
   * Optimize: 'JavaScript Code' 
     * // `doNotBlockMainThread` : // `useSmallIndividualAsyncTasks` // `useWebWorker`
     * // `useDebounceOrThrottle` //`use:removeEventListener`
     * // `useForLoopLengthCached` // `useMemoizationCacheFnResults`
   * Optimize: 'DOM'
     * // `lazyLoadLessWantedDomElems` 
     * // `doBatchDomManipulation` //`useDocumentFragment`
   * Optimize: 'HTTP Response'
     * `cache` / `prefetch` / `loadOnDemandLessWanted`
{% endtab %}

{% tab title="1. Optimize: CRP" %}
**1.Optimize: CRP \(Critical Rendering Path\)**

**CRP:**   `[DOM Tree + CSSOM Tree + JS]`  &gt;&gt; Render Tree  &gt;&gt;  Layout  &gt;&gt; Paint

* Browser does Layout & Paint \(nothing much we can improve here\) 
* Optimize : Building the “Render Tree” To-do that, 
  * Optimize :: Building the DOM Tree & CSSOM Tree To-do that, 
    * Optimize :: Render-Blocking CSS and JavaScript

**1.1 Optimize: Render-Blocking CSS and JavaScript** 

```javascript
----------------------------------------------------------------------------------
## All these helps, reduces the blockingTime of 'DOM Tree & CSSOM Tree construction'
----------------------------------------------------------------------------------

1. Minimize 'noOfCriticalResources (CSS, JS)': // eliminate them or defer their download
    #why: loadOnlyReqdCriticalResources, becoz criticalResources are 'renderBlocking' 
    #how: lazyLoadOtherResources, 
        - use 'async': <script … async></script>
        - use 'defer': <script … defer></script>
        - use 'media': <link media="print" /or/ media="(min-width: 40em)” ..> 


2. Reduce HTML,CSS,JS Size
    #why: 'fasterDownload'
    #how: Use BuildTools: to (compress[gzip], minify, uglify, removeSpace&Comments)

3. Cache: 'criticalResources'

4. Use CDN (to load *HTML*,CSS,JS) - to reduce n/w latency
    #why: 'fasterDownload'
    #how: CDN fetches cachedFiles from nearby EdgeServers

5. PreFetch: 'criticalResources'

6.	Optimize the order in which the remaining critical resources are loaded: 

// Download all 'critical assets' as early as possible - to shorten the CRP length.

/* ------------------------------------------------------------------------ */
KeyWords:
#'criticalResources': (CSS, JS) which are renderBlocking // block CRP
#'renderBlocking': blocks the DOM Tree construction
#'CRP': Critical Render Path // [DOM Tree + CSSOM Tree + JS]  >> Render Tree  >>  Layout  >> Paint
#'fasterDownload': reduces, noOfRoundTrips to download the entireFile


```

\*\*\*\*

**script: 'default' vs 'async' vs 'defer'**

```markup
<!-- render-blocking -->
<script src="myscript.js"></script> 

<!-- no render-blocking // script will be executed as soon as it’s ready -->
<script src="myscript.js" async></script> 

<!-- no render-blocking // script will be executed after the DOM Tree construction (even if script ready earlier)-->
<script src="myscript.js" defer></script> <!-- // good -->

```

\*\*\*\*
{% endtab %}

{% tab title="2. Optimize: Code" %}
#### 1. Optimize: 'JavaScript Code'

```javascript
1. Optimize: 'Event Loop & Call Stack'
    - Do not 'blockMainThread', this will 'freezeUserInteraction' // remember: javascript is 'singleThreaded'
    - consider spliting 'longRunningSynchScripts' them into 'smallIndividualAsyncTasks' 
      // remember: Keeping `longRunningSynchScripts` in asynchronous tasks also 'blockMainThread'
    - or ask `WebWorker` to run the script parallelly

2. Optimize: 'Events'
     - Use: Debounce & Throttle 
     - Use: removeEventListener when we remove subscribed elements from DOM 

3. Use For… Loop (with Length Cached)
4. Use Memoize Fn (Cache the fn results)


/* ------------------------------- KeyWords: -------------------------------- */
# 'blockMainThread': longRunningSynchScripts - blocks the main thread
# 'longRunningSynchScripts': Long Running Synchronous Scripts
# 'freezeUserInteraction': blocking the CRP 

```

\*\*\*\*

#### **2. Optimize: DOM Manipulation**

```javascript
1. LazyLoad [less-wanted items]
    - when we have huge elements
    - consider first rendering elements which are in user viewport (and upcoming viewport)
    - then lazily load/render other elements (on-demand) when those element reaches close to the viewport
    // use: Intersection Observer API:
    
/* ----------------- Intersection Observer API: (example-code): -------------------- */
let options = { root: document.querySelector('#item1'), rootMargin: '0px', threshold: 1.0 }
let observer = new IntersectionObserver(callback, options);
```

```javascript
2. Optimize: DOM Manipulation
    use: 'documentFragment' while 'addOrRemoveMultipleItems'
    - consider append all the newChildElements to 'documentFragment' (dummyParentNode) // instead of adding each item to realParentNode
    - and then 'appendChild' or add that dummyParentNode only once to the 'parentElement'
    // remember: 'appendChild' to realDomElem is expensive // runs CRP


/* ------------------------------- KeyWords: -------------------------------- */
# 'documentFragment' is a dummyNode (Pseudo DOM Node or virtualElement) // no physical element created


/* ----------------- createDocumentFragment (example-code): -------------------- */
/* html: <ul id="list"></ul> */
// ## BAD apporach: ##
var listNode = document.querySelector('#list'); 
// Create 1000 list items, add to realDomNode
for(let i = 0; i < 1000; i++) { 
	var li = document.createElement("li"); li.innerText = "ListItem: " + i;
	listNode.appendChild(li); // 'render' happens multipleTimes (forEach nodeAddition) 
	// 'appendChild' to realDomNode is expensive operation
}

// ## GOOD apporach: ##
// create a docFragment 
var docFrag = document.createDocumentFragment(); // dummyVirtualNode
// Create 1000 list items, add to fragment
for(let i = 0; i < 1000; i++) { 
	var li = document.createElement("li"); li.innerText = "ListItem: " + i;
	docFrag.appendChild(li);
}
// BulkAdd: add all listItems at once (to the realDOM)
document.querySelector('#list').appendChild(docFrag); // 'render' happens only once

```



#### **3.**Optimize: 'HTTP Response'

```javascript
- Cache: HTTP response
- PreFetch: (most wanted) HTTP response
- Load `On-Demand` (less wanted) // LazyLoad
```
{% endtab %}

{% tab title="3. Memory Leak" %}


{% embed url="https://www.lambdatest.com/blog/eradicating-memory-leaks-in-javascript/" %}

{% embed url="https://dev.to/gc\_psk/debugging-memory-leaks-in-angular-4m2o" %}
{% endtab %}
{% endtabs %}



[https://github.com/jagadeeshpalaniappan/jnotes/blob/master/studies/js/ui-performance.pptx](https://github.com/jagadeeshpalaniappan/jnotes/blob/master/studies/js/ui-performance.pptx)

[https://github.com/jagadeeshpalaniappan/jnotes/blob/master/studies/js/2-webpage-load-optimization.docx](https://github.com/jagadeeshpalaniappan/jnotes/blob/master/studies/js/2-webpage-load-optimization.docx)



* We should send your long-running loops to the task queue
  * handle manually or use [async.js](http://caolan.github.io/async/)
* **Use:** setTimeout, Promise, requestAnimationFrame \(rAF\)
* **Use:** Debounce, Throttle, requestAnimationFrame \(for lagging issue\)





{% tabs %}
{% tab title="First Tab" %}


{% embed url="https://www.youtube.com/watch?v=sX7B4GghnqM&t=228s" %}
{% endtab %}

{% tab title="Second Tab" %}
{% embed url="https://www.youtube.com/watch?v=YJGCZCaIZkQ" %}
{% endtab %}
{% endtabs %}



