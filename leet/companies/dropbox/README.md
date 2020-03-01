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

{% tab title="CodeSnap" %}
```javascript

/*

ExistingState:
------------------
0 : deadCell
1 : liveCell

NewState: (encode/decode) tecniq to use the same Grid: 
--------------------------------------------------
2 : nextDeadCell ( 1 ---> 0 ) (live to 'dead' in nextState)
3 : nextLiveCell ( 0 ---> 1 ) (dead to 'live' in nextState)

*/

// encode:
// newState:0  --> 2 | newState:1  --> 3


// decode:
// newState:2  --> 0 | newState:3  --> 1


// revertNewChange:
// newState:2  --> 1 | newState:3  --> 0



getCellOldVal(board, r, c) {
  let val = 0;
  if (board[r] !== undefined && board[r][c] !== undefined) {
    val = revertNewChange(board[r][c]);
  }
  return val;
}


countNeightbors(board, r, c) {

  const neighborsLoc = [
    //topLeft   top     topRight
    [-1, -1],   [-1, 0], [-1, 1], 
    //left      curr     right
    [0, -1],             [0, 1],
    //btmLeft    btm     btmRight
    [1, -1],    [1, 0],  [1, 1]
  ];
  
  // forEachNeighborCell: getCellOldVal
      --> getCellOldVal: revertNewChange & getCellVal ==and==> summTheTotalCount

}

applyRules(board, r, c, neightbors) {

  curState = board[r][c];
  
  // rule1: curState:1 && (neightbors < 2 || neightbors > 3) ===> newState: dead
    --> board[r][c] = encode(0);
  
  // rule2: curState:0 && (neightbors === 3) ===> newState: live 
    --> board[r][c] = encode(1);
}


gameOfLife(board) {
  // invalid: input
    -> return null;

  // valid: input
  rows = board.length;
  cols = board[0].length;


  // forEachCell: countNeightbors & applyRules
      --> neightbors = countNeightbors(board, r, c);  // revertNewChangeAndGetCellOldVal and countNeightbors
      --> applyRules(board, r, c, neightbors);  // applyRules and encodeVals

      

  // forEachCell: decodeVals
      --> board[r][c] = decode(board[r][c]);

  // return: decodedVals
  return board;
}
```
{% endtab %}

{% tab title="Code" %}
```javascript
/*
289. Game of Life
https://leetcode.com/problems/game-of-life/

Rules :
-------
1. Any live cell with fewer than two live neighbors dies, as if caused by under-population.
2. Any live cell with two or three live neighbors lives on to the next generation.
3. Any live cell with more than three live neighbors dies, as if by over-population..
4. Any dead cell with exactly three live neighbors becomes a live cell, as if by reproduction.


0: dead
1: live


https://www.youtube.com/watch?v=FWSR_7kZuYg [MUST]
https://www.youtube.com/watch?v=3Bx9moUnIjM
*/

/*
*********************
Simplify the Rules:
*********************

curGenState     ------------>    nextGenState
~~~~~~~~~~~                      ~~~~~~~~~~~~
    1   ---   (neighbors < 2)     ---> 0      // died: dueToUnderPopulation
    1   ---   (neighbors > 3)     ---> 0      // died: dueToOverPopulation
    0   ---   (neighbors === 3)   ---> 1      // living: dueToReproduction


Use the same Grid:
-------------------
  -1:  1--->0 (live to dead)
   2:  0--->1 (dead to live)
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
  const neighborsLoc = [
    [-1, -1], // topLeft
    [-1, 0], // top
    [-1, 1], // topRight
    [0, -1], // left
    [0, 1], // right
    [1, -1], // bottomLeft
    [1, 0], // bottom
    [1, 1] // bottomRight
  ];
  let count = 0;
  for (const curNeighborLoc of neighborsLoc) {
    const curNeighborVal = gridGet(
      board,
      r + curNeighborLoc[0],
      c + curNeighborLoc[1]
    );
    count = count + curNeighborVal;
  }

  return count;
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
  // invalid: input
  if (!(board && board.length > 0 && board[0] && board[0].length > 0)) {
    return null;
  }

  // valid: input
  const rows = board.length;
  const cols = board[0].length;

  // forEachCell: countNeightbors & applyRules
  for (let r = 0; r < rows; r++) {
    for (let c = 0; c < cols; c++) {
      const neightbors = countNeightbors(board, r, c);
      applyRules(board, r, c, neightbors);
    }
  }

  // forEachCell: decodeValues
  for (let r = 0; r < rows; r++) {
    for (let c = 0; c < cols; c++) {
      board[r][c] = decode(board[r][c]);
    }
  }

  return board;
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
  if (pattern.length !== words.length) return false;
    
  var map1 = {}; // { patternChar: word }
  var map2 = {}; // { word: patternChar }

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

{% tab title="ThoughtProcess" %}
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

## 

## [11. Grid Illumination](https://leetcode.com/problems/grid-illumination)

{% tabs %}
{% tab title="Question" %}
```javascript
// https://leetcode.com/problems/grid-illumination/

