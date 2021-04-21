# Core Java \[TODO\]





{% tabs %}
{% tab title="Collections" %}
![](../.gitbook/assets/image%20%2835%29.png)
{% endtab %}

{% tab title="Second Tab" %}
**HashMap Vs TreeMap  Vs LinkedHashMap  :**

All three classes implement the Map interface

Differences:

* HashMap makes absolutely no guarantees about the iteration order. It can \(and will\) even change completely when new elements are added.
* TreeMap will iterate according to the "natural ordering" of the keys according to their compareTo\(\) method \(or an externally supplied Comparator\). Additionally, it implements the [SortedMap](http://java.sun.com/javase/6/docs/api/java/util/SortedMap.html) interface, which contains methods that depend on this sort order.· 
* LinkedHashMap will iterate in the order in which the entries were put into the map

["Hashtable"](http://en.wikipedia.org/wiki/Hashtable) is the generic name for hash-based maps. In the context of the Java API, Hashtable is an obsolete class from the days of Java 1.1 before the collections framework existed. It should not be used anymore, because its API is cluttered with obsolete methods that duplicate functionality, and its methods are synchronized \(which can decrease performance and is generally useless\). Use [ConcurrrentHashMap](http://docs.oracle.com/javase/7/docs/api/java/util/concurrent/ConcurrentHashMap.html) instead of Hashtable.
{% endtab %}
{% endtabs %}

