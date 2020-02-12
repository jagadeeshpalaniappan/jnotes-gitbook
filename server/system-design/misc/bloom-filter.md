# Bloom Filter

{% tabs %}
{% tab title="Video" %}
{% embed url="https://www.youtube.com/watch?v=Bay3X9PAX5k" %}

* [https://www.youtube.com/watch?v=bgzUdBVr5tE](https://www.youtube.com/watch?v=bgzUdBVr5tE)
* [https://www.youtube.com/watch?v=RSwjdlTp108](https://www.youtube.com/watch?v=RSwjdlTp108)
{% endtab %}

{% tab title="Intro" %}
```fsharp
# Bloom Filter (BF)


Bloom filter,
    - superFastSearch to say item 'PRESENT' or 'NOT-PRESENT' in set
    - it stores very-very-less-data  //memory-efficient // BitArray ---> DecimalNumber (base10)
    - Cons: It gurantees only 'NOT-PRESENT'


Thatsy BF is a probabilistic data structure,
Ask Bloom filter, 'str1' present in Set or Not?
    - maybe present (confidenceLevel: 50%) // NOT-GUARANTEED
    - not-present (confidenceLevel: 100%) // GUARANTEED // if we find any one zero that means that str is not added in the set


# UseCases:
    - DB: Postgres, Cassandra, HBase using Bloom filters 
        - to check particular 'ID' is present in Bloom filter
        - if 'not-present' they do not spend time searching // GUARANTEED 
        - if 'present' they try spend time searching and may or may not find record // NOT-GUARANTEED

    - GoogleChrome: check the 'newUrl' - is NOT mallicous
    - Medium.com: maintains eachUser 'suggestedArticle' is NOT visited

Why NOT HashMap or HashTable?
    - HashTable lookup is not always O(1) //avg
    - If more data and 'hashCollision' happens, it might have to search all items in that bucket
    - Also HashMap has to store all the data
```
{% endtab %}

{% tab title="More.." %}
```fsharp

https://www.youtube.com/watch?v=bgzUdBVr5tE


often we have to 'compare entire string with another string'

there are other data structures around strings which are,
    1. Tries 
    2. Suffix Trees
    3. Hashing

Lets say 'tries' or 'suffix trees' its not easy to actually optimize them for any given problem 
so even though they have really good theoretical complexity 
in practical scenario their complexity is not that great

so in practice, 
    - 'hashing' is one of the best approach for comparing a lot of strings


- we dont want to store the entire string instead we want to store the hash of these strings
- so that the comparison is efficient

```
1. Store 'str1' hashCodes:
    - str1HashCode = hashFn(str1)
2. when we want to compare 'str1' with 'str2',
    - str2HashCode = hashFn(str2)
3. Compare str1HashCodes with str2HashCodes
    - str1HashCode === str2HashCode
        - single number comparison
        - TC: O(m+n) m: str1Length, n: str2Length
```

    
# Then, why dont we just use 'HashMap'? 
    - In some cases, HashMap might not have enough bucket range required to store that many
strings
    - HashMap: 0 --to--> bucketSize  // bucketSize is not enough

# To avoid this, 'Store muliple hashCode of a string'

1. Store 'str1' hashCodes:
    - str1HashCode1 = hashFn1(str1), str1HashCode2 = hashFn2(str1), str1HashCode3 = hashFn3(str1);
    - store: [str1HashCode1, str1HashCode2, str1HashCode3]

2. when we want to compare 'str1' with 'str2',
    - str2HashCode1 = hashFn1(str2), str2HashCode2 = hashFn2(str2), str2HashCode3 = hashFn3(str2);
    - populateHash: [str2HashCode1, str2HashCode2, str2HashCode3]

3. Compare str1HashCodes with str2HashCodes
    - (str1HashCode1 === str2HashCode1) && (str1HashCode2 === str2HashCode2) && (str1HashCode3 === str2HashCode3)  

- there is a very high probability that different 'str3' can bring the same 3 hashCodes

This is the general concept of 'bloom filters'
```
{% endtab %}

{% tab title="Example" %}
```fsharp

BF: bitArray

  0   1   2   3   4   5   6   7   8   9  10  11  12  13  14  15  16  18 ....
 _______________________________________________________________________
| 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |......
 -----------------------------------------------------------------------

1. Add: 'cat' in BF
--------------------
str1= 'cat'
str1HashCode1 = hashFn1(str1) // 2
str1HashCode2 = hashFn2(str1) // 6
str1HashCode3 = hashFn3(str1) // 5

bitArray[2] // 0 // that means notPresent in BF // checking anyOne is not present is fine //GUARANTEED


  0   1  *2   3   4  *5  *6   7   8   9  10  11  12  13  14  15  16  18 ....
 _______________________________________________________________________
| 0 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |......
 -----------------------------------------------------------------------


2. Add: 'dog' in BF
--------------------
str2= 'dog'
str2HashCode1 = hashFn1(str2) // 4
str2HashCode2 = hashFn2(str2) // 10
str2HashCode3 = hashFn3(str2) // 15

bitArray[4] // 0 // that means notPresent in BF // checking anyOne is not present is fine //GUARANTEED


  0   1   2   3  *4   5   6   7   8   9  *10  11  12  13  14 *15  16  18 ....
 _______________________________________________________________________
| 0 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 0 |......
 -----------------------------------------------------------------------



3. Check: 'cat' in BF
--------------------
str3= 'cat'
str3HashCode1 = hashFn1(str3) // 2
str3HashCode2 = hashFn2(str3) // 6
str3HashCode3 = hashFn3(str3) // 5

bitArray[2] // 1
bitArray[6] // 1
bitArray[5] // 1

// If all are '1', it might be present //NOT-GUARANTEED
// Reality: PRESENT // CORRECT-ANSWER


4. Check: 'rat' in BF
--------------------
str4= 'rat'
str4HashCode1 = hashFn1(str4) // 15
str4HashCode2 = hashFn2(str4) // 5
str4HashCode3 = hashFn3(str4) // 6


bitArray[15] // 1
bitArray[5] // 1
bitArray[6] // 1

// If all are '1', it might be present //NOT-GUARANTEED
// Reality: PRESENT // WRONG-ANSWER



That is why this is 'probabilistic data structure'
- But BF says, NOT-PRESENT // it guarantees 
- BF also stores this Binary Respresentation into smallerIntegerNumber // This saved lot of space
 _______________________________________________________________________
           Binary                  Decimal
      001011100010000100    --->    47236
 -----------------------------------------------------------------------

```
{% endtab %}
{% endtabs %}

