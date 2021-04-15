# React Synthetic Events



* `Synthetic Events` are delegated to `document` node. 
* Therefore **'native events' are triggered first** and the events bubble up to document, after which the synthetic events are triggered.

{% tabs %}
{% tab title="Example Code" %}
```jsx

/*

If user 'clicks' childBtn, execution order:

#1: [child button] native dom event triggered 
#2: [parent div] native dom event triggered 
#3: [child button] synthetic event triggered 
#4: [parent div] synthetic event triggered 
#5: [document] native dom event triggered 

*/



function App() {

  useEffect(() => {
    // #5: NativEvent: on 'document' click
    document.addEventListener("click", (e) => {
      e.stopPropagation();
      console.log("#5: [document] native dom event triggered");
    });

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
```
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

