# DB

## Index

| \# | LC\# | Title | Difficulty | Frequency |
| :--- | :--- | :--- | :--- | :--- |
| 1 | 609 | [Find Duplicate File in System](https://leetcode.com/problems/find-duplicate-file-in-system) | Medium | \*\*\*\*\* |
| 2 | 289 | [Game of Life](https://leetcode.com/problems/game-of-life) | Medium | \*\*\*\* |
| 3 | 924 | [Minimize Malware Spread](https://leetcode.com/problems/minimize-malware-spread) \[TODO\] | Hard | \*\*\*\* |
| 4 | 928 | [Minimize Malware Spread II](https://leetcode.com/problems/minimize-malware-spread-ii) \[TODO\] | Hard | \*\* |
| 5 | 379 | [Design Phone Directory](https://leetcode.com/problems/design-phone-directory) | Medium | \*\*\* |
| 6 | 362 | [Design Hit Counter](https://leetcode.com/problems/design-hit-counter) | Medium | \*\*\* |
| 7 | 290 | [Word Pattern](https://leetcode.com/problems/word-pattern) | Easy |  |
| 8 | 291 | [Word Pattern II](https://leetcode.com/problems/word-pattern-ii) | Hard | \*\*\* |
| 9 | 1236 | [Web Crawler](https://leetcode.com/problems/web-crawler) | Medium | \*\* |
| 10 | 1242 | [Web Crawler Multithreaded](https://leetcode.com/problems/web-crawler-multithreaded) | Medium | \* |
| 11 | 17 | [Letter Combinations of a Phone Number](https://leetcode.com/problems/letter-combinations-of-a-phone-number) | Medium | \* |
| 12 | 1001 | [Grid Illumination](https://leetcode.com/problems/grid-illumination) | Hard | \* |
| 13 | 642 | [Design Search Autocomplete System](https://leetcode.com/problems/design-search-autocomplete-system) | Hard | \* |
| 14 | 1178 | [Number of Valid Words for Each Puzzle](https://leetcode.com/problems/number-of-valid-words-for-each-puzzle) \[TODO\] | Hard |  |
| 15 | 140 | [Word Break II](https://leetcode.com/problems/word-break-ii) | Hard |  |
| 16 | 146 | [LRU Cache](https://leetcode.com/problems/lru-cache) | Medium |  |
| 17 | 1010 | [Pairs of Songs With Total Durations Divisible by 60](https://leetcode.com/problems/pairs-of-songs-with-total-durations-divisible-by-60) | Easy |  |
| 18 | 4 | [Median of Two Sorted Arrays](https://leetcode.com/problems/median-of-two-sorted-arrays) | Hard |  |
|  | 23 | [Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists) | Hard |  |
| 19 | 1 | [Two Sum](https://leetcode.com/problems/two-sum) | Easy |  |
| 20 | 64 | [Minimum Path Sum](https://leetcode.com/problems/minimum-path-sum) | Medium |  |
| 21 |  |  |  |  |
| 22 | 28 | [Implement strStr\(\)](https://leetcode.com/problems/implement-strstr) | Easy |  |
| 23 | 1250 | [Check If It Is a Good Array](https://leetcode.com/problems/check-if-it-is-a-good-array) | Hard |  |



## 0. Implement getByClassName & getByClassnameHierarchy \[FE\]

* [https://leetcode.com/discuss/interview-question/427896/Dropbox-or-Phone-Screen-or-Implement-getByClassName-and-getByClassnameHierarchy](https://leetcode.com/discuss/interview-question/427896/Dropbox-or-Phone-Screen-or-Implement-getByClassName-and-getByClassnameHierarchy)

## [1. Find Duplicate File in System](https://leetcode.com/problems/find-duplicate-file-in-system)

{% tabs %}
{% tab title="Question" %}

{% endtab %}

{% tab title="More" %}
* [https://leetcode.com/discuss/interview-question/307373/Dropbox-or-Phone-Screen-or-Find-Duplicate-File-in-System](https://leetcode.com/discuss/interview-question/307373/Dropbox-or-Phone-Screen-or-Find-Duplicate-File-in-System)

```java
/*
Given a string value for the top level directory as input to your function 
- and helper functions to get files/directories in a given directory (that you need to define, not code),
- write a function to return a list of all duplicate files in the file system. 

For example:  
*/

//Helper functions (need to be defined by you)

 public List<String> getFiles(String directoryPath); //Returns all files directly under this directory
 public List<String> getDirectories(String directoryPath); //Returns all directories directly under this directory 
public String getFileContent(String filePath); //Returns content of a file  

// Write this function (Interviewer just cared about this)
 public List<String> findDuplicates(String rootDirectory) {
```

**Files \(related questions\)**

Duplicate File:

* find in directory identical files 
* How to get all the files with duplicate file names given a path name.  
  * find all duplicate files within a folder
  * Implement a function that searches a file system for files with identical contents
  * How to find duplicate files in storage
  * Group duplicate files in folder
  * Grouping same file in folder
  * How could you group files in nested directories \(like a multidimensional array\) and group files of the same content in a similar array?
* The follow-up
* given two very large files, how can one most efficiently check if they are the same file? 
  * I answered is hash each file chunk by chunk
  * If you received a file in chunks, calculate when you have the full file. 
  * How will you determine duplicates
    * Fairly open ended
  * Can assume chunks come with start and end, or size, etc

Other Questions

* Log File manipulation and Query:
* Array presence in another array and questions related to byte arrays
* How can you determine if a file has any copyright infringement content 
* Cows and folders
* Dropbox File Syncing
* Recursively sort files in a file system
* Write a basic file system and implement the commands 
  * ls, pwd, mkdir, create, rm, cd, cat, mv
  * This was done on my own computer, in the interview room, with a 1.5 hour time limit. 

**Distribute binary file \(daily\) for thousands of servers**

* [https://leetcode.com/discuss/interview-question/193953/Distribute-binary-file-\(daily\)-for-thousands-of-servers](https://leetcode.com/discuss/interview-question/193953/Distribute-binary-file-%28daily%29-for-thousands-of-servers)

**Design a distributed scalable file-storage system like Dropbox**

* [https://leetcode.com/discuss/interview-question/125225/Design-a-distributed-scalable-file-storage-system-like-Dropbox](https://leetcode.com/discuss/interview-question/125225/Design-a-distributed-scalable-file-storage-system-like-Dropbox)

**Permissions in a File System**

* [https://leetcode.com/discuss/interview-question/417262/Dropbox-or-Phone-Screen-or-Permissions-in-a-File-System](https://leetcode.com/discuss/interview-question/417262/Dropbox-or-Phone-Screen-or-Permissions-in-a-File-System)
{% endtab %}

{% tab title="Follow-Up" %}
### **Follow-up Question:**

1. Imagine you are given a real file system, how will you search files? DFS or BFS?
   * [https://jagadeeshpalaniappan.gitbook.io/jnotes/sys-design/system-design/file/search](https://jagadeeshpalaniappan.gitbook.io/jnotes/sys-design/system-design/file/search)
2. If the file content is very large \(GB level\), how will you modify your solution?
   * **key:** fileContent --&gt; **`fileContentHash`** \( SHA-256 or MD5 \)
3. If you can only read the file by 1kb each time, how will you modify your solution?
4. What is the time complexity of your modified solution? What is the most time-consuming part and memory consuming part of it? How to optimize?
5. How to make sure the duplicated files you find are not false positive?

### **Follow-up Answer:**

* **BFS or DFS --&gt; `BFS`**
  * In real file system, files are located close to each other.
  * BFS explores neighbors first. This is great for **space locality** and that's why BFS is expected to be faster.
* **Steps: to handle 'falsePositives':**
  1. compare: **fileSize** // if equal, then files might be same, check further
  2. compare: **hash** \(MD5 or SHA256\) // if equal, then files might be same, check further
  3. asyncCompare: **byteByByte** // to avoid false positives due to hashCollisions
* **Steps: to handle 'veryLargeFile':**
  * read: **chunkByChunk** // instead of reading entireFile \(RAM is not enough\)
  * hash: **eachChunk** \(MD5 or SHA256\)
  * compare: **allChunkHashes**

#### Complexity

Runtime - Worst case \(which is very unlikely to happen\): O\(N^2 \* L\) where L is the size of the maximum bytes that need to be compared  
Space - Worst case: all files are hashed and inserted in the hashmap, so O\(H^2\*L\), H is the hash code size and L is the filename size
{% endtab %}

{% tab title="Video" %}

{% endtab %}

{% tab title="Sol1" %}
```javascript

/*
Using Map
TC: O(n*x) n strings of average length x is parsed.
SC: O(n*x) map and res size grows upto n*x
*/
function findDuplicate(paths) {
  const contentMap = {};
  const res = [];

  // loop: dir
  for (const path of paths) {
    debugger;
    const pathArr = path.split(" ");
    const dirName = pathArr[0];
    for (let i = 1; i < pathArr.length; i++) {
      const fileAndContent = pathArr[i];
      const fileAndContentArr = fileAndContent.split("(");
      const fileName = fileAndContentArr[0];
      const content = fileAndContentArr[1].slice(
        0,
        fileAndContentArr[1].length - 1
      );
      const fullName = `${dirName}/${fileName}`;
  
      if (contentMap[content]) {
        contentMap[content].push(fullName);
      } else {
        contentMap[content] = [fullName];
      }
    }
  }

  // loop: contentMap
  for (const [key, val] of Object.entries(contentMap)) {
      if(val && val.length > 1) {
          // we need only duplicate items
          res.push(val)
      }
  }

  return res;
}


```
{% endtab %}
{% endtabs %}

## [2. Game of Life](https://leetcode.com/problems/game-of-life)

{% tabs %}
{% tab title="Question" %}
...
{% endtab %}

{% tab title="More" %}
* [https://leetcode.com/discuss/interview-question/312457/Dropbox-or-Phone-Screen-or-Game-of-Life](https://leetcode.com/discuss/interview-question/312457/Dropbox-or-Phone-Screen-or-Game-of-Life)
* [https://leetcode.com/discuss/interview-question/285610/Dropbox-or-Game-of-Life](https://leetcode.com/discuss/interview-question/285610/Dropbox-or-Game-of-Life)
* Implement a function to give the next stage of the board for Game of Life \(check LeetCode for more info\). 
  * Follow up: how would you handle the situation if the board \(matrix\) was really large?
* In the game of life \(not the board game with the spinner, the other one\), calculate how to compute the next state of the board. 
  * Interviewer went on to ask how I would do this if I had memory constraints \(board represented by a 1 TB file\).
* Was able to solve it completely and answered a few more questions on how to deal with cases where the board has many \(say, a million\) cells.
{% endtab %}

{% tab title="Video" %}
{% embed url="https://www.youtube.com/watch?v=FWSR\_7kZuYg" %}
{% endtab %}

{% tab title="Code" %}
```javascript
/*
289. Game of Life

Rules :
-------
1. Any live cell with fewer than two live neighbors dies, as if caused by under-population.
2. Any live cell with two or three live neighbors lives on to the next generation.
3. Any live cell with more than three live neighbors dies, as if by over-population..
4. Any dead cell with exactly three live neighbors becomes a live cell, as if by reproduction.

It Means:
--------
0: dead
1: live

*/


/*
*********************
Simplify the Rules:
*********************

curGen     ------------>    nextGen
~~~~~~                      ~~~~~~~
  1 --- (neighbors < 2)   ---> 0      // died: dueToUnderPopulation
  1 --- (neighbors > 3)   ---> 0      // died: dueToOverPopulation
  0 --- (neighbors === 3) ---> 1      // living: dueToReproduction


Use the same Grid:
-------------------
-1:  1--->0 (live to dead)
2:   0--->1 (dead to live)
*/

function encode(item) {
  if (item === 0) {
    return -1;
  } else if (item === 1) {
    return 2;
  } else {
    return item;
  }
}

function decode(item) {
  if (item === -1) {
    return 0;
  } else if (item === 2) {
    return 1;
  } else {
    return item;
  }
}

function revertEncode(item) {
  if (item === -1) {
    return 1;
  } else if (item === 2) {
    return 0;
  } else {
    return item;
  }
}

function gridGet(board, r, c) {
  let val = 0;
  if (board[r] !== undefined && board[r][c] !== undefined) {
    val = revertEncode(board[r][c]);
  }
  return val;
}

function countNeightbors(board, r, c) {
  const topLeft = gridGet(board, r - 1, c - 1);
  const top = gridGet(board, r - 1, c);
  const topRight = gridGet(board, r - 1, c + 1);
  const left = gridGet(board, r, c - 1);
  const right = gridGet(board, r, c + 1);
  const bottomLeft = gridGet(board, r + 1, c - 1);
  const bottom = gridGet(board, r + 1, c);
  const bottomRight = gridGet(board, r + 1, c + 1);

  return (
    topLeft + top + topRight + left + right + bottomLeft + bottom + bottomRight
  );
}

function applyRules(board, r, c, neightbors) {
  const curState = board[r][c];
  // 1 & 2
  if (curState === 1 && (neightbors < 2 || neightbors > 3)) {
    board[r][c] = encode(0); // newState: dead
  } else if (curState === 0 && neightbors === 3) {
    board[r][c] = encode(1); // newState: live
  }
}


/**
  TC: O(M×N), where M is the number of rows and N is the number of columns of the Board.
  SC: O(1)  // since we are re-using the sameArr using encode/decode techniques
 */
function gameOfLife(board) {
  if (board && board.length > 0 && board[0] && board[0].length > 0) {
    const rows = board.length;
    const cols = board[0].length;

    // applyRules
    for (let r = 0; r < rows; r++) {
      for (let c = 0; c < cols; c++) {
        const curState = board[r][c];
        const neightbors = countNeightbors(board, r, c);
        applyRules(board, r, c, neightbors);
      }
    }

    // console.log(JSON.stringify(board));

    // decode
    for (let r = 0; r < rows; r++) {
      for (let c = 0; c < cols; c++) {
        board[r][c] = decode(board[r][c]);
      }
    }

    return board;
  } else {
    return null;
  }
}

const board = [[0, 1, 0], [0, 0, 1], [1, 1, 1], [0, 0, 0]];
console.log(JSON.stringify(gameOfLife(board)));

/*
[
  [0,0,0],
  [1,0,1],
  [0,1,1],
  [0,1,0]
]
*/
```
{% endtab %}

{% tab title="\*\*FOLLOW-UP\*\*" %}
```javascript
/*
FOLLOW-UP:

What if the board is a million by a million? // OR What would happen if the board is infinitely large?
- not possible to 'store' & 'iterate' that big a matrix entirely in memory
- wasting a lot of space if such a huge board only has a few live cells and the rest of them are all dead

#SOL1: (ignoreDeadCells & storeOnlyLiveCells )
----------------------------------------------------------------

it's quite possible that we have a big matrix with a very few live cells. 
In that case it make sense to consider only liveCells
  - ignoreDeadCells & storeOnlyLiveCells 
  - applyRules accordingly using only these live cells

Essentially, we obtain only the live cells from the entire board and then apply the different rules using only the live cells and finally we update the board in-place. The only problem with this solution would be when the entire board cannot fit into memory. how will you return the result?


#SOL2: (loadOnly: curRow, curRow's aboveRow & curRow's belowRow)  (at max 3 rows in memory, discard them once if it is processed)
--------------------------------------------------------------------------------------------------------------------------------
For that scenario, we assume that the contents of the matrix are stored in a file, one row at a time.
In order for us to update a particular cell, 
  - we only have to look at its 8 neighbors which essentially lie in the row above and below it. 
  - So, for updating the cells of a row, we just need the row above and the row below. 
  Thus, we read one row at a time from the file and at max we will have 3 rows in memory. 
  We will keep discarding rows that are processed and then we will keep reading new rows from the file, one at a time.

@beagle's solution revolves around this idea and you can refer to the code in the discussion section for the same. It's important to note that there is no single solution for solving this problem. Everybody might have a different viewpoint for addressing the scalability aspect of the problem and these two solutions just address the most basic problems with handling matrix based problems at scale.


#SOL3:   (loadOnly smalPortion of 3 rows [above, cur, below])
----------------------------------------------------------------
if 3 rows also not possible in memory // take chunk by chunk
(loadOnly: curRowSmalPortion, curRow's aboveRowSmalPortion & curRow's belowRowSmalPortion)  
(at max 3 rows smalPortion in memory, discard them once if it is processed)


#SOL4: Read eachCell and its surrounding 8 cells at a time // But Processing time is very slow 

*/

```
{% endtab %}
{% endtabs %}

## [3. Minimize Malware Spread](https://leetcode.com/problems/minimize-malware-spread)

{% tabs %}
{% tab title="Question" %}
...
{% endtab %}

{% tab title="More" %}
* Malware defender // how I would scale/speed up/improve the solution
{% endtab %}

{% tab title="Video" %}

{% endtab %}

{% tab title="Code" %}
```javascript
...
```
{% endtab %}
{% endtabs %}

## [4. Minimize Malware Spread II](https://leetcode.com/problems/minimize-malware-spread-ii)

{% tabs %}
{% tab title="Question" %}
...
{% endtab %}

{% tab title="More" %}

{% endtab %}

{% tab title="Video" %}

{% endtab %}

{% tab title="Code" %}
```javascript
...
```
{% endtab %}
{% endtabs %}

...

## [6. Design Hit Counter](https://leetcode.com/problems/design-hit-counter)

{% tabs %}
{% tab title="Question" %}
...
{% endtab %}

{% tab title="More" %}
* [https://leetcode.com/discuss/interview-question/178662/Design-a-Hit-Counter](https://leetcode.com/discuss/interview-question/178662/Design-a-Hit-Counter)
* [https://leetcode.com/discuss/interview-question/124821/Dropbox-or-Design-Hit-Counter](https://leetcode.com/discuss/interview-question/124821/Dropbox-or-Design-Hit-Counter)
* Design a Hit Counter 
  * write a program to count how many times a web page has been accessed in the last 5 minutes.  
  * First question was about how to implement get\_hits and log\_hits methods for a website visitors, where get\_hits would return the number of hits in last 5 minutes.
* Follow up question was how to scale this as a service when billions of concurrent Users may be hitting and thus log\_hits will be called that often.
* Write methods to log hits and get number of hits in past 'x' minutes.
{% endtab %}

{% tab title="Video" %}
Implementation: 

* [https://www.youtube.com/watch?v=vMB0XjFpt\_s](https://www.youtube.com/watch?v=vMB0XjFpt_s) 

System Design:\(Rate Limit\) 

* [https://www.youtube.com/watch?v=xrizarXJgC8](https://www.youtube.com/watch?v=xrizarXJgC8)
* [https://www.youtube.com/watch?v=mhUQe4BKZXs](https://www.youtube.com/watch?v=mhUQe4BKZXs)
{% endtab %}

{% tab title="Code" %}
```javascript
/*
https://leetcode.com/problems/design-hit-counter/discuss/83483/Super-easy-design-O(1)-hit()-O(s)-getHits()-no-fancy-data-structure-is-needed!

What is 300? we need only past 5mins  // 5*60sec ==> 300sec
For each second (timestamp), we are counting an entry

TC: 
  -hit(): O(1)      
  -getHits(): O(1)
SC: O(1)

// since we always store & get '300' items O(1) // remember: 300 is constant
// but if we consider 300 is an input, 
  -- then it should be O(s) // s is seconds (past 5 minutes = 5x60sec ==> 300sec)
*/
class HitCounter {
  constructor() {
    this.hits = [];  // new Array(300);
  }
  hit(timestamp) {
    let index = timestamp % 300;
    const hitEntry = this.hits[index];
    if (hitEntry && hitEntry.timestamp === timestamp) {
      hitEntry.count = hitEntry.count + 1;
    } else {
      this.hits[index] = { timestamp, count: 1 };
    }
  }
  getHits = function(curTimestamp) {
    let counter = 0;
    for (let hitEntry of this.hits) {
      if (hitEntry) {
        const timestampFromNow = curTimestamp - hitEntry.timestamp;
        if (timestampFromNow < 300) {
          // count: only applicable timestamp (within 5mins)
          counter = counter + hitEntry.count;
        }
      }
    }

    return counter;
  };
}

```
{% endtab %}

{% tab title="Exe" %}
```
const counter = new HitCounter();

// hit at timestamp 1.
counter.hit(1);

// hit at timestamp 2.
counter.hit(2);

// hit at timestamp 3.
counter.hit(3);

// get hits at timestamp 4, should return 3.
console.log(counter.getHits(4));

// hit at timestamp 300.
counter.hit(300);

// get hits at timestamp 300, should return 4.
console.log(counter.getHits(300));

// get hits at timestamp 301, should return 3.
console.log(counter.getHits(301));

// hit at timestamp 350.
counter.hit(350);

console.log(counter.getHits(600)); // 1
```
{% endtab %}
{% endtabs %}

...

## [7. Word Pattern](https://leetcode.com/problems/word-pattern)

{% tabs %}
{% tab title="Question" %}
...
{% endtab %}

{% tab title="More" %}

{% endtab %}

{% tab title="Video" %}

{% endtab %}

{% tab title="Code" %}
```javascript
/*
290. Word Pattern
https://leetcode.com/problems/word-pattern/

Example 1:
Input: pattern = "abba", str = "dog cat cat dog" ---> Output: true

Example 2:
Input:pattern = "abba", str = "dog cat cat fish" ---> Output: false

Example 3:
Input: pattern = "aaaa", str = "dog cat cat dog" ---> Output: false

Example 4:
Input: pattern = "abba", str = "dog dog dog dog" ---> Output: false
*/

/*
Using Map
TC: O(n)
SC: O(n)
*/
function wordPattern(pattern, str) {
  const words = str.split(" ");
  var map1 = {}; // { patternChar: word }
  var map2 = {}; // { word: patternChar }
  if (pattern.length !== words.length) return false;
  for (let i = 0; i < pattern.length; i++) {
    const char = pattern[i];
    const word = words[i];
    if (map1[char] && map2[word]) {
      if (map1[char] !== word || map2[word] !== char) {
        return false;
      }
    } else if (map1[char] || map2[word]) {
      return false;
    } else {
      map1[char] = word;
      map2[word] = char;
    }
  }
  return true;
}

console.log(wordPattern("abba", "dog cat cat dog")); // true
console.log(wordPattern("abba", "dog dog dog dog")); // false

```
{% endtab %}
{% endtabs %}

...

## [8. Word Pattern II](https://leetcode.com/problems/word-pattern-ii)

{% tabs %}
{% tab title="Question" %}
...

```javascript
Example 1:

Input: pattern = "abab", str = "redblueredblue"
Output: true
Example 2:

Input: pattern = pattern = "aaaa", str = "asdasdasdasd"
Output: true
Example 3:

Input: pattern = "aabb", str = "xyzabcxzyabc"
Output: false
```
{% endtab %}

{% tab title="More" %}
* [https://leetcode.com/discuss/interview-question/124709/Dropbox-or-Pattern-Matching](https://leetcode.com/discuss/interview-question/124709/Dropbox-or-Pattern-Matching)
{% endtab %}

{% tab title="Video" %}
* [https://www.youtube.com/watch?v=XQ3QryI9G2A](https://www.youtube.com/watch?v=XQ3QryI9G2A)
{% endtab %}

{% tab title="Code" %}
```javascript
function matchPattern(str, sIdx, pattern, pIdx, map, set) {
  // BASE-CASE: BOTH-REACHED-MAX-STR: SUCESS
  if (sIdx === str.length && pIdx === pattern.length) {
    return true;
  }
  // BASE-CASE--ONE-REACHED-MAX-STR: FAILED
  if (sIdx === str.length || pIdx === pattern.length) {
    return false;
  }

  // get: curPaternChar
  const curPaternChar = pattern[pIdx];

  // ADDITIONAL-BASE-CASE:
  // curPaternChar--AVAILABLE-IN-MAP
  // & if 'str' startsWith 'subStr' (there is a good chance 'subStr' form the expected str )
  if (map.has(curPaternChar)) {
    // curPaternChar--AVAILABLE-IN-MAP
    const subStr = map.get(curPaternChar);

    // check: 'str' startsWith 'subStr'
    if (str.startsWith(subStr, sIdx)) {
      // substr: MATCHED: proceedBuildingSubstr
      // continue to match the rest match str[sIdx...sIdx+subStr.length]
      const nextSIdx = sIdx + subStr.length;
      return matchPattern(str, nextSIdx, pattern, pIdx + 1, map, set);
    } else {
      // substr: NOT-MATCHED // proceeding further doesnt match at all
      return false;
    }
  }

  // loop: str
  for (let i = sIdx; i < str.length; i++) {
    // get: curSubStr
    const curSubStr = str.substring(sIdx, i + 1);

    // stackTrace(str, i, pIdx, curSubStr);

    if (!set.has(curSubStr)) {
      // curSubStr--NOT-AVAILABLE-IN-SET
      // TRY: currCombo {curPaternChar, curSubStr} // assumption
      map.set(curPaternChar, curSubStr);
      set.add(curSubStr);

      // continue to match the rest
      if (matchPattern(str, i + 1, pattern, pIdx + 1, map, set)) {
        // TRIED-WORKED
        return true;
      }

      // ::backtracking::
      // TRIED-NOT-WORKED: // wrongAssumption: delete currCombo {curPaternChar, curSubStr}
      map.delete(curPaternChar);
      set.delete(curSubStr);
    }
  }

  // we've tried all the possibilties // still no-luck
  return false;
}

/*
Using backtracking solution
TC: O(S^P)  // P: Pattern length, S: str length
SC: O(P)
*/
function wordPatternMatch(pattern, str) {
  const map = new Map();
  const set = new Set();

  return matchPattern(str, 0, pattern, 0, map, set);
}

console.log(wordPatternMatch("aba", "redbluered"));

```
{% endtab %}

{% tab title="Exp" %}
```javascript
/*
--------------------
Thought Process:
--------------------
pattern: 'aba'      // p[0]: 'a',     p[1]: 'b',      p[3]: 'a'
str: 'redbluered'   // s[0]: 'red',   s[1]: 'blue',   s[3]: 'red'

p[0]
r | edbluered

 p[1]	 p[2]
	e # dbluered
	ed # bluered
	edb # luered
	edbl # uered
	edblu # ered
	edblue # red
	edbluer # ed
	edbluere # d
	edbluered #
	// NOT-MATCHED

p[0]
re | dbluered

 p[1]	 p[2]
	d # bluered
	db # luered
	dbl # uered
	dblu # ered
	dblue # red
	dbluer # ed
	dbluere # d
	dbluered #
	// NOT-MATCHED

p[0]
red | bluered

 p[1]	 p[2]
	b # luered
	bl # uered
	blu # ered
	blue # red
	// MATCHED
	true

*/

/*

************
DEBUG:
************

matchPattern(str: redbluered, sIdx: 0, pattern: aba, pIdx: 0, map: [], set: {})

_____loop: start______
-----------i=0--------------
--{ curPaternChar: a, curSubStr: r }
--curSubStr--NOT-AVAILABLE-IN-SET
--TRY--{ curPaternChar: a, curSubStr: r }

	matchPattern(str: redbluered, sIdx: 1, pattern: aba, pIdx: 1, map: [["a","r"]], set: {r})
	_____loop: start______
	-----------i=1--------------
	--{ curPaternChar: b, curSubStr: e }
	--curSubStr--NOT-AVAILABLE-IN-SET
	--TRY--{ curPaternChar: b, curSubStr: e }
		matchPattern(str: redbluered, sIdx: 2, pattern: aba, pIdx: 2, map: [["a","r"],["b","e"]], set: {r,e})
		--curPaternChar--AVAILABLE-IN-MAP
		--{curPaternChar: a, subStr: r }
		--str.startsWith(subStr, sIdx): false
		--substr: NOT-MATCHED
	--TRIED-NOT-WORKED--{ curPaternChar: b, curSubStr: e }
	-----------i=2--------------
	--{ curPaternChar: b, curSubStr: ed }
	--curSubStr--NOT-AVAILABLE-IN-SET
	--TRY--{ curPaternChar: b, curSubStr: ed }
		matchPattern(str: redbluered, sIdx: 3, pattern: aba, pIdx: 2, map: [["a","r"],["b","ed"]], set: {r,ed})
		--curPaternChar--AVAILABLE-IN-MAP
		--{curPaternChar: a, subStr: r }
		--str.startsWith(subStr, sIdx): false
		--substr: NOT-MATCHED
	--TRIED-NOT-WORKED--{ curPaternChar: b, curSubStr: ed }
	-----------i=3--------------
	--{ curPaternChar: b, curSubStr: edb }
	--curSubStr--NOT-AVAILABLE-IN-SET
	--TRY--{ curPaternChar: b, curSubStr: edb }
		matchPattern(str: redbluered, sIdx: 4, pattern: aba, pIdx: 2, map: [["a","r"],["b","edb"]], set: {r,edb})
		--curPaternChar--AVAILABLE-IN-MAP
		--{curPaternChar: a, subStr: r }
		--str.startsWith(subStr, sIdx): false
		--substr: NOT-MATCHED
	--TRIED-NOT-WORKED--{ curPaternChar: b, curSubStr: edb }
	-----------i=4--------------
	--{ curPaternChar: b, curSubStr: edbl }
	--curSubStr--NOT-AVAILABLE-IN-SET
	--TRY--{ curPaternChar: b, curSubStr: edbl }
		matchPattern(str: redbluered, sIdx: 5, pattern: aba, pIdx: 2, map: [["a","r"],["b","edbl"]], set: {r,edbl})
		--curPaternChar--AVAILABLE-IN-MAP
		--{curPaternChar: a, subStr: r }
		--str.startsWith(subStr, sIdx): false
		--substr: NOT-MATCHED
	--TRIED-NOT-WORKED--{ curPaternChar: b, curSubStr: edbl }
	-----------i=5--------------
	--{ curPaternChar: b, curSubStr: edblu }
	--curSubStr--NOT-AVAILABLE-IN-SET
	--TRY--{ curPaternChar: b, curSubStr: edblu }
		matchPattern(str: redbluered, sIdx: 6, pattern: aba, pIdx: 2, map: [["a","r"],["b","edblu"]], set: {r,edblu})
		--curPaternChar--AVAILABLE-IN-MAP
		--{curPaternChar: a, subStr: r }
		--str.startsWith(subStr, sIdx): false
		--substr: NOT-MATCHED
	--TRIED-NOT-WORKED--{ curPaternChar: b, curSubStr: edblu }
	-----------i=6--------------
	--{ curPaternChar: b, curSubStr: edblue }
	--curSubStr--NOT-AVAILABLE-IN-SET
	--TRY--{ curPaternChar: b, curSubStr: edblue }

		matchPattern(str: redbluered, sIdx: 7, pattern: aba, pIdx: 2, map: [["a","r"],["b","edblue"]], set: {r,edblue})
		--curPaternChar--AVAILABLE-IN-MAP
		--{curPaternChar: a, subStr: r }
		--str.startsWith(subStr, sIdx): true
		--substr: MATCHED: proceedBuildingSubstr

			matchPattern(str: redbluered, sIdx: 8, pattern: aba, pIdx: 3, map: [["a","r"],["b","edblue"]], set: {r,edblue})
			--BASE-CASE--ONE-REACHED-MAX-STR: FAILED (pattern-reached-max)

	--TRIED-NOT-WORKED--{ curPaternChar: b, curSubStr: edblue }
	-----------i=7--------------
	--{ curPaternChar: b, curSubStr: edbluer }
	--curSubStr--NOT-AVAILABLE-IN-SET
	--TRY--{ curPaternChar: b, curSubStr: edbluer }
		matchPattern(str: redbluered, sIdx: 8, pattern: aba, pIdx: 2, map: [["a","r"],["b","edbluer"]], set: {r,edbluer})
		--curPaternChar--AVAILABLE-IN-MAP
		--{curPaternChar: a, subStr: r }
		--str.startsWith(subStr, sIdx): false
		--substr: NOT-MATCHED
	--TRIED-NOT-WORKED--{ curPaternChar: b, curSubStr: edbluer }
	-----------i=8--------------
	--{ curPaternChar: b, curSubStr: edbluere }
	--curSubStr--NOT-AVAILABLE-IN-SET
	--TRY--{ curPaternChar: b, curSubStr: edbluere }
		matchPattern(str: redbluered, sIdx: 9, pattern: aba, pIdx: 2, map: [["a","r"],["b","edbluere"]], set: {r,edbluere})
		--curPaternChar--AVAILABLE-IN-MAP
		--{curPaternChar: a, subStr: r }
		--str.startsWith(subStr, sIdx): false
		--substr: NOT-MATCHED
	--TRIED-NOT-WORKED--{ curPaternChar: b, curSubStr: edbluere }
	-----------i=9--------------
	--{ curPaternChar: b, curSubStr: edbluered }
	--curSubStr--NOT-AVAILABLE-IN-SET
	--TRY--{ curPaternChar: b, curSubStr: edbluered }
		matchPattern(str: redbluered, sIdx: 10, pattern: aba, pIdx: 2, map: [["a","r"],["b","edbluered"]], set: {r,edbluered})
		--BASE-CASE--ONE-REACHED-MAX-STR: FAILED
	--TRIED-NOT-WORKED--{ curPaternChar: b, curSubStr: edbluered }
	_____loop: end______

--TRIED-NOT-WORKED--{ curPaternChar: a, curSubStr: r }


-----------i=1--------------
--{ curPaternChar: a, curSubStr: re }
--curSubStr--NOT-AVAILABLE-IN-SET
--TRY--{ curPaternChar: a, curSubStr: re }

	matchPattern(str: redbluered, sIdx: 2, pattern: aba, pIdx: 1, map: [["a","re"]], set: {re})

	_____loop: start______
	-----------i=2--------------
	--{ curPaternChar: b, curSubStr: d }
	--curSubStr--NOT-AVAILABLE-IN-SET
	--TRY--{ curPaternChar: b, curSubStr: d }
		matchPattern(str: redbluered, sIdx: 3, pattern: aba, pIdx: 2, map: [["a","re"],["b","d"]], set: {re,d})
		--curPaternChar--AVAILABLE-IN-MAP
		--{curPaternChar: a, subStr: re }
		--str.startsWith(subStr, sIdx): false
		--substr: NOT-MATCHED
	--TRIED-NOT-WORKED--{ curPaternChar: b, curSubStr: d }
	-----------i=3--------------
	--{ curPaternChar: b, curSubStr: db }
	--curSubStr--NOT-AVAILABLE-IN-SET
	--TRY--{ curPaternChar: b, curSubStr: db }
		matchPattern(str: redbluered, sIdx: 4, pattern: aba, pIdx: 2, map: [["a","re"],["b","db"]], set: {re,db})
		--curPaternChar--AVAILABLE-IN-MAP
		--{curPaternChar: a, subStr: re }
		--str.startsWith(subStr, sIdx): false
		--substr: NOT-MATCHED
	--TRIED-NOT-WORKED--{ curPaternChar: b, curSubStr: db }
	-----------i=4--------------
	--{ curPaternChar: b, curSubStr: dbl }
	--curSubStr--NOT-AVAILABLE-IN-SET
	--TRY--{ curPaternChar: b, curSubStr: dbl }
		matchPattern(str: redbluered, sIdx: 5, pattern: aba, pIdx: 2, map: [["a","re"],["b","dbl"]], set: {re,dbl})
		--curPaternChar--AVAILABLE-IN-MAP
		--{curPaternChar: a, subStr: re }
		--str.startsWith(subStr, sIdx): false
		--substr: NOT-MATCHED
	--TRIED-NOT-WORKED--{ curPaternChar: b, curSubStr: dbl }
	-----------i=5--------------
	--{ curPaternChar: b, curSubStr: dblu }
	--curSubStr--NOT-AVAILABLE-IN-SET
	--TRY--{ curPaternChar: b, curSubStr: dblu }
		matchPattern(str: redbluered, sIdx: 6, pattern: aba, pIdx: 2, map: [["a","re"],["b","dblu"]], set: {re,dblu})
		--curPaternChar--AVAILABLE-IN-MAP
		--{curPaternChar: a, subStr: re }
		--str.startsWith(subStr, sIdx): false
		--substr: NOT-MATCHED
	--TRIED-NOT-WORKED--{ curPaternChar: b, curSubStr: dblu }
	-----------i=6--------------
	--{ curPaternChar: b, curSubStr: dblue }
	--curSubStr--NOT-AVAILABLE-IN-SET
	--TRY--{ curPaternChar: b, curSubStr: dblue }
		matchPattern(str: redbluered, sIdx: 7, pattern: aba, pIdx: 2, map: [["a","re"],["b","dblue"]], set: {re,dblue})
		--curPaternChar--AVAILABLE-IN-MAP
		--{curPaternChar: a, subStr: re }
		--str.startsWith(subStr, sIdx): true
		--substr: MATCHED: proceedBuildingSubstr

			matchPattern(str: redbluered, sIdx: 9, pattern: aba, pIdx: 3, map: [["a","re"],["b","dblue"]], set: {re,dblue})
			--BASE-CASE--ONE-REACHED-MAX-STR: FAILED

	--TRIED-NOT-WORKED--{ curPaternChar: b, curSubStr: dblue }
	-----------i=7--------------
	--{ curPaternChar: b, curSubStr: dbluer }
	--curSubStr--NOT-AVAILABLE-IN-SET
	--TRY--{ curPaternChar: b, curSubStr: dbluer }
		matchPattern(str: redbluered, sIdx: 8, pattern: aba, pIdx: 2, map: [["a","re"],["b","dbluer"]], set: {re,dbluer})
		--curPaternChar--AVAILABLE-IN-MAP
		--{curPaternChar: a, subStr: re }
		--str.startsWith(subStr, sIdx): false
		--substr: NOT-MATCHED
	--TRIED-NOT-WORKED--{ curPaternChar: b, curSubStr: dbluer }
	-----------i=8--------------
	--{ curPaternChar: b, curSubStr: dbluere }
	--curSubStr--NOT-AVAILABLE-IN-SET
	--TRY--{ curPaternChar: b, curSubStr: dbluere }
		matchPattern(str: redbluered, sIdx: 9, pattern: aba, pIdx: 2, map: [["a","re"],["b","dbluere"]], set: {re,dbluere})
		--curPaternChar--AVAILABLE-IN-MAP
		--{curPaternChar: a, subStr: re }
		--str.startsWith(subStr, sIdx): false
		--substr: NOT-MATCHED
	--TRIED-NOT-WORKED--{ curPaternChar: b, curSubStr: dbluere }
	-----------i=9--------------
	--{ curPaternChar: b, curSubStr: dbluered }
	--curSubStr--NOT-AVAILABLE-IN-SET
	--TRY--{ curPaternChar: b, curSubStr: dbluered }
		matchPattern(str: redbluered, sIdx: 10, pattern: aba, pIdx: 2, map: [["a","re"],["b","dbluered"]], set: {re,dbluered})
		--BASE-CASE--ONE-REACHED-MAX-STR: FAILED
		--TRIED-NOT-WORKED--{ curPaternChar: b, curSubStr: dbluered }
	_____loop: end______


--TRIED-NOT-WORKED--{ curPaternChar: a, curSubStr: re }
-----------i=2--------------
--{ curPaternChar: a, curSubStr: red }
--curSubStr--NOT-AVAILABLE-IN-SET
--TRY--{ curPaternChar: a, curSubStr: red }

	matchPattern(str: redbluered, sIdx: 3, pattern: aba, pIdx: 1, map: [["a","red"]], set: {red})
	_____loop: start______
	-----------i=3--------------
	--{ curPaternChar: b, curSubStr: b }
	--curSubStr--NOT-AVAILABLE-IN-SET
	--TRY--{ curPaternChar: b, curSubStr: b }
		matchPattern(str: redbluered, sIdx: 4, pattern: aba, pIdx: 2, map: [["a","red"],["b","b"]], set: {red,b})
		--curPaternChar--AVAILABLE-IN-MAP
		--{curPaternChar: a, subStr: red }
		--str.startsWith(subStr, sIdx): false
		--substr: NOT-MATCHED
	--TRIED-NOT-WORKED--{ curPaternChar: b, curSubStr: b }
	-----------i=4--------------
	--{ curPaternChar: b, curSubStr: bl }
	--curSubStr--NOT-AVAILABLE-IN-SET
	--TRY--{ curPaternChar: b, curSubStr: bl }
		matchPattern(str: redbluered, sIdx: 5, pattern: aba, pIdx: 2, map: [["a","red"],["b","bl"]], set: {red,bl})
		--curPaternChar--AVAILABLE-IN-MAP
		--{curPaternChar: a, subStr: red }
		--str.startsWith(subStr, sIdx): false
		--substr: NOT-MATCHED
	--TRIED-NOT-WORKED--{ curPaternChar: b, curSubStr: bl }
	-----------i=5--------------
	--{ curPaternChar: b, curSubStr: blu }
	--curSubStr--NOT-AVAILABLE-IN-SET
	--TRY--{ curPaternChar: b, curSubStr: blu }
		matchPattern(str: redbluered, sIdx: 6, pattern: aba, pIdx: 2, map: [["a","red"],["b","blu"]], set: {red,blu})
		--curPaternChar--AVAILABLE-IN-MAP
		--{curPaternChar: a, subStr: red }
		--str.startsWith(subStr, sIdx): false
		--substr: NOT-MATCHED
	--TRIED-NOT-WORKED--{ curPaternChar: b, curSubStr: blu }
	-----------i=6--------------
	--{ curPaternChar: b, curSubStr: blue }
	--curSubStr--NOT-AVAILABLE-IN-SET
	--TRY--{ curPaternChar: b, curSubStr: blue }
		matchPattern(str: redbluered, sIdx: 7, pattern: aba, pIdx: 2, map: [["a","red"],["b","blue"]], set: {red,blue})
		--curPaternChar--AVAILABLE-IN-MAP
		--{curPaternChar: a, subStr: red }
		--str.startsWith(subStr, sIdx): true
		--substr: MATCHED: proceedBuildingSubstr
			matchPattern(str: redbluered, sIdx: 10, pattern: aba, pIdx: 3, map: [["a","red"],["b","blue"]], set: {red,blue})
			--BASE-CASE--BOTH-REACHED-MAX-STR: SUCESS
			--TRIED-WORKED--{ curPaternChar: b, curSubStr: blue }
			--TRIED-WORKED--{ curPaternChar: a, curSubStr: red }

true
 */

```
{% endtab %}
{% endtabs %}

...

## [10. Letter Combinations of a Phone Number](https://leetcode.com/problems/letter-combinations-of-a-phone-number)

{% tabs %}
{% tab title="Question" %}
...

[Refer](https://jagadeeshpalaniappan.gitbook.io/jnotes/leet/top-100-liked/top-100-medium#16-letter-combinations-of-a-phone-number):

[https://jagadeeshpalaniappan.gitbook.io/jnotes/leet/top-100-liked/top-100-medium\#16-letter-combinations-of-a-phone-number](https://jagadeeshpalaniappan.gitbook.io/jnotes/leet/top-100-liked/top-100-medium#16-letter-combinations-of-a-phone-number)
{% endtab %}

{% tab title="More" %}
* You are given a 7 digit phone number, and you should find all possible letter combinations based on the digit-to-letter mapping on numeric pad and return only the ones that have valid match against a given dictionary of words. 
{% endtab %}

{% tab title="Video" %}

{% endtab %}

{% tab title="Code" %}
```javascript
...
```
{% endtab %}
{% endtabs %}

...

## [5. Design Phone Directory](https://leetcode.com/problems/design-phone-directory)

{% tabs %}
{% tab title="Question" %}
379. Design Phone Directory

Design a Phone Directory which supports the following operations:

1. `get`: Provide a number which is not assigned to anyone.
2. `check`: Check if a number is available or not.
3. `release`: Recycle or release a number.
{% endtab %}

{% tab title="More" %}

{% endtab %}

{% tab title="Video" %}

{% endtab %}

{% tab title="Code" %}
```javascript

class PhoneDirectory {
  constructor(maxNumbers) {
    this.len = maxNumbers;
    this.availableNumbers = new Set();
    for (let i = 0; i < maxNumbers; i++) {
      this.availableNumbers.add(i);
    }
    // console.log(this.availableNumbers);
  }

  get() {
    if (this.availableNumbers.size === 0) return -1;
    const nextAvailableNo = this.availableNumbers.values().next().value;
    this.availableNumbers.delete(nextAvailableNo);
    return nextAvailableNo;
  }

  check(number) {
    return this.availableNumbers.has(number);
  }

  release(number) {
    this.availableNumbers.add(number);
  }
}

// Init a phone pd containing a total of 3 numbers: 0, 1, and 2.
const pd = new PhoneDirectory(3);

// It can return any available phone number. Here we assume it returns 0.
console.log(pd.get());

// Assume it returns 1.
console.log(pd.get());

// The number 2 is available, so return true.
console.log(pd.check(2));

// It returns 2, the only number that is left.
console.log(pd.get());

// The number 2 is no longer available, so return false.
console.log(pd.check(2));

// Release number 2 back to the pool.
pd.release(2);

// Number 2 is available again, return true.
console.log(pd.check(2));

```
{% endtab %}
{% endtabs %}

...

## [11. Grid Illumination](https://leetcode.com/problems/grid-illumination)

{% tabs %}
{% tab title="Question" %}
...
{% endtab %}

{% tab title="More" %}
* Given an NxN grid with an array of lamp coordinates. Each lamp provides illumination to every square on their x axis, every square on their y axis, and every square that lies in their diagonal \(think of a Queen in chess\). Given an array of query coordinates, determine whether that point is illuminated or not. The catch is when checking a query all lamps adjacent to, or on, that query get turned off. The ranges for the variables/arrays were about: 10^3 &lt; N &lt; 10^9, 10^3 &lt; lamps &lt; 10^9, 10^3 &lt; queries &lt; 10^9.  
{% endtab %}

{% tab title="Video" %}

{% endtab %}

{% tab title="Code" %}
```javascript
...
```
{% endtab %}
{% endtabs %}

...

## [12. Design Search Autocomplete System](https://leetcode.com/problems/design-search-autocomplete-system)

{% tabs %}
{% tab title="Question" %}
...
{% endtab %}

{% tab title="More" %}
* [https://leetcode.com/discuss/interview-question/366628/Dropbox-or-OA-2019-or-Auto-complete-feature](https://leetcode.com/discuss/interview-question/366628/Dropbox-or-OA-2019-or-Auto-complete-feature)
{% endtab %}

{% tab title="Video" %}

{% endtab %}

{% tab title="Code" %}
```javascript
...
```
{% endtab %}
{% endtabs %}

...

## [13. Number of Valid Words for Each Puzzle](https://leetcode.com/problems/number-of-valid-words-for-each-puzzle)

{% tabs %}
{% tab title="Question" %}
...
{% endtab %}

{% tab title="More" %}

{% endtab %}

{% tab title="Video" %}

{% endtab %}

{% tab title="Code" %}
```javascript
...
```
{% endtab %}
{% endtabs %}

...

## 

## [15. Word Break II](https://leetcode.com/problems/word-break-ii)

{% tabs %}
{% tab title="Question" %}
...
{% endtab %}

{% tab title="More" %}

{% endtab %}

{% tab title="Video" %}

{% endtab %}

{% tab title="Code" %}
```javascript
...
```
{% endtab %}
{% endtabs %}

...

## [16. LRU Cache](https://leetcode.com/problems/lru-cache)

{% tabs %}
{% tab title="Question" %}
...
{% endtab %}

{% tab title="More" %}
* It's a data struct with a capacity. Beyond this capacity the least recently used item is removed. You should be able to insert an element, access an element given its key, and delete an element, in constant time. Note that when you access an element, even if it's just for a read, it becomes the most recently used.
{% endtab %}

{% tab title="Video" %}

{% endtab %}

{% tab title="Code" %}
```javascript
...
```
{% endtab %}
{% endtabs %}

...



## [17. Pairs of Songs With Total Durations Divisible by 60](https://leetcode.com/problems/pairs-of-songs-with-total-durations-divisible-by-60)

{% tabs %}
{% tab title="Question" %}
...
{% endtab %}

{% tab title="More" %}
* [https://leetcode.com/discuss/interview-question/315317/Dropbox-or-Online-assessment-or-Pairs-of-songs](https://leetcode.com/discuss/interview-question/315317/Dropbox-or-Online-assessment-or-Pairs-of-songs)
{% endtab %}

{% tab title="Video" %}

{% endtab %}

{% tab title="Code" %}
```javascript
...
```
{% endtab %}
{% endtabs %}

...

## [18. Median of Two Sorted Arrays](https://leetcode.com/problems/median-of-two-sorted-arrays)

{% tabs %}
{% tab title="Question" %}
...
{% endtab %}

{% tab title="More" %}

{% endtab %}

{% tab title="Video" %}

{% endtab %}

{% tab title="Code" %}
```javascript
...
```
{% endtab %}
{% endtabs %}

...

## [19. Two Sum](https://leetcode.com/problems/two-sum)

{% tabs %}
{% tab title="Question" %}
...
{% endtab %}

{% tab title="More" %}

{% endtab %}

{% tab title="Video" %}

{% endtab %}

{% tab title="Code" %}
```javascript
...
```
{% endtab %}
{% endtabs %}

...

## [20. Minimum Path Sum](https://leetcode.com/problems/minimum-path-sum)

{% tabs %}
{% tab title="Question" %}
...
{% endtab %}

{% tab title="More" %}

{% endtab %}

{% tab title="Video" %}

{% endtab %}

{% tab title="Code" %}
```javascript
...
```
{% endtab %}
{% endtabs %}

...

## [21. Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists)

{% tabs %}
{% tab title="Question" %}
...
{% endtab %}

{% tab title="More" %}

{% endtab %}

{% tab title="Video" %}

{% endtab %}

{% tab title="Code" %}
```javascript
...
```
{% endtab %}
{% endtabs %}

...

## [22. Implement strStr\(\)](https://leetcode.com/problems/implement-strstr)

{% tabs %}
{% tab title="Question" %}
...
{% endtab %}

{% tab title="More" %}

{% endtab %}

{% tab title="Video" %}

{% endtab %}

{% tab title="Code" %}
```javascript
...
```
{% endtab %}
{% endtabs %}

...

## [23. Check If It Is a Good Array](https://leetcode.com/problems/check-if-it-is-a-good-array)

{% tabs %}
{% tab title="Question" %}
...
{% endtab %}

{% tab title="More" %}

{% endtab %}

{% tab title="Video" %}

{% endtab %}

{% tab title="Code" %}
```javascript
...
```
{% endtab %}
{% endtabs %}

...

## XXX

{% tabs %}
{% tab title="Question" %}
...
{% endtab %}

{% tab title="More" %}

{% endtab %}

{% tab title="Video" %}

{% endtab %}

{% tab title="Code" %}
```javascript
...
```
{% endtab %}
{% endtabs %}

...



## Interview Experience \[MUST READ\]\*\*\*\*\*

[https://leetcode.com/discuss/interview-experience/335629/Dropbox-or-Sr.-Software-Engineer-or-San-Francisco-Reject  
](https://leetcode.com/discuss/interview-experience/335629/Dropbox-or-Sr.-Software-Engineer-or-San-Francisco-Reject
)



## ID Allocator\*\*\*\*\*\*

* How to optimize space for storing availability of ID’s from 1 to N
* Design a system that maintains a freelist of integers.
* Write a program that allocates and deallocates integers in the rage of 1 -1000000
* Design an ID allocator which can allocate and de-allocate from a range of 1-1,000,000
* Implement two functions that assign/release unique id's from a pool. Memory usage should be minimized and the assign/release should be fast, even under high contention.  



## Number to Text Form

{% tabs %}
{% tab title="First Tab" %}
* Make a program that can print out the text form of numbers from 1 - 1000 \(ex. 20 is "twenty", 105 is "one hundred and five"\)  
* given a number as a string write a algorithm to map to its oral description. I.e.

```text
"1" --> "11" //this can be thought of as there is one one.
"11" --> "21" // there are two ones
"21" -->; "1211" // there is one two and one one
"1211" --> "111221" //there is one one, one two and two ones  
```

* given the output from the first question write a algorithm to calculate how many possible inputs could have created that output. for example.
* "1211" could be interpreted as one two and one one \|\| one hundred and twenty one ones. 
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

--



Questions:

* How to find the greatest value in all the paths from the left to the right on a given board 
* Implement a search method that finds the minimal-cost element of each path in a matrix.
* finding the maximal minimum element in all paths from left to right side of a grid. 
* Implement Dictionary Tree
* Sorting Words in a List
* design a spell-checking algorithm
* finding the next state given a grid
* Tree navigation
* What happens when you type google.com into your browser and press enter?
* Combination, Filesystem, Something like B tree
* how much memory a boolean, long, or char takes up for example
  * how to select data types to compress memory



* locate certain types of words in a dictionary 
* You have a number of meetings \(with their start and end times\). You need to schedule them using the minimum number of rooms. Return the list of meetings in every room.
* Given a list of names \(strings\) and the width of a line, design an algorithm to display them using the minimum number of lines.
* find the square root of an integer
* Frenemy: Find if a given string matches any path in a labeled graph. A path may contain cycles. You have 60 minutes to solve it.
* Implement a Reader writers lock using mutexes and/or condition variables.



