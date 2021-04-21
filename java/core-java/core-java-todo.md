# Collections \[TODO\]



{% tabs %}
{% tab title="Collections" %}
![](../../.gitbook/assets/image%20%2835%29.png)
{% endtab %}

{% tab title="HashMap\*\*\*" %}
{% embed url="https://www.youtube.com/watch?v=c3RVW3KGIIE" %}
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

{% tab title="" %}

{% endtab %}
{% endtabs %}

  
  


<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>ArrayList</b>
      </th>
      <th style="text-align:left"><b>Vector</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">ArrayList is not synchronized.</td>
      <td style="text-align:left">Vector is synchronized.</td>
    </tr>
    <tr>
      <td style="text-align:left">ArrayList is not a legacy class.</td>
      <td style="text-align:left">
        <p>Vector is a legacy class.</p>
        <p>- legacy means &#x2013;before java 1.5</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p>ArrayList increases its size by 50% of the array size.</p>
        <p>If array size is 1kb &#xE0; ArrayList size will be 1.5kb</p>
      </td>
      <td style="text-align:left">
        <p>Vector increases its size by doubling the array size.</p>
        <p>If array size is 1kb &#xE0; Vector size will be 2kb</p>
      </td>
    </tr>
  </tbody>
</table>

  


<table>
  <thead>
    <tr>
      <th style="text-align:left">ArrayList</th>
      <th style="text-align:left">LinkedList</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">ArrayList uses a &#x201C;dynamic array&#x201D;</td>
      <td style="text-align:left">LinkedList uses &#x201C;doubly linked list&#x201D;</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p>ArrayList is NOT efficient for manipulation</p>
        <p>Because a lot of shifting is required.</p>
        <p>(Traversing is NOT easy)</p>
      </td>
      <td style="text-align:left">
        <p>LinkedList is efficient for manipulation.</p>
        <p>(Traversing is easy)</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">ArrayList is better to store and fetch data.</td>
      <td style="text-align:left">LinkedList is better to manipulate data.</td>
    </tr>
  </tbody>
</table>



#### What is the difference between List and Set?

* List can contain duplicate elements whereas
* Set contains only unique elements. 

#### Difference between HashSet and TreeSet?

* HashSet maintains no order
* TreeSet maintains ascending order 

#### Difference between Set and Map?

* Set contains values only
* Map contains key and values both. 

#### Difference between HashMap and Hashtable?

* HashMap
  * -is not synchronized
  * -can contain one null key and multiple null values.
* Hashtable
  * -is synchronized
  * -cannot contain any null key or null value. 

#### Difference between Collection and Collections?

* Collection --is an interface
  * Collection interface provides normal functionality of data structure to List, Set and Queue. 
* Collections --is a class. 
  * But, Collections class is to sort and synchronize --collection elements.







<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Comparable</b>
      </th>
      <th style="text-align:left"><b>Comparator</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p>o compareTo(Object o)</p>
        <p>o If we have a source file to modify the content</p>
      </td>
      <td style="text-align:left">
        <p>o compare(Object o1, Object o2)</p>
        <p>o If we do not have access to source file to modify the content</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Comparable provides only one sort of sequence.</td>
      <td style="text-align:left">Comparator provides multiple sort of sequences.</td>
    </tr>
    <tr>
      <td style="text-align:left">It is in java.lang package.</td>
      <td style="text-align:left">It is in java.util package.</td>
    </tr>
    <tr>
      <td style="text-align:left">If we implement Comparable interface, actual class is modified.</td>
      <td
      style="text-align:left">Actual class is not modified.</td>
    </tr>
  </tbody>
</table>



#### Why we override equals\(\) method?

```java
class Emp{
	
	private String empId;
	private String empName;
	
	@Override
	public boolean equals(Object obj) {
		boolean flag =false;
		
		if(obj instanceof Emp){
			Emp e = (Emp)obj;
			
			if(this.empName.equals(e.empName)){
				flag = true;
			}
			
		}
		
		return flag;
	}

	//Getters & Setters
}



public class EqualsExample {
	
	public static void main(String[] args) {
		
		Emp e1 = new Emp(); 
		e1.setEmpName("jagan");
		
		Emp e2 = new Emp(); 
		e2.setEmpName("jagan");
		
		if(e1.equals(e2)){
			System.out.println("e1-Emp name & e2-Emp names are same");
		}
	}

}

```

#### How to synchronize List, Set and Map elements? 

Yes, Collections class provides methods to make List, Set or Map elements as synchronized:

```java
- Collections.synchronizedList(List l){} 
- Collections.synchronizedSet(Set s){} 
- Collections.synchronizedSortedSet(SortedSet s){} 
- Collections.synchronizedMap(Map m){} 
- Collections.synchronizedSortedMap(SortedMap m){}
```

#### What is the advantage of generic collection?

* If we use generic class, we don't need typecasting.  It is “typesafe“ and “checked at compile time”. 

#### What is hash-collision in Hashtable and how it is handled in Java?

* Two different keys --with the same hash value \(are known as hash-collision.\)
* Two different entries will be kept in a  “single hash bucket” --to avoid the collision.

#### What is the Dictionary class?

* The Dictionary class provides the capability to store key-value pairs. 

#### What is the default size of “load factor” in hashing based collection?

* The default size of load factor is 0.75.
* The default capacity is computed as initial capacity  _load factor._
* _For example, 16_  0.75 = 12
* So, 12 is the default capacity of Map. 
* “Based on Load Factor only – Collections increases the size” 

#### Collections --SORTING--



