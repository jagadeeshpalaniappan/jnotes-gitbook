# DB

## Index

| \# | LC\# | Title | Difficulty | Frequency |
| :--- | :--- | :--- | :--- | :--- |
| 1 | 609 | [Find Duplicate File in System](https://leetcode.com/problems/find-duplicate-file-in-system) | Medium | \*\*\*\*\* |
| 2 | 289 | [Game of Life](https://leetcode.com/problems/game-of-life) | Medium | \*\*\*\* |
| 3 | 924 | [Minimize Malware Spread](https://leetcode.com/problems/minimize-malware-spread) | Hard | \*\*\*\* |
| 4 | 928 | [Minimize Malware Spread II](https://leetcode.com/problems/minimize-malware-spread-ii) | Hard | \*\* |
| 5 | 379 | [Design Phone Directory](https://leetcode.com/problems/design-phone-directory) | Medium | \*\*\* |
| 6 | 362 | [Design Hit Counter](https://leetcode.com/problems/design-hit-counter) | Medium | \*\*\* |
| 7 | 290 | [Word Pattern](https://leetcode.com/problems/word-pattern) | Easy |  |
| 8 | 291 | [Word Pattern II](https://leetcode.com/problems/word-pattern-ii) | Hard | \*\*\* |
| 9 | 1236 | [Web Crawler](https://leetcode.com/problems/web-crawler) | Medium | \*\* |
| 10 | 1242 | [Web Crawler Multithreaded](https://leetcode.com/problems/web-crawler-multithreaded) | Medium | \* |
| 11 | 17 | [Letter Combinations of a Phone Number](https://leetcode.com/problems/letter-combinations-of-a-phone-number) | Medium | \* |
| 12 | 1001 | [Grid Illumination](https://leetcode.com/problems/grid-illumination) | Hard | \* |
| 13 | 642 | [Design Search Autocomplete System](https://leetcode.com/problems/design-search-autocomplete-system) | Hard | \* |
| 14 | 1178 | [Number of Valid Words for Each Puzzle](https://leetcode.com/problems/number-of-valid-words-for-each-puzzle) | Hard |  |
| 15 | 140 | [Word Break II](https://leetcode.com/problems/word-break-ii) | Hard |  |
| 16 | 146 | [LRU Cache](https://leetcode.com/problems/lru-cache) | Medium |  |
| 17 | 1010 | [Pairs of Songs With Total Durations Divisible by 60](https://leetcode.com/problems/pairs-of-songs-with-total-durations-divisible-by-60) | Easy |  |
| 18 | 4 | [Median of Two Sorted Arrays](https://leetcode.com/problems/median-of-two-sorted-arrays) | Hard |  |
| 19 | 1 | [Two Sum](https://leetcode.com/problems/two-sum) | Easy |  |
| 20 | 64 | [Minimum Path Sum](https://leetcode.com/problems/minimum-path-sum) | Medium |  |
| 21 | 23 | [Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists) | Hard |  |
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

* find in directory identical files 
* How to get all the files with duplicate file names given a path name.  
  * find all duplicate files within a folder.  
* Duplicated file. The follow-up I answered is hash each file chunk by chunk.
* Implement a function that searches a file system for files with identical contents
* given two very large files, how can one most efficiently check if they are the same file? 
* Group duplicate files in folder, log file manipulation and query.
* If you received a file in chunks, calculate when you have the full file. Fairly open ended.
  * Can assume chunks come with start and end, or size, etc.
* Array presence in another array and questions related to byte arrays
* How to find duplicate files in storage
* Grouping same file in folder
  * How could you group files in nested directories \(like a multidimensional array\) and group files of the same content in a similar array?
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

{% tab title="Video" %}

{% endtab %}

{% tab title="Code" %}
```javascript
...
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

{% endtab %}

{% tab title="Code" %}
```javascript
...
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

## [5. Design Phone Directory](https://leetcode.com/problems/design-phone-directory)

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

{% endtab %}

{% tab title="Code" %}
```javascript
...
```
{% endtab %}
{% endtabs %}

...

## [7. Word Pattern II](https://leetcode.com/problems/word-pattern-ii)

{% tabs %}
{% tab title="Question" %}
...
{% endtab %}

{% tab title="More" %}
* [https://leetcode.com/discuss/interview-question/124709/Dropbox-or-Pattern-Matching](https://leetcode.com/discuss/interview-question/124709/Dropbox-or-Pattern-Matching)
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

## [8. Web Crawler](https://leetcode.com/problems/web-crawler)

{% tabs %}
{% tab title="Question" %}
...
{% endtab %}

{% tab title="More" %}
* Write a program to find all reachable web pages from a given url
{% endtab %}

{% tab title="Video" %}

{% endtab %}

{% tab title="Code" %}
```javascript
...
```
{% endtab %}
{% endtabs %}



## [9. Web Crawler Multithreaded](https://leetcode.com/problems/web-crawler-multithreaded)

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

## [10. Letter Combinations of a Phone Number](https://leetcode.com/problems/letter-combinations-of-a-phone-number)

{% tabs %}
{% tab title="Question" %}
...
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

## [14. Word Pattern](https://leetcode.com/problems/word-pattern)

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



