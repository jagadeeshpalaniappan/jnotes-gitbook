# React Synthetic Events



* `Synthetic Events` are delegated to `document` node. 
* Therefore **'native events' are triggered first** and the events bubble up to document, after which the synthetic events are triggered.

{% tabs %}
{% tab title="Example Code" %}
```jsx




import React, { useEffect } from "react";
import ReactDOM from "react-dom";

// Component: App
function App() {
  useEffect(() => {
    // #2: NativEvent: on 'parentDiv' click
    const parentDiv = document.getElementById("parent");
    parentDiv.addEventListener("click", (e) => {
      // e.stopPropagation(); // it will stop here, doesnt execute '#3'
      console.log("#2: [parent div] native dom event triggered");
    });

    // #1: NativEvent: on 'childBtn' click
    const childBtn = document.getElementById("child");
    childBtn.addEventListener("click", (e) => {
      // e.stopPropagation();  // it will stop here, doesnt execute '#2'
      console.log("#1: [child button] native dom event triggered");
    });
  }, []);

  // #4: SyntheticEvent: on 'parentDiv' click
  const onParentClick = (e) => {
    // e.stopPropagation(); // it will stop here, doesnt execute '#5'
    console.log("#4: [parent div] synthetic event triggered");
  };

  // #3: SyntheticEvent: on 'button' click
  const onChildClick = (e) => {
    // e.stopPropagation(); // it will stop here, doesnt execute '#4'
    console.log("#3: [child button] synthetic event triggered");
  };

  return (
    <div id="parent" onClick={onParentClick} style={{ border: "1px solid" }}>
      <button id="child" onClick={onChildClick}>
        child
      </button>
    </div>
  );
}

// #5: NativEvent: on 'document' click
document.addEventListener("click", (e) => {
  // e.stopPropagation();
  console.log("#5: [document] native dom event triggered");
});

// #3: NativEvent: on 'rootDiv' click
const rootDiv = document.getElementById("root");
rootDiv.addEventListener("click", (e) => {
  // e.stopPropagation();
  console.log("#3: [root div] native dom event triggered");
});

ReactDOM.render(<App />, rootDiv);

```
{% endtab %}

{% tab title="Output \(Execution Order\)" %}
```javascript
/*

If user 'clicks' childBtn, execution order in 'React 17'

#1: [child button] native dom event triggered 
#2: [parent div] native dom event triggered 
#3: [root div] native dom event triggered 
#3: [child button] synthetic event triggered 
#4: [parent div] synthetic event triggered 
#5: [document] native dom event triggered     #####


If user 'clicks' childBtn, execution order in 'React 16x'

#1: [child button] native dom event triggered 
#2: [parent div] native dom event triggered 
#3: [root div] native dom event triggered 
#5: [document] native dom event triggered     #####
#3: [child button] synthetic event triggered 
#4: [parent div] synthetic event triggered 

*/
```



[https://reactjs.org/blog/2020/10/20/react-v17.html\#changes-to-event-delegation](https://reactjs.org/blog/2020/10/20/react-v17.html#changes-to-event-delegation)

![](../../../.gitbook/assets/image%20%2833%29.png)
{% endtab %}
{% endtabs %}