/*
Question: jUndertstanding
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Input: N = 5, lamps = [[0,0],[4,4]], queries = [[1,1],[1,0]]
Output: [1,0]

#N: 5x5 matrix

#lamps: lampsLocation 'lamp1: at [0,0]' and 'lamp1: at [4,4]'
eachLampLocation: can provides lights visibility to that 
  'entireRow', 'entireCol', 'fwdSlashDiagnol', 'bwdSlashDiagnol'


#queries:  'checkLightVisibilityStatus' & 'turnOffSurrondingLamps'

checkLightVisibilityStatus:
  - if 'light' is visible at that queriedLoc, ===> return '1' 
  - if 'light' is NOT visible, ===> return '0'   

turnOffSurrondingLamps: of 'queriedLoc' 
  - only surrodingArea [[-1,-1],[-1,0],[-1,1],[0,-1],[0,0],[0,1],[-1,-1],[1,0],[1,1]]
                        - topLeft, top, topRight
                        - left,    cur, right
                        - btmLeft, btm, btmRight
  - turiningOff these lamps will impact lightVibility, 
  - so we need to update the lightVibility area whenever we turiningOff light


#Output:  will have the status of eachQuery lightVisibilityStatus

*/
```
{% endtab %}

{% tab title="More" %}
* Given an NxN grid with an array of lamp coordinates. Each lamp provides illumination to every square on their x axis, every square on their y axis, and every square that lies in their diagonal \(think of a Queen in chess\). Given an array of query coordinates, determine whether that point is illuminated or not. The catch is when checking a query all lamps adjacent to, or on, that query get turned off. The ranges for the variables/arrays were about: 10^3 &lt; N &lt; 10^9, 10^3 &lt; lamps &lt; 10^9, 10^3 &lt; queries &lt; 10^9.  
{% endtab %}

{% tab title="jnotes" %}
{% embed url="https://drive.google.com/open?id=14fUVzYVsdK8OaHG5Ksf2dNIX-APSVBnNBRjpNrFSy-c" %}
{% endtab %}

{% tab title="Code" %}
```javascript


function increaseLightCount(map, value) {
  if (map.has(value)) {
    map.set(value, map.get(value) + 1); // increment: lightCount
  } else {
    map.set(value, 1);
  }
}

function decreaseLightCount(map, value) {
  if (map.has(value)) {
    map.set(value, map.get(value) - 1);
  }
}

function turnOffSurrondingLamps(r, c, N, rowMap,colMap,diag1Map, diag2Map, lampMap) {
  
  const direction = [ [-1, -1], [-1, 0], [-1, 1], [0, -1], [0, 0], [0, 1], [-1, -1], [1,0], [1, 1] ];

  // loop: direction  // helps to iterate surrondingArea
  for (let [i, j] of direction) {
    let newR = r + i;
    let newC = c + j;
    const curGridNo = N * newR + newC;

    // if: any of the 'surrondingArea' hasLamp, ===> then 'turnOffAllThoseLamp'
    if (lampMap.has(curGridNo)) {

      // turnOffLamp:: update: lightCount status
      decreaseLightCount(rowMap, newR);
      decreaseLightCount(colMap, newC);
      decreaseLightCount(diag1Map, newR + newC);
      decreaseLightCount(diag2Map, newR - newC);

      // turnOffLamp:: update 'lampMap'
      lampMap.delete(curGridNo);
    }
  }
}

function gridIllumination(N, lamps, queries) {
  const rowMap = new Map(); // {rowNo: lightCount}
  const colMap = new Map(); // {colNo: lightCount}
  const diag1Map = new Map(); // {diag1No: lightCount}  // diag1: r+c
  const diag2Map = new Map(); // {diag2No: lightCount}  // diag2: r-c
  const lampMap = new Map(); // {gridNo: hasLamp} // whether that particular cell 'hasLamp'

  //map what areas are lit
  for (let [r, c] of lamps) {
    increaseLightCount(rowMap, r);
    increaseLightCount(colMap, c);
    increaseLightCount(diag1Map, r + c);
    increaseLightCount(diag2Map, r - c);
    lampMap.set(N * r + c, true);
  }

  // const result = new Array(queries.length).fill(0);
  // let count = 0; // prob could've iterated with queries

  const res = [];

  // loop: queries
  for (let [r, c] of queries) {

    // check: anyway curr (r,c) can get light
    const hasVisibleLight =
      rowMap.get(r) > 0 || // isCurItem 'row' has light -or-
      colMap.get(c) > 0 || // isCurItem 'col' has light -or-
      diag1Map.get(r + c) > 0 || // isCurItem 'diag1' has light -or-
      diag2Map.get(r - c) > 0; // isCurItem 'diag2' has light -or-

    if (hasVisibleLight) {
      res.push(1); // hasVisibleLight
    } else {
      res.push(0); // doesntHaveVisibleLight
    }


    turnOffSurrondingLamps(r, c, N, rowMap,colMap,diag1Map, diag2Map, lampMap);
  }
  return res;
}



