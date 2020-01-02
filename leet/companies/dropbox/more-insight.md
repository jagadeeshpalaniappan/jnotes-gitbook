# More Insight

## \*\*\*\*

## **Game of Life**

[https://leetcode.com/discuss/interview-question/312457/Dropbox-or-Phone-Screen-or-Game-of-Life](https://leetcode.com/discuss/interview-question/312457/Dropbox-or-Phone-Screen-or-Game-of-Life)

[https://leetcode.com/discuss/interview-question/285610/Dropbox-or-Game-of-Life](https://leetcode.com/discuss/interview-question/285610/Dropbox-or-Game-of-Life)

Implement a function to give the next stage of the board for Game of Life \(check LeetCode for more info\). Follow up: how would you handle the situation if the board \(matrix\) was really large?

*     In the game of life \(not the board game with the spinner, the other one\), calculate how to compute the next state of the board. Interviewer went on to ask how I would do this if I had memory constraints \(board represented by a 1 TB file\).  

  o    Was able to solve it completely and answered a few more questions on how to deal with cases where the board has many \(say, a million\) cells.

  o    [https://leetcode.com/problems/game-of-life/](https://leetcode.com/problems/game-of-life/)

## Design a Hit Counter

[https://leetcode.com/discuss/interview-question/178662/Design-a-Hit-Counter](https://leetcode.com/discuss/interview-question/178662/Design-a-Hit-Counter)

[https://leetcode.com/discuss/interview-question/124821/Dropbox-or-Design-Hit-Counter](https://leetcode.com/discuss/interview-question/124821/Dropbox-or-Design-Hit-Counter)

* Design a Hit Counter 
  * write a program to count how many times a web page has been accessed in the last 5 minutes.  
  * First question was about how to implement get\_hits and log\_hits methods for a website visitors, where get\_hits would return the number of hits in last 5 minutes.
* Follow up question was how to scale this as a service when billions of concurrent Users may be hitting and thus log\_hits will be called that often.
* Write methods to log hits and get number of hits in past 'x' minutes.  

## \[PS\] Pattern Matching

[https://leetcode.com/discuss/interview-question/124709/Dropbox-or-Pattern-Matching](https://leetcode.com/discuss/interview-question/124709/Dropbox-or-Pattern-Matching)

## Find Duplicate File in System

[https://leetcode.com/discuss/interview-question/307373/Dropbox-or-Phone-Screen-or-Find-Duplicate-File-in-System](https://leetcode.com/discuss/interview-question/307373/Dropbox-or-Phone-Screen-or-Find-Duplicate-File-in-System)

## Distribute binary file \(daily\) for thousands of servers

[https://leetcode.com/discuss/interview-question/193953/Distribute-binary-file-\(daily\)-for-thousands-of-servers](https://leetcode.com/discuss/interview-question/193953/Distribute-binary-file-%28daily%29-for-thousands-of-servers)

## Design a distributed scalable file-storage system like Dropbox

[https://leetcode.com/discuss/interview-question/125225/Design-a-distributed-scalable-file-storage-system-like-Dropbox](https://leetcode.com/discuss/interview-question/125225/Design-a-distributed-scalable-file-storage-system-like-Dropbox)

## \[PS\] Permissions in a File System

[https://leetcode.com/discuss/interview-question/417262/Dropbox-or-Phone-Screen-or-Permissions-in-a-File-System](https://leetcode.com/discuss/interview-question/417262/Dropbox-or-Phone-Screen-or-Permissions-in-a-File-System)

## Rate Limiter

[https://leetcode.com/discuss/interview-question/162779/Dropbox-or-Rate-Limiter](https://leetcode.com/discuss/interview-question/162779/Dropbox-or-Rate-Limiter)

## \[OA\] Auto-complete feature

[https://leetcode.com/discuss/interview-question/366628/Dropbox-or-OA-2019-or-Auto-complete-feature](https://leetcode.com/discuss/interview-question/366628/Dropbox-or-OA-2019-or-Auto-complete-feature)

\[OA\] Spelling Bee

[https://leetcode.com/discuss/interview-question/354523/Dropbox-or-OA-2019-or-Spelling-Bee](https://leetcode.com/discuss/interview-question/354523/Dropbox-or-OA-2019-or-Spelling-Bee)

\[OA\] Pairs of songs [https://leetcode.com/discuss/interview-question/315317/Dropbox-or-Online-assessment-or-Pairs-of-songs](https://leetcode.com/discuss/interview-question/315317/Dropbox-or-Online-assessment-or-Pairs-of-songs)

\[FullExp\] [https://leetcode.com/discuss/interview-experience/335629/Dropbox-or-Sr.-Software-Engineer-or-San-Francisco-Reject](https://leetcode.com/discuss/interview-experience/335629/Dropbox-or-Sr.-Software-Engineer-or-San-Francisco-Reject)

\[PS\] \[QE\] [https://leetcode.com/discuss/interview-question/306379/Dropbox-%40-Quality-Engineer-phone-screen](https://leetcode.com/discuss/interview-question/306379/Dropbox-%40-Quality-Engineer-phone-screen)

Glass Door: [https://www.glassdoor.com/Interview/Dropbox-Software-Engineer-Interview-Questions-EI\_IE415350.0,7\_KO8,25.htm?sort.sortType=RD&sort.ascending=false](https://www.glassdoor.com/Interview/Dropbox-Software-Engineer-Interview-Questions-EI_IE415350.0,7_KO8,25.htm?sort.sortType=RD&sort.ascending=false)

Algorithms, Systems Design, multi-threading, etc 5 rounds \(1 behavioral, 1 deep dive, 2 coding, 1 architecture\). phone screen, coding challenge, and 3 in person on location interviews \(system, parallel programming, networking, basic data structure, algorithm, web infrastructure, tech-stack\)



* Id Allocator

  o    How to optimize space for storing availability of ID’s from 1 to N  

  o    Design a system that maintains a freelist of integers.

  o    Write a program that allocates and deallocates integers in the rage of 1 -1000000  

  o    Design an ID allocator which can allocate and de-allocate from a range of 1-1,000,000

  o    Implement two functions that assign/release unique id's from a pool. Memory usage should be minimized and the assign/release should be fast, even under high contention.  

  o    

* Design a web crawler \(single-threading\) multi-threading \(single machine\)  

  o    Write a program to find all reachable web pages from a given url.  

  o    

* Design client server synchronization protocol for dropbox.
* Files o find in directory identical files o Array presence in another array and questions related to byte arrays o How to get all the files with duplicate file names given a path name. o Duplicated file. The follow-up I answered is hash each file chunk by chunk. o given two very large files, how can one most efficiently check if they are the same file? o Group duplicate files in folder, log file manipulation and query. o If you received a file in chunks, calculate when you have the full file. Fairly open ended. Can assume chunks come with start and end, or size, etc. o How can you determine if a file has any copyright infringement content o Cows and folders o Malware defender ♣ how I would scale/speed up/improve the solution ♣ o How could you group files in nested directories \(like a multidimensional array\) and group files of the same content in a similar array? o Dropbox file syncing. Grouping same file in folder o How to find duplicate files in storage o o Recursively sort files in a file system o Implement a function that searches a file system for files with identical contents. o \(Coding\) Write a basic file system and implement the commands ls, pwd, mkdir, create, rm, cd, cat, mv. This was done on my own computer, in the interview room, with a 1.5 hour time limit. o
* online class registration system: o I had a bunch of related functions that I had to implement \(add a class, remove a class, enroll a student, remove a student, etc\), and they give you the specifics for each function. I didn't think it was very difficult, but it was kind of long so I didn't get to implement everything. o Class registration system. You have to implement 9 functions like create/delete classes, students, enroll/deenroll student to class, remove class \(deregister all students\). o
* * Grid Illumination: 

  o    Given an NxN grid with an array of lamp coordinates. Each lamp provides illumination to every square on their x axis, every square on their y axis, and every square that lies in their diagonal \(think of a Queen in chess\). Given an array of query coordinates, determine whether that point is illuminated or not. The catch is when checking a query all lamps adjacent to, or on, that query get turned off. The ranges for the variables/arrays were about: 10^3 &lt; N &lt; 10^9, 10^3 &lt; lamps &lt; 10^9, 10^3 &lt; queries &lt; 10^9.  

* Pattern Matching

  o    Given a pattern string like "ABBA" and an input string like "redbluebluered", return true if and only if there's a one to one mapping of letters in the pattern to substrings of the input.

* * Write a program to get possible valid words for a given phone number.  

  o    You are given a 7 digit phone number, and you should find all possible letter combinations based on the digit-to-letter mapping on numeric pad and return only the ones that have valid match against a given dictionary of words. 

* * log data aggregation problem 
* How to find the greatest value in all the paths from the left to the right on a given board 
* Implement a search method that finds the minimal-cost element of each path in a matrix.
* finding the maximal minimum element in all paths from left to right side of a grid. 
* sorting of words in a list
* How do you implement a dictionary tree?
* Design a link shortening URL system. Discuss the tradeoffs of different approaches
* Design an LRU cache. 

  o    It's a data struct with a capacity. Beyond this capacity the least recently used item is removed. You should be able to insert an element, access an element given its key, and delete an element, in constant time. Note that when you access an element, even if it's just for a read, it becomes the most recently used. 

* design a spell-checking algorithm
* finding the next state given a grid
* * * lot of questions on scalability and I/o operations related to the problem
* * * Tree navigation 
* MD5
* implement a Reader writers lock using mutexes and/or condition variables.
* Find the optimal solution for "this" algorithm.
* how much memory a boolean, long, or char takes up for example, how to select data types to compress memory
* Iterate through database
* What happens when you type google.com into your browser and press enter? 
* Write a program to find all duplicate files within a folder.  
* Quesion about Hash
* Combination, Filesystem, Something like B tree

talking about edge cases, writing test cases and coding optimizations. The problem addressed building a very big hashmap and how to delete entries given certain time parameters. Things that were dicussed included multithreading and concurrency.

Systm Design: Design a dropbox like application

locate certain types of words in a dictionary lists and sums of elements of the list How would you redo a specific UI?

-- Infix -&gt; postfix expression conversion and evaluation.

### Solve a software routine problem

given a number as a string write a algorithm to map to its oral description. I.e. "1" -&gt; "11" //this can be thought of as there is one one. "11" -&gt; "21" // there are two ones "21" -&gt; "1211" // there is one two and one one "1211" -&gt; "111221" ect. //there is one one, one two and two ones  
given the output from the first question write a algorithm to calculate how many possible inputs could have created that output. for example.

### "1211" could be interpreted as one two and one one \|\| one hundred and twenty one ones.

"Make a program that can print out the text form of numbers from 1 - 1000 \(ex. 20 is "twenty", 105 is "one hundred and five"\)  
Given an array of integers eg \[1,2,-3,1\] find whether there is a sub-sequence that sums to 0 and return it \(eg 1,2,-3 or 2,-3,1\)

--

### You have a number of meetings \(with their start and end times\). You need to schedule them using the minimum number of rooms. Return the list of meetings in every room.

### Given a list of names \(strings\) and the width of a line, design an algorithm to display them using the minimum number of lines.

### find the square root of an integer

Frenemy: Find if a given string matches any path in a labeled graph. A path may contain cycles. You have 60 minutes to solve it.

Duplicated file & Folder:

Given a string value for the top level directory as input to your function and helper functions to get files/directories in a given directory \(that you need to define, not code\), write a function to return a list of all duplicate files in the file system. For example: //Helper functions \(need to be defined by you\) public List getFiles\(String directoryPath\); //Returns all files directly under this directory public List getDirectories\(String directoryPath\); //Returns all directories directly under this directory public String getFileContent\(String filePath\); //Returns content of a file //Write this function \(Interviewer just cared about this\) public List findDuplicates\(String rootDirectory\) {

Deep dive into an application.  
Do you have experience with multithreading and concurrency?

1. String manipulation and arrays - pretty straightforward.     2. Recursion - instructions were not so clear the interviewer provided helper functions as I stuck on some parts

Implement a network service.

Then the interviewer asked me a lot of questions on scalability and I/o operations related to the problem. I felt I had good insights and shared all the trade offs of different approaches to solve the scalability issues.

3:

Most algo questions are easy, but you need to familiar with multithread stuff.

4: Question around data storage and accessing  
Game of life

a coding question on depth first search I was asked about MD5.  
Cows and folders // file I/O hackerrank coding exercise - folders and cows

### design question.

----

### Second question was the folllowing:

Concurrency, locks, system design, know tradeoffs between space and time, think about creative ways to eliminate expensive operations, study a lot of questions that concern matrices, I know you want specific real questions here but honestly studying design patterns and basic tradeoffs of data structures is going to help you more than memorizing a bunch of problems

6:

“Design hit counter” problem has recently been asked by many companies including Dropbox and the question is harder than it seems to be. This week, we’ll uncover all the mysteries of the problem. A couple of topics are discussed including basic data structures design, various optimization, concurrency and distributed counter.

Definitely be very comfortable with concurrency and details of memory \(know how much memory a boolean, long, or char takes up for example, how to select data types to compress memory\).

7:

some dynamic programming, and a lot of systems. It would also be helpful to know multiple implementations of priority queues and advantages and disadvantages to each

--

### I definitely recommend studying up on concurrency for the interview in the language of your choice. If you can build a basic image link downloader or web crawler with mutlithreading then you should be fine on that one part. The interviewer will be of no help so you must memorize every API call and piece of syntactic sugar surrounding concurrency. If you aren't familiar enough with the syntax then you won't be able to demonstrate that you understand the most basic concurrency concepts properly. It is not a discussion question. It is very much a whiteboard multiple threads in 30 minutes question.

Develop a system to count web hits in the last 5 minutes Write a web crawler \(follow up question: make it multithreaded\)

### Interviewer was much more interested in seeing how you handle edge cases and how you approach scalability. On-sites were difficult, and most of the questions were harder/more-involved versions of common LeetCode type questions. Expect one question requiring detailed concurrency knowledge, and be prepared to explain how your algorithm can scale to larger data sets.

10:

implement a function that returns the number of visit in the most recent 10 minutes, and a log function to be called every time there is a new visit.

As an engineer, maybe 10-20% of your job is writing code to solve a problem; much more of the job is about explaining to other people how you've solved a problem, or why you've solved it that way. It may seem like the interview is all about writing code to solve a problem, but it's actually about both writing code to solve a problem and communicating clearly about how you're solving the problem.

Basically the interview asked the question about gets and hits for a website, how you would design the system and the trade off.

### Implementing interfaces, dynamic programming/recursive backtracking problems, problems that could only be solved through bit-manipulation

### --

Web crawler implementation \(single and multi-threaded\)

Phone: On site:

Implement a class to allocate integer IDs and release them so that they are reusable

Implement a Class Registration System. The requirements were neatly specified in a very long description. The method declarations were provided. I was asked to implement around 8 to 9 methods according to the requirement.

you are building a website and how would you count the number of visitors for the past 5 min. Follow ups included exploring potential concurrency issues and how would you fix it.

Normal behavior questions followed by two questions related to log system. And then talked about the complexity of the algorithm.

I had a question about locking which was probably the trickiest.

\(VARIATION OF:\) Given a set of possible change, such as {1, 5, 10, 25}, and an amount such as 13, return all possible ways you can give change back to someone.

pattern matching with strings.

First interview involved finding the sum to a target in an array, second involved designing a log-hit counter for a website. I was allowed to write both in java. The questions weren't overly difficult, but they expected top-notch answers!

