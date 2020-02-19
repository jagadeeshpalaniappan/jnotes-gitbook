# File: Content Search

## Search File Content

```fsharp
# Search File Content:
- Brute Force
- Index (Meta Data)
- Inverted Index 
```

## Inverted Index

```fsharp
# Inverted Index

// Basic
{
 'keyword1': ['file1.txt', 'file3.txt'],
 'keyword2': ['file2.txt', 'file6.txt'],
  ....
}


// Advanced: (store more metadata)
{
 'keyword1': {
    freq: 5,
    files: {
        'file1.txt': { position: [0, 3, 6] },
        'file2.txt': { position: [ 8 ] }
  },
 'keyword2': {
    freq: 2,
    files: {
        'file3.txt': { position: [2] },
  }
  ....
}
    
```

## Inverted Index `Example`:

```fsharp
'
file1.txt: Yov! Hello! i am jagadeesh. hello World is my text.....
file2.txt: my world is different than other world.....
file3.txt: Hello, my world is different.....
file4.txt: i am jagadeesh.....
file5.txt: hello jagadeesh. hello world is my text.....
'


// 1. Read File Content
// 2. Cleanup File Content:  toLowerCase, removeStopWords, noiseRemoval, stemmingAndLemmatization ===> keyword
// 3. Inverted Indexing: addKeyWordAndMetaData in DB

const db = {
    'hello': {
        freq: 3,
        files: {
            'file1.txt': { position: [ 1, 5 ] },
            'file3.txt': { position: [ 0 ] }
            'file5.txt': { position: [ 0, 3 ] }
        }
    },
    'world': {
        freq: 8,
        files: {
            'file1.txt': { position: [ 6 ] },
            'file2.txt': { position: [ 1, 6 ] },
            'file3.txt': { position: [ 2 ] },
            'file5.txt': { position: [ 4 ] },
        }
    },
    // ....
};


const searchKeyword = 'hello world';
const searchResults = searchFilesContent(search);  // db['hello']  // db['world']
/'
- file1.txt     // hello: 2 times, world: 1 times present // total: 3
- file5.txt     // hello: 2 times, world: 1 times present // total: 3
- file2.txt     // hello: 0 times, world: 2 times present // total: 2
- file3.txt     // hello: 1 times, world: 2 times present // total: 1
'/
```

## How do we search by `sentance`?

```fsharp
# How do we search by `sentance`?
 - E.g. (both provides same result)  
     - searchKeyword: 'hello world' // file3.txt, file8.txt, file2.txt
     - searchKeyword: 'world hello' // file3.txt, file8.txt, file2.txt
 - there might be a case that 'world' and 'hello' part of different sentence

EASY: we have postions stored in db, match the positions - by searchKeyWordIndex

// E.g. searchKeyword: 'hello world'  // { 0: hello, 1: world }
/'
       hello: 0                world: 1
 - file1[1] matching --> file1[1] notMatching // NOT-OK
 - file1[5] matching --> file1[6] matching // OK
 - file5[0] matching --> file5[1] notMatching // NOT-OK
 - file5[3] matching --> file5[4] matching // OK
 - file3[0] matching --> file3[1] notMatching // NOT-OK  
     - file3[0] matching --> file3[2] matching  // CLOSE-MATCH  // OK
'/


```

## How do we `fuzzySearch` efficiently ?

```fsharp
# How do we `fuzzySearch` or `wildCardSearch` efficiently ?
- E.g. 'hell*'
- Have the keys in sortedOrder // TreeMap
    - find the releated keys using mergeSort // O(logN)
```

## Cons

```fsharp
# Cons:
 - Consume more space
 - wildCardSearch: '*hell*'
    - in this case, we have to search all the keywords
    - Soln: use PrefixTrie or PrefixArray Data Structure
```



{% tabs %}
{% tab title="First Tab" %}
{% embed url="https://www.youtube.com/watch?v=CeGtqouT8eA" %}
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