//---------------------------Output------------------------------

// Ex1:

let N = 5,
  lamps = [[0, 0], [4, 4]],
  queries = [[1, 1], [1, 0]];
console.log(gridIllumination(N, lamps, queries)); // [1, 0]


// Ex2:
// let N = 6, lamps = [[1, 3], [2, 4], [5, 4]], queries = [[2, 4], [1, 2]];
// console.log(gridIllumination(N, lamps, queries)); // [1, 0]

```
{% endtab %}

{% tab title="matrixShortcuts" %}
```javascript

//--------------------------MARTIX-SHORTCUTS-------------------------------

// 'N x N' matrix  // N=6 here
const grid = [
  ["r0c0", "r0c1", "r0c2", "r0c3", "r0c4", "r0c5"],
  ["r1c0", "r1c1", "r1c2", "r1c3", "r1c4", "r1c5"],
  ["r2c0", "r2c1", "r2c2", "r2c3", "r2c4", "r2c5"],
  ["r3c0", "r3c1", "r3c2", "r3c3", "r3c4", "r3c5"],
  ["r4c0", "r4c1", "r4c2", "r4c3", "r4c4", "r4c5"],
  ["r5c0", "r5c1", "r5c2", "r5c3", "r5c4", "r5c5"]
];

// 'r+c' ===> gives 'forward-slash direction' diagonals
const diag1 = [
  [0, 1, 2, 3, 4, 5],
  [1, 2, 3, 4, 5, 6],
  [2, 3, 4, 5, 6, 7],
  [3, 4, 5, 6, 7, 8],
  [4, 5, 6, 7, 8, 9],
  [5, 6, 7, 8, 9, 10]
];

// 'r-c' ===> gives 'back-slash direction' diagonals
const diag2 = [
  [0, -1, -2, -3, -4, -5],
  [1, 0, -1, -2, -3, -4],
  [2, 1, 0, -1, -2, -3],
  [3, 2, 1, 0, -1, -2],
  [4, 3, 2, 1, 0, -1],
  [5, 4, 3, 2, 1, 0]
];

// '(n * r) + c' ===> gives uniqueGridNo
const uniqueGridNo = [
  [0, 1, 2, 3, 4, 5],
  [6, 7, 8, 9, 10, 11],
  [12, 13, 14, 15, 16, 17],
  [18, 19, 20, 21, 22, 23],
  [24, 25, 26, 27, 28, 29],
  [30, 31, 32, 33, 34, 35]
];

```
{% endtab %}
{% endtabs %}

...

## 

## [13. Number of Valid Words for Each Puzzle](https://leetcode.com/problems/number-of-valid-words-for-each-puzzle) \[JTODO\]

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

{% tab title="Sol1: dp" %}
```javascript
/*

Using DP (simmilar to Recursion)

TC : O(n^3) 
// Size of recursion tree can go up to n^2 // The creation of curDpRes takes n time.

SC : O(n^3)
// The depth of the recursion tree can go up to nn and each activation record can contains a string curDpRes of size nn.

*/
function wordBreak(str, wordDict) {
  const wordDictSet = new Set(wordDict);
  const dp = [];

  dp[0] = [""]; // initial result // baseCase: in recursion

  for (let end = 1; end <= str.length; end++) {
    const curDpRes = [];

    for (let start = 0; start < end; start++) {
      const curWord = str.substring(start, end);

      if (wordDictSet.has(curWord) && dp[start].length > 0) {
        // curWord: available in 'wordDict'

        // populate: curDpRes
        for (const eachItem of dp[start]) {

          // append: 'eachItem' with 'curWord'
          curDpRes.push(eachItem + (eachItem === "" ? "" : " ") + curWord);
        }
      }
    }

    // store: in dp
    dp[end] = curDpRes;
  }

  return dp[str.length];
}

console.log(wordBreak("catsanddog", ["cat", "cats", "and", "sand", "dog"]));
// ["cat sand dog", "cats and dog"]


```
{% endtab %}

{% tab title="ThoughtProcess" %}
```javascript

/*

Input: catsanddog

start-->end ==> curWord   // curWord = str.substring(start,end)

--------$dp=[[""]]------------

#end: 1
~~~~~~~~~~
0 --> 1   ==> c
---------$dp=[[""],[]]-----------

#end: 2
~~~~~~~~~~
 0 --> 2  ==> ca
 1 --> 2  ==> a 

----------$dp=[[""],[],[]]----------

#end: 3
~~~~~~~~~~
 0 --> 3  ==> cat ==> IN-DICT & $dp[0] ==> eachItem in $dp[0] ==> append: 'eachItem + curWord' ==>  $dp[3].push(appendedVal)
 #                                                                              ''   +  cat  
 1 --> 3  ==> at
 2 --> 3  ==> t

------------$dp=[[""],[],[],["cat"]]--------

#end: 4
~~~~~~~~~~
 0 --> 4  ==> cats ==> IN-DICT & $dp[0] ==> eachItem in $dp[0] ==> append: 'eachItem + curWord' ==>  $dp[4].push(appendedVal)
 #                                                                              ''   +  cats  
 1 --> 4  ==> ats
 2 --> 4  ==> ts
 3 --> 4  ==> s

----------$dp=[[""],[],[],["cat"],["cats"]]----------

#end: 5
~~~~~~~~~~
 0 --> 5  ==> catsa
 1 --> 5  ==> atsa
 2 --> 5  ==> tsa
 3 --> 5  ==> sa
 4 --> 5  ==> a
---------$dp=[[""],[],[],["cat"],["cats"],[]]-----------

#end: 6
~~~~~~~~~~
 0 --> 6  ==> catsan
 1 --> 6  ==> atsan
 2 --> 6  ==> tsan
 3 --> 6  ==> san
 4 --> 6  ==> an
 5 --> 6  ==> n

---------$dp=[[""],[],[],["cat"],["cats"],[],[]]-----------

#end: 7
~~~~~~~~~~
 0 --> 7  ==> catsand
 1 --> 7  ==> atsand
 2 --> 7  ==> tsand
 3 --> 7  ==> sand ==> IN-DICT & $dp[3] ==> eachItem in $dp[3] ==> append: 'eachItem + curWord' ==>  $dp[4].push(appendedVal)
 #                                                                           'cat'   +  sand

 4 --> 7  ==> and ==> IN-DICT & $dp[3] ==> eachItem in $dp[4] ==> append: 'eachItem + curWord' ==>  $dp[4].push(appendedVal)
 #                                                                           'cats' +  and

 5 --> 7  ==> nd
 6 --> 7  ==> d

---------$dp=[[""],[],[],["cat"],["cats"],[],[],["cat sand","cats and"]]-----------

#end: 8
~~~~~~~~~~
 0 --> 8  ==> catsandd
 1 --> 8  ==> atsandd
 2 --> 8  ==> tsandd
 3 --> 8  ==> sandd
 4 --> 8  ==> andd
 5 --> 8  ==> ndd
 6 --> 8  ==> dd
 7 --> 8  ==> d

---------$dp=[[""],[],[],["cat"],["cats"],[],[],["cat sand","cats and"],[]]-----------

#end: 9
~~~~~~~~~~
 0 --> 9  ==> catsanddo
 1 --> 9  ==> atsanddo
 2 --> 9  ==> tsanddo
 3 --> 9  ==> sanddo
 4 --> 9  ==> anddo
 5 --> 9  ==> nddo
 6 --> 9  ==> ddo
 7 --> 9  ==> do
 8 --> 9  ==> o

---------$dp=[[""],[],[],["cat"],["cats"],[],[],["cat sand","cats and"],[],[]]-----------

#end: 10
~~~~~~~~~~
 0 --> 10  ==> catsanddog
 1 --> 10  ==> atsanddog
 2 --> 10  ==> tsanddog
 3 --> 10  ==> sanddog
 4 --> 10  ==> anddog
 5 --> 10  ==> nddog
 6 --> 10  ==> ddog
 7 --> 10  ==> dog  ==> IN-DICT & $dp[3] ==> eachItem in $dp[7] ==> append: 'eachItem + curWord' ==>  $dp[10].push(appendedVal)
 #                                                                         'cat sand' +  dog
 #                                                                         'cats and' +  dog

 8 --> 10  ==> og
 9 --> 10  ==> g

---------$dp=[[""],[],[],["cat"],["cats"],[],[],["cat sand","cats and"],[],[],["cat sand dog","cats and dog"]]-----------

*/
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



