# 1. Top 100 - EASY

## Index

| \# | qId | Title | freqStars |
| :--- | :--- | :--- | :--- |
| 1 | 1 | [Two Sum](https://leetcode.com/problems/two-sum) | \*\*\*\*\*\*\* |
| 2 | 53 | [Maximum Subarray](https://leetcode.com/problems/maximum-subarray) | \*\*\*\*\* |
| 3 | 21 | [Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists) | \*\*\*\*\* |
| 4 | 20 | [Valid Parentheses](https://leetcode.com/problems/valid-parentheses) | \*\*\*\*\* |
| 5 | 206 | [Reverse Linked List](https://leetcode.com/problems/reverse-linked-list) | \*\*\*\* |
| 6 | 121 | [Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock) | \*\*\*\* |
| 7 | 155 | [Min Stack](https://leetcode.com/problems/min-stack) | \*\*\* |
| 8 | 70 | [Climbing Stairs](https://leetcode.com/problems/climbing-stairs) | \*\*\* |
| 9 | 283 | [Move Zeroes](https://leetcode.com/problems/move-zeroes) | \*\*\* |
| 10 | 101 | [Symmetric Tree](https://leetcode.com/problems/symmetric-tree) | \*\* |
| 11 | 198 | [House Robber](https://leetcode.com/problems/house-robber) | \*\* |
| 12 | 234 | [Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list) | \*\* |
| 13 | 543 | [Diameter of Binary Tree](https://leetcode.com/problems/diameter-of-binary-tree) | \*\* |
| 14 | 141 | [Linked List Cycle](https://leetcode.com/problems/linked-list-cycle) | \*\* |
| 15 | 169 | [Majority Element](https://leetcode.com/problems/majority-element) | \*\* |
| 16 | 136 | [Single Number](https://leetcode.com/problems/single-number) | \*\* |
| 17 | 160 | [Intersection of Two Linked Lists](https://leetcode.com/problems/intersection-of-two-linked-lists) | \*\* |
| 18 | 104 | [Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree) | \*\* |
| 19 | 448 | [Find All Numbers Disappeared in an Array](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array) | \*\* |
| 20 | 226 | [Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree) | \*\* |
| 21 | 617 | [Merge Two Binary Trees](https://leetcode.com/problems/merge-two-binary-trees) | \* |
| 22 | 437 | [Path Sum III](https://leetcode.com/problems/path-sum-iii) | \* |
| 23 | 581 | [Shortest Unsorted Continuous Subarray](https://leetcode.com/problems/shortest-unsorted-continuous-subarray) | \* |



## [1.Two Sum](https://leetcode.com/problems/two-sum)

{% tabs %}
{% tab title="Question" %}
Given an array of integers, return **indices** of the two numbers such that they add up to a specific target.

You may assume that each input would have _**exactly**_ one solution, and you may not use the _same_ element twice.

**Example:**

```text
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```
{% endtab %}

{% tab title="Video" %}
{% embed url="https://www.youtube.com/watch?v=TcsYEnMrnFo" %}

{% embed url="https://www.youtube.com/watch?v=Ivyh3V4QolA" %}
{% endtab %}

{% tab title="Code" %}
```javascript
// Map lookup [BEST-SOLN]
// Time Complexity: O(n) // Space complexity : O(n) extraSpace: hashmap-lookup
function twoSum(inputArr, target) {

  // map = { eachInputVal: currespondingIndex }
  var map = {};
  for (var i = 0; i < inputArr.length; i++) {

    var currentNo = inputArr[i];
    var expectedNo = target - currentNo;

    // Is expectedNo already available in Map?
    if (map[expectedNo] || map[expectedNo] === 0) {
      // [expectedIndex , currentIndex]
      return [map[expectedNo], i];
    }

    // expectedNo NOT available, add it in the map
    // map: { currentNo: currentIndex }
    map[currentNo] = i;
  }

}
```
{% endtab %}
{% endtabs %}

## [2. Maximum Contiguous 'SubArr Sum'](https://leetcode.com/problems/maximum-subarray) 

{% tabs %}
{% tab title="Question" %}
Given an integer array `nums`, find the **contiguous subarray** \(containing at least one number\) which has the **largest sum** and return its sum.

**Example:**

```text
Input: [-2,1,-3,4,-1,2,1,-5,4],
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.
```

**Follow up:**

If you have figured out the O\(_n_\) solution, try coding another solution using the divide and conquer approach, which is more subtle.
{% endtab %}

{% tab title="Video" %}
{% embed url="https://www.youtube.com/watch?v=2MmGzdiKR9Y" %}
{% endtab %}

{% tab title="Code" %}
```javascript
// Sol1: [BEST]
// Time complexity : O(N) // Space complexity : O(1)

function maxSubArray(inputArr) {
  let maxSumSoFar = inputArr[0];
  let currBestSum = inputArr[0];

  for (let i = 1; i < inputArr.length; i++) {
    // currBestSum = 'currItem' or 'currItem+lastBestSum'
    currBestSum = Math.max(inputArr[i], currBestSum + inputArr[i]);
    maxSumSoFar = Math.max(maxSumSoFar, currBestSum);
  }
  return maxSumSoFar;
}
```
{% endtab %}
{% endtabs %}

## [3. Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists)

{% tabs %}
{% tab title="Question" %}
Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

**Example:**

```text
Input: 1->2->4, 1->3->4
Output: 1->1->2->3->4->4
```
{% endtab %}

{% tab title="Video" %}
{% embed url="https://www.youtube.com/watch?v=GfRQvf7MB3k" %}
{% endtab %}

{% tab title="Code" %}
```javascript
class ListNode {}

// Sol1: [BEST]
// Time complexity : Time complexity : O(n + m)  n: l1.length , m: l2.length
//    -technically: l1.length or l2.length (whichever is greater)
// Space complexity : O(1)

function mergeTwoLists(l1, l2) {
  let dummyHead = new ListNode(0);
  let current = dummyHead;

  // We set pointers to the head of list 1 and list 2
  // use 2pointers: these pointers (for iteration)
  let p1 = l1;
  let p2 = l2;

  // stopIteration: when anyOne 'list' is exhausted
  while (p1 != null && p2 != null) {

    // compare: 'p1' or 'p2' smaller
    if (p1.val <= p2.val) {
      // 'p1' wins (p1.val is smaller)
      current.next = p1;
      p1 = p1.next;
    } else {
      // 'p2' wins (p2.val is smaller)
      current.next = p2;
      p2 = p2.next;
    }

    // iteration: nextItem
    current = current.next;
  }

  // anyOne 'list' is exhausted, we just append the other remaining list to the end of the current list
  current.next = p1 != null ? p1 : p2;

  // We just return dummyHead's next, (now this will have the final sorted merged list)
  return dummyHead.next;
}
```
{% endtab %}
{% endtabs %}

## [4. Is Parentheses Valid](https://leetcode.com/problems/valid-parentheses)

{% tabs %}
{% tab title="Question" %}
Given a string containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:

1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.

Note that an empty string is also considered valid.

**Example 1:**

```text
Input: "()"
Output: true
```

**Example 2:**

```text
Input: "()[]{}"
Output: true
```

**Example 3:**

```text
Input: "(]"
Output: false
```

**Example 4:**

```text
Input: "([)]"
Output: false
```

**Example 5:**

```text
Input: "{[]}"
Output: true
```
{% endtab %}

{% tab title="Video" %}
{% embed url="https://www.youtube.com/watch?v=CCyEXcNamC4" %}
{% endtab %}

{% tab title="Code" %}
```javascript
// Sol1: [BEST]
// Time complexity : O(n) 
// Space complexity : O(n) extraSpace: stack-space 
//  - worst case, we might end up pushing all the brackets onto the stack. e.g. ((((((((((.


// hashMap: { closingBracket: openingBracket }
const bracketMap = {
  ")": "(",
  "}": "{",
  "]": "["
};

function isValid(s) {
  const stack = [];

  for (let i = 0; i < s.length; i++) {
    const currChar = s[i];

    // Is 'currChar' is 'closingBracket'
    if (bracketMap[currChar]) {
      // get: matchingOpeningBracket from the bracketMap.
      const matchingOpeningBracket = bracketMap[currChar];
      // get: lastOpeningBracket from the stack.
      const lastOpeningBracket = stack.pop();

      if (matchingOpeningBracket != lastOpeningBracket) {
        // If 'matchingOpeningBracket' is not 'lastOpeningBracket' we added in stack, return false.
        return false;
      }

    } else {
      // add 'openingBracket' to the stack.
      stack.push(currChar);
    }
  }

  // If the 'stack' still contains openingBracket, then it is an invalid expression.
  return stack.length === 0;
}

```
{% endtab %}
{% endtabs %}



## [5. Reverse LinkedList](https://leetcode.com/problems/reverse-linked-list) 

{% tabs %}
{% tab title="Question" %}
Reverse a singly linked list.

**Example:**

```text
Input: 1->2->3->4->5->NULL
Output: 5->4->3->2->1->NULL
```

**Follow up:**

A linked list can be reversed either iteratively or recursively. Could you implement both?
{% endtab %}

{% tab title="Video" %}
{% embed url="https://www.youtube.com/watch?v=O0By4Zq0OFc" %}
{% endtab %}

{% tab title="Code" %}
```javascript
// Sol1: [BEST]
// Time complexity : O(n) // Space complexity : O(1)

class ListNode {}

function reverseList(head) {
  let prev = null;
  let curr = head;

  // iterate: until lastNode
  while (curr != null) {
    let nextTemp = curr.next;

    // reverse:
    curr.next = prev;

    // next: iteration
    prev = curr;
    curr = nextTemp;
  }
  return prev;
}

```
{% endtab %}

{% tab title="Code \(Recursive\)" %}
```javascript

// Sol2:
// Time complexity : O(n) // Space complexity : O(n) extraSpace: recursion-stack-space
function reverseList(currNode) {
  // base case:
  if (currNode == null || currNode.next == null) {
    return currNode;
  }

  // save: 'nextNodeTemp'
  let nextNodeTemp = currNode.next;

  // (except: myself) give me 'reversedList' all other items next to myself
  let reversedListHead = reverseList(nextNodeTemp);


  // now, 'nextNodeTemp' is the 'lastNode' (since it is reversed)
  // reversedListHead <-- ... <--- 'lastNode [nxt]'  --> NULL

  // assign: myself to lastNode's nextNode
  // reversedListHead<-- ... <--- 'lastNode [nxt]'  --> currNode
  nextNodeTemp.next = currNode;

  // now 'myself' becomes the 'lastNode'
  // mark: my nextNode as 'NULL'
  currNode.next = null;

  return reversedListHead;
}
```

[https://www.youtube.com/watch?v=MRe3UsRadKw](https://www.youtube.com/watch?v=MRe3UsRadKw)
{% endtab %}
{% endtabs %}

## [6.Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock)

{% tabs %}
{% tab title="Question" %}
Say you have an array for which the _i_th element is the price of a given stock on day _i_.

If you were only permitted to complete at most one transaction \(i.e., buy one and sell one share of the stock\), design an algorithm to find the maximum profit.

Note that you cannot sell a stock before you buy one.

**Example 1:**

```text
Input: [7,1,5,3,6,4]
Output: 5
Explanation: 
Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
NOT: 7-1 = 6, as selling price needs to be larger than buying price.
```

**Example 2:**

```text
Input: [7,6,4,3,1]
Output: 0
Explanation: In this case, no transaction is done, i.e. max profit = 0.
```
{% endtab %}

{% tab title="Video" %}
{% embed url="https://www.youtube.com/watch?v=mj7N8pLCJ6w" %}
{% endtab %}

{% tab title="Code\(BF\)" %}
```javascript
// Sol1 :  Brute Force
// Time complexity : O(n^2) // Space complexity : O(1)
function maxProfit(prices) {
  let maxProfitSoFar = 0;
  for (let i = 0; i < prices.length - 1; i++) {
    const currItem = prices[i];

    // we can avoid this 'forLoop',
    // since anyway , we further iterate other items in the outerForLooop,
    // We dont need this extraLoop
    for (let j = i + 1; j < prices.length; j++) {
      const currProfit = prices[j] - currItem;

      // 'currProfit' is better than 'maxProfitSoFar'
      // update: maxProfitSoFar
      maxProfitSoFar = Math.max(maxProfitSoFar, currProfit);
    }
  }
  return maxProfitSoFar;
}
```
{% endtab %}

{% tab title="Code\(BEST\)" %}
```javascript
// Sol2 :  [BEST]
// Time complexity : O(n) // Space complexity : O(1)
/*
  1. find: minItem
  2. find: maxProfitSoFar
*/
function maxProfit2(prices) {
  let minPriceSoFar = Number.MAX_VALUE;
  let maxProfitSoFar = 0;

  for (let i = 0; i < prices.length; i++) {
    const currItem = prices[i];

    if (currItem < minPriceSoFar) {
      // 'currItem' is smaller than 'minPriceSoFar'
      // update: minPriceSoFar
      minPriceSoFar = currItem;
    } else {
      const currProfit = currItem - minPriceSoFar;

      // 'currProfit' is better than 'maxProfitSoFar'
      // update: maxProfitSoFar
      maxProfitSoFar = Math.max(maxProfitSoFar, currProfit);
    }
  }
  return maxProfitSoFar;
}

```



```javascript
// Sol2 :  [BEST] [SHORT]
// Time complexity : O(n) // Space complexity : O(1)
/*
  1. find: minItem
  2. find: maxProfitSoFar
*/
function maxProfit(prices) {
  let minPriceSoFar = Number.MAX_VALUE;
  let maxProfitSoFar = 0;

  for (let i = 0; i < prices.length; i++) {
    const currItem = prices[i];

    // 'currItem' is smaller than 'minPriceSoFar' // update: minPriceSoFar
    minPriceSoFar = Math.min(currItem, minPriceSoFar);

    const currProfit = currItem - minPriceSoFar;
    // 'currProfit' is better than 'maxProfitSoFar' // update: maxProfitSoFar
    maxProfitSoFar = Math.max(maxProfitSoFar, currProfit);
  }
  return maxProfitSoFar;
}
```
{% endtab %}
{% endtabs %}

## [7. Min Stack](https://leetcode.com/problems/min-stack)

{% tabs %}
{% tab title="Question" %}
Design a **Stack** data-structure that supports push, pop, top, and retrieving the minimum element in constant time O\(1\).

* **push\(x\)** -- Push element x onto stack.
* **pop\(\)** -- Removes the element on top of the stack.
* **top\(\)** -- Get the top element.
* **getMin\(\)** -- Retrieve the minimum element in the stack.

**Example:**

```text
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.getMin();   --> Returns -3.
minStack.pop();
minStack.top();      --> Returns 0.
minStack.getMin();   --> Returns -2.
```
{% endtab %}

{% tab title="Video" %}

{% endtab %}

{% tab title="Code\(wrong\)" %}
```javascript
class MinStack {
    constructor() {
        this.stack = [];
        this.min = Number.MAX_VALUE;
    }
    push(x) {
        const min = typeof this.getMin() === 'number' ? Math.min(x, this.getMin()) : x;
  this.stack.push({val: x, min});
    }
    pop() {
        return this.stack.pop();
    }
    top() {
        return this.stack.length ? this.getLast().val : null;
    }
    getMin() {
        return this.stack.length ? this.getLast().min : null;
    }
    getLast() {
        return this.stack[this.stack.length - 1];
    }

}


// NOTE: This is WRONG-ANSWER
// while 'pushing' new val (this can update the minVal)
// But while 'poping' (this doesn't update the current minVal)
// This solution doesn't track minVal for eachRecord
```
{% endtab %}

{% tab title="Code" %}
```javascript
/*
  Sol1: [BEST] keep track currMin for each item we push
  push, pop, top, getMin --> O(1) Time & Space
  [ 
    {val: 1, currMin: 1}, 
    {val: 2, currMin: 1},
    {val: -5, currMin: -5}, 
    {val: 3, currMin: -5},.....
  ]

  // getMin: lastItem.currMin
*/
class MinStack {
  constructor() {
    this.stack = [];
  }
  push(x) {
    const currMin =
      typeof this.getMin() === "number" ? Math.min(x, this.getMin()) : x;
    this.stack.push({ val: x, currMin });
  }
  pop() {
    return this.stack.pop();
  }
  top() {
    return this.stack.length ? this.getLast().val : null;
  }
  getMin() {
    return this.stack.length ? this.getLast().currMin : null;
  }
  getLast() {
    return this.stack[this.stack.length - 1];
  }
}

```
{% endtab %}

{% tab title="Result Walkthrough" %}
```javascript

console.log("MinStack");

const minStack = new MinStack();
minStack.push(1);
minStack.push(2);
// [1, 2]

console.log(minStack.getMin()); // 1

minStack.push(3);
minStack.push(-2);
minStack.push(4);
minStack.push(5);
// [1, 2, 3, -2, 4, 5]

console.log(minStack.getMin()); // -2
console.log(minStack.top()); // 5

minStack.pop();
// [1, 2, 3, -2, 4]

console.log(minStack.top()); // 4
console.log(minStack.getMin()); // -2

minStack.pop();
minStack.pop();
// [1, 2, 3]

console.log(minStack.top()); // 3
console.log(minStack.getMin()); // 1

```
{% endtab %}
{% endtabs %}

## [8.Climbing Stairs](https://leetcode.com/problems/climbing-stairs)

{% tabs %}
{% tab title="Question" %}
You are climbing a stair case. It takes _n_ steps to reach to the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

**Note:** Given _n_ will be a positive integer.

**Example 1:**

```text
Input: 2
Output: 2
Explanation: There are two ways to climb to the top.
1. 1 step + 1 step
2. 2 steps
```

**Example 2:**

```text
Input: 3
Output: 3
Explanation: There are three ways to climb to the top.
1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step
```
{% endtab %}

{% tab title="QExplained" %}
```javascript
For '2' steps, 
way1: u can take '1-step' (2 times)   ===> (1 + 1)
way2: u can take '2-step' (1 time)    ===> 2
Ans: noOfWays ==> 2


For '3' steps, 
way1: u can take '1-step' (3 times)   ===> (1 + 1 + 1)
way2: u can take '2-step' (1 time)  +  take '1-step' (1 time)   ===> (2 + 1)
way3: u can take '1-step' (1 time)  +  take '2-step' (1 time)   ===> (1 + 2)
Ans: noOfWays ==> 3

For '4' steps, 
way1: u can take '1-step' (4 times)   ===> (1 + 1 + 1 + 1)
way2: u can take '2-step' (1 time)  +  take '2-step' (1 time)   ===> (2 + 2)
way3: u can take '2-step' (1 time)  +  take '1-step' (2 time)   ===> (2 + 2)
way4: u can take '1-step' (2 time)  +  take '2-step' (1 time)   ===> (2 + 2)
way5: u can take '1-step' (1 time)  +  take '2-step' (1 time)  +  take '1-step' (1 time) ===> (1 + 2)
Ans: noOfWays ==> 5
```
{% endtab %}

{% tab title="Video" %}
{% embed url="https://www.youtube.com/watch?v=NFJ3m9a1oJQ" %}
{% endtab %}

{% tab title="Formula" %}
```bash
------------------------------------------------------------------------
Solution: Formula
------------------------------------------------------------------------
if we can only take ('1-step' or '2-step' )at a time
f(n) = f(n-1) + f(n-2)


if we can only take ('1-step' or '3-step' )at a time
f(n) = f(n-1) + f(n-3)

------------------------------------------------------------------------
Base Case:: f(1 steps) = 1 way, f(0 steps) = 1 way, f(-x steps) = 1 way
------------------------------------------------------------------------
for '0' steps --> u can make only one distinct way : take '0-step' (1 time) // which means doing nothing
for '1' steps --> u can make only one distinct way : take '1-step' (1 time)


***for any negative values,
for '-4' steps --> u can make only one distinct way : take '0-step' (1 time) // which means doing nothing
------------------------------------------------------------------------
```
{% endtab %}

{% tab title="PPT" %}
{% embed url="https://drive.google.com/open?id=1HXCxrhPcw5vHx8SxaLxfeDE\_MzhLc-DirRTUZsSLtac" %}
{% endtab %}

{% tab title="Sol1" %}
```javascript

// Sol1: Recursion (memoized) (DP: top-to-bottom-approach)
// Time Complexity: O(n) // Space Complexity: O(n)  extraSpace: stack-space

function climbStairs1(n, memo) {
  // Base Case:: f(0 steps) = 1 way, f(-x steps) = 0 way
  if (n < 0) {
    return 0;
  }

  // only 1 distinct way to climb 1 steps is, We take 1 step.
  if (n == 0) {
    return 1;
  }

  // get: form cache (if available)
  if (memo[n] > 0) {
    return memo[n];
  }

  // if we can only take 1 or 2 steps
  // f(n) = f(n-1) + f(n-2)
  const currNoOfWays = climbStairs1(n - 1, memo) + climbStairs1(n - 2, memo);

  // cache it
  memo[n] = currNoOfWays;
  return currNoOfWays;
}

function climbStairsHelper(n) {
  const memo = [];
  return climbStairs1(n, memo);
}

// 3 steps
console.log(climbStairsHelper(3)); // 3 ways
// 6 steps
console.log(climbStairsHelper(6)); // 13 ways
```
{% endtab %}

{% tab title="Sol2" %}
```javascript
// Soln2: Using 'dpArray' [DP: BOTTOM-UP-APPROACH]
// Time Complexity: O(n) // Space Complexity: O(n)  extraSpace: 'dpArray'

/*
noOfSteps ---->          0   1   2   3   4   5    6
noOfWays  ---->        [ 1,  1,  2,  3,  5,  8,  13]


######## How? ########

// Base Case:: f(1 steps) = 1 way, f(0 steps) = 1 way
for '0' steps --> u can make only one distinct way : take '0-step' (1 time) // which means doing nothing
for '1' steps --> u can make only one distinct way : take '1-step' (1 time)

noOfSteps ---->          0   1
noOfWays  ---->        [ 1,  1 ]


------------------------------------------------------------------------

if we can only take ('1-step' or '2-step' ) at a time
f(n) = f(n-1) + f(n-2)
------------------------------------------------------------------------

For '2' steps, f(2steps) ==> f(1steps) + f(0steps)
noOfSteps ---->          0   1   2
noOfWays  ---->        [ 1,  1,  2 ]
Ans: noOfWays ==> 2

For '3' steps, f(3steps) ==> f(2steps) + f(1steps)
noOfSteps ---->          0   1   2   3
noOfWays  ---->        [ 1,  1,  2,  3 ]
Ans: noOfWays ==> 3

For '4' steps, f(4steps) ==> f(3steps) + f(2steps)
noOfSteps ---->          0   1   2   3   4
noOfWays  ---->        [ 1,  1,  2,  3,  5]
Ans: noOfWays ==> 3

*/

function climbStairs(n) {
  // Base Case:: f(1 steps) = 1 way, f(0 steps) = 1 way
  const dp = [1, 1];

  // Note: 'n' is noOfSteps, iterate untill 'n steps' (NOT n-1 steps)
  for (let i = 2; i <= n; i++) {
    // if we can only take 1 or 2 steps
    // f(n) = f(n-1) + f(n-2)
    dp[i] = dp[i - 1] + dp[i - 2];
  }

  return dp[n];
}

// 6 steps
console.log(climbStairs(6)); // 13 ways
```
{% endtab %}

{% tab title="Sol3 \[BEST\]" %}
```javascript
// Sol3: [BEST] [SOLN2-EXTENDED] Without using 'dpArray' [DP: BOTTOM-UP-APPROACH]
// Time Complexity: O(n) // Space Complexity: O(1)
function climbStairs3(n) {
  let res = 0;
  // Base Case:: f(1 steps) = 1 way, f(0 steps) = 1 way
  // const dp = [1, 1];
  const prev = 1; // 0 steps
  let curr = 1; // 1 steps

  // Note: 'n' is noOfSteps, iterate untill 'n steps' (NOT n-1 steps)
  for (let i = 2; i <= n; i++) {
    const currTmp = curr; // store: 'curr'

    curr = curr + prev;

    // for nextIter, make the curr as 'prev'
    prev = currTmp;
  }

  return curr;
}

console.log(climbStairs3(6)); // 13 ways
```
{% endtab %}

{% tab title="Related" %}
11. House Robber
{% endtab %}
{% endtabs %}

## [9. Move Zeroes to Last](https://leetcode.com/problems/move-zeroes)

{% tabs %}
{% tab title="Question" %}
Given an array `nums`, write a function to move all `0`'s to the end of it while maintaining the relative order of the non-zero elements.

**Example:**

```text
Input: [0,1,0,3,12]
Output: [1,3,12,0,0]
```

**Note**:

1. You must do this **in-place** without making a copy of the array.
2. Minimize the total number of operations.
{% endtab %}

{% tab title="Video" %}
{% embed url="https://www.youtube.com/watch?v=1PEncepEIoE" %}

{% embed url="https://www.youtube.com/watch?v=PEr3JB9AAm0" %}
{% endtab %}

{% tab title="Code" %}
```javascript
// Sol2: [BEST] Swap '0' with values
// 1. move: 'currVal' to 'lastZeroIndex'
// 2. move: 'lastZeroIndexVal' to 'currIndex'
// Time Complexity: O(n)  // Space Complexity: O(1)

function moveZeroes(inputArr) {
  let lastZeroIndex = 0;

  for (let i = 0; i < inputArr.length; i++) {
    // if the 'currVal' is not 0, swap: 'currVal' with 'lastZeroIndex'
    if (inputArr[i] != 0) {
      //swap:
      const currVal = inputArr[i];
      const lastZeroIndexVal = inputArr[lastZeroIndex]; // always 'zero'

      // 1. move: 'currVal' to 'lastZeroIndex'
      inputArr[lastZeroIndex] = currVal; // arr[lastZeroIndex] <---- arr [currIndex]

      // 2. move: 'lastZeroIndexVal' to 'currIndex'
      inputArr[i] = lastZeroIndexVal; // arr[currIndex] <---- arr [lastZeroIndex]

      // assume: nextItem is 'zero'
      lastZeroIndex++;
    }
  }
}

const arr1 = [1, 2, 0, 4, 0, 3];
moveZeroes(arr1);
console.log(arr1); // [1, 2, 4, 3, 0, 0]
```
{% endtab %}

{% tab title="Result Walkthrough" %}
```bash
'*': lastZeroIndex
'#': currIndex

lastZeroIndex=0;

[1, 2, 0, 4, 0, 3] ==> (nonZeroItemFOund=> swap(currItem, lastZeroIndex)) [*#1, 2, 0, 4, 0, 3] ==> lastZeroIndex-->1
 *#                                                 0           0

[1, 2, 0, 4, 0, 3] ==> (nonZeroItemFOund=> swap(currItem, lastZeroIndex)) [1, *#2, 0, 4, 0, 3] ==> lastZeroInde-->2
    *#                                              1           1                                                


[1, 2, 0, 4, 0, 3] ==> lastZeroIndex-->2
       *#

[1, 2, 0, 4, 0, 3] ==> ==> (nonZeroItemFOund=> swap(currItem, lastZeroIndex)) [1, 2, #4, *0, 0, 3] ==> lastZeroIndex-->3
       *  #                                            3           2



[1, 2, 0, 4, 0, 3] ==> lastZeroIndex-->3
             *#

[1, 2, 0, 4, 0, 3] ==> ==> (nonZeroItemFOund=> swap(currItem, lastZeroIndex)) [1, 2, 4, #3, 0, *0] ==> lastZeroIndex-->4
             *  #                                        5           3

```
{% endtab %}
{% endtabs %}

## [10. Is this BinaryTree 'Symmetric' or Not](https://leetcode.com/problems/symmetric-tree)

{% tabs %}
{% tab title="Question" %}
101. Symmetric Tree

Given a binary tree, check whether it is a mirror of itself \(ie, symmetric around its center\).

For example, this binary tree `[1,2,2,3,4,4,3]` is symmetric:

```text
    1
   / \
  2   2
 / \ / \
3  4 4  3
```

But the following `[1,2,2,null,3,null,3]` is not:

```text
    1
   / \
  2   2
   \   \
   3    3
```

**Note:**  
Bonus points if you could solve it both recursively and iteratively.
{% endtab %}

{% tab title="QExplain" %}
```bash

    1
   / \
  2    2     ====> isSymmetric ==> true
 / \  / \
3  4  4  3


    1
   / \
  2    2     ====> isSymmetric ==> false
 / \  / \
3  4  5  3
```
{% endtab %}

{% tab title="Video" %}
{% embed url="https://www.youtube.com/watch?v=XV7Sg2hJO3Q" %}
{% endtab %}

{% tab title="Code" %}
```javascript

// Sol1: [BEST]:
// Time Complexity: O(n)
// Space Complexity: O(h)  extraSpace: reccursive-stack-space (h --> height of the Tree)
/*

------------------------------------------------------------------------
Formula or Rules:
------------------------------------------------------------------------

leftNode === null && rightNode == null
-or-
1. leftNode.val === rightNode.val
2. leftNode.right === rightNode.left
3. leftNode.left === rightNode.right

----
otherwise: false
-----------------------------------------------------------------------
*/

function isMirror(leftNode, rightNode) {
  // base case:
  // if bothNodes are 'null' // isSymmetric
  if (leftNode == null && rightNode == null) return true;

  // if oneNode is 'null' and otherNode is 'not-null' // isNotSymmetric
  if (leftNode == null || rightNode == null) return false;

  // if bothNodes has 'sameValue' and ..... // isSymmetric
  return (
    leftNode.val == rightNode.val &&
    isMirror(leftNode.right, rightNode.left) &&
    isMirror(leftNode.left, rightNode.right)
  );
}

function isSymmetric(root) {
  return isMirror(root, root);
}

class TreeNode {}
```
{% endtab %}
{% endtabs %}



## [11. House Robber](https://leetcode.com/problems/house-robber)

{% tabs %}
{% tab title="Question" %}
You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security system connected and **it will automatically contact the police if two adjacent houses were broken into on the same night**.

Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight **without alerting the police**.

**Example 1:**

```text
Input: [1,2,3,1]
Output: 4
Explanation: Rob house 1 (money = 1) and then rob house 3 (money = 3).
             Total amount you can rob = 1 + 3 = 4.
```

**Example 2:**

```text
Input: [2,7,9,3,1]
Output: 12
Explanation: Rob house 1 (money = 2), rob house 3 (money = 9) and rob house 5 (money = 1).
             Total amount you can rob = 2 + 9 + 1 = 12.
```
{% endtab %}

{% tab title="Video" %}
{% embed url="https://www.youtube.com/watch?v=xlvhyfcoQa4" %}
{% endtab %}

{% tab title="DP" %}
{% embed url="https://drive.google.com/open?id=1PbQDq9cd85p0UcLbVoAZ1heuqSrO8tTF4mq6swsGC5Q" %}
{% endtab %}

{% tab title="Sol1" %}
```javascript
/*
houseIndex      ---->           0   1   2   3   4
houseMoney      ---->         [ 2,  7,  9,  3,  1 ]
maxICanSteelSoFar(dpArr) -->  [ 2,  7, 11, 11,  12 ]
*/

// Sol1: Using 'dpArray' [DP: BOTTOM-UP-APPROACH]
// Time Complexity: O(n) // Space Complexity: O(n)  extraSpace: 'dpArray'

function rob(arr) {
  // base case:
  // if 'no-house', max i can steel is 0
  if (arr.length === 0) return 0;
  // if '1-house', max i can steel is '1stHouseMoney'
  if (arr.length === 1) return arr[0];

  // dpArr: maxICanSteelSoFar
  const dp = [];
  // if '1-house', max i can steel is '1stHouseMoney'
  dp[0] = arr[0];
  // if '2-houses', max i can steel is '1stHouseMoney' or '2ndHouseMoney' (whichever is maximum)
  dp[1] = Math.max(arr[0], arr[1]);

  for (let i = 2; i < arr.length; i++) {
    // with 'currHouseItem' + lastPossibleMax -- i can get 'currMaxIcanSteel'
    // why dp[i-2]? why not dp[i-1]? // becoz i cant steel previous house
    const currMaxTemp = arr[i] + dp[i - 2];

    // lastMaxIcanSteel
    const lastMaxTemp = dp[i - 1];

    // if: max('currMaxIcanSteel' or 'lastMaxIcanSteel')
    // that is the bestIcanSteel as of now
    dp[i] = Math.max(currMaxTemp, lastMaxTemp);
  }

  return dp[dp.length - 1];
}

console.log(rob([2, 7, 9, 3, 1]));
```
{% endtab %}

{% tab title="Sol2\[BEST\]" %}
```javascript
// if we  clearly see, we dont need to maintain to track all the house 'bextIcanSteel'

// Soln2: without using 'dpArray' [SOL1-EXTENDED] [DP: BOTTOM-UP-APPROACH]
// Time Complexity: O(n) // Space Complexity: O(1)
function rob(arr) {
  // base case:
  // if 'no-house', max i can steel is 0
  if (arr.length === 0) return 0;
  // if '1-house', max i can steel is '1stHouseMoney'
  if (arr.length === 1) return arr[0];

  // lastMaxIcanSteel
  let lastMax = arr[0];
  // currMaxIcanSteel
  let currMax = Math.max(arr[0], arr[1]);

  for (let i = 2; i < arr.length; i++) {
    // with 'currHouseItem' + lastPossibleMax -- i can get 'currMaxIcanSteel'
    // why dp[i-2]? why not dp[i-1]? // becoz i cant steel previous house
    const currMaxTemp = arr[i] + lastMax;

    // lastMaxIcanSteel
    const lastMaxTemp = currMax;

    // if: max('currMaxIcanSteel' or 'lastMaxIcanSteel')
    // that is the bestIcanSteel as of now
    currMax = Math.max(currMaxTemp, lastMaxTemp);

    lastMax = lastMaxTemp;
  }

  return currMax;
}

```
{% endtab %}
{% endtabs %}

## [12. Is 'Palindrome' Linked List](https://leetcode.com/problems/palindrome-linked-list)

{% tabs %}
{% tab title="Question" %}
Given a singly linked list, determine if it is a palindrome.

**Example 1:**

```text
Input: 1->2
Output: false
```

**Example 2:**

```text
Input: 1->2->2->1
Output: true
```

**Follow up:**  
Could you do it in O\(n\) time and O\(1\) space?
{% endtab %}

{% tab title="Video" %}
{% embed url="https://www.youtube.com/watch?v=oZuR2-AKkXE&t=148s" %}
{% endtab %}

{% tab title="Code" %}
```javascript

/*
 1. split: into two LinkedList
 2. reverse: the 'secondLinkedList' 
 3. compare: 'firstLinkedList' & 'secondLinkedList'

 How do we 'split into two LinkedList'?
    1.1 find the 'middleNode' (using slowPtr & fastPtr)
        -when 'fastPtr' reaches "lastNode", 'slowPtr' will reach the "middleNode"
        - cornerCase:  for 'odd' noOfItems, ignore the 'middleNode'

    1.2 so the 'middleNode' is our 'secondLinkedListHead'
    
*/
// Time complexity : O(n) // Space complexity : O(1)  
// Note: noExtraSpaceUsed:  we didn't create any extra space for secondLinkedList
function isPalindrome(head) {

  // 1. split: into two LinkedList
  // 1.1 find the 'middleNode' (using slowPtr & fastPtr)
  let slow = head;
  let fast = head;
  while (fast != null && fast.next != null) {
    slow = slow.next;
    fast = fast.next.next;
  }
  // 1.2
  let middleNode = slow;
  if (fast != null) {
    // if 'fast' is notNull then is oddList, ignore the 'middleNode'
    middleNode = slow.next;
  }

  // 2. reverse: the 'secondLinkedList'
  let secondLinkedListHead = reverse(middleNode);
  let firstLinkedListHead = head;

  // 3. compare: 'firstLinkedList' & 'secondLinkedList'
  while (secondLinkedListHead != null) {
    if (firstLinkedListHead.val != secondLinkedListHead.val) {
      return false;
    }
    firstLinkedListHead = firstLinkedListHead.next;
    secondLinkedListHead = secondLinkedListHead.next;
  }
  return true;
}


// Time complexity : O(n) // Space complexity : O(1)
function reverse(head) {
  let prev = null;
  let curr = head;

  // iterate: until lastNode
  while (curr != null) {
    let nextTemp = curr.next;

    // reverse:
    curr.next = prev;

    // next: iteration
    prev = curr;
    curr = nextTemp;
  }
  return prev;
}

```
{% endtab %}
{% endtabs %}

## [13. Diameter of Binary Tree](https://leetcode.com/problems/diameter-of-binary-tree)

{% tabs %}
{% tab title="Question" %}
* Longest Path between any two points of the Circle is "Diameter of the Circle"
* **'Longest Path' between any two nodes** of the Tree is "Diameter of the Tree"

Given a binary tree, you need to compute the length of the diameter of the tree. The diameter of a binary tree is the length of the '**longest path' between any two nodes in a tree**. This path may or may not pass through the root.

**Example:**  
Given a binary tree  


```text
          1
         / \
        2   3
       / \     
      4   5    
```

Return **3**, which is the length of the path \[4,2,1,3\] or \[5,2,1,3\].

**Note:** The length of path between two nodes is represented by the number of edges between them.
{% endtab %}

{% tab title="Video" %}
{% embed url="https://www.youtube.com/watch?v=ey7DYc9OANo" %}
{% endtab %}

{% tab title="Code" %}
```javascript
/*
'Longest Path' between any two nodes of the Tree is "Diameter of the Tree"

1. Find which 'node' has 'maxDiameter'

   # How to find maxDiameter?
   find: 'diameter' for eachNode in the BinaryTree
   diameter = leftTreeHeight + rightTreeHeight

    # How to find that 'heightOfTree'?
    heightOfTree = max(leftTreeHeight, rightTreeHeight) + 1

2. When you find 'diameter' eachNode, update the 'sofarMaxDiameter'
*/

function height(currNode, sofarMaxDiameter) {
  // base case:
  if (currNode == null) {
    return 0;
  }

  const leftTreeHeight = height(currNode.left, sofarMaxDiameter);
  const rightTreeHeight = height(currNode.right, sofarMaxDiameter);

  // also update: sofarMaxDiameter
  const currDiameter = leftTreeHeight + rightTreeHeight;
  sofarMaxDiameter.val = Math.max(sofarMaxDiameter.val, currDiameter);

  // heightOfTree
  return Math.max(leftTreeHeight, rightTreeHeight) + 1;
}

function diameterOfBinaryTree(root) {
  const sofarMaxDiameter = { val: 0 };
  height(root, sofarMaxDiameter);
  return sofarMaxDiameter.val;
}
```
{% endtab %}
{% endtabs %}

## [14. Linked List has 'Cycle'](https://leetcode.com/problems/linked-list-cycle)

{% tabs %}
{% tab title="Question" %}
Given a linked list, determine if it has a **cycle** in it.

To represent a cycle in the given linked list, we use an integer `pos` which represents the position \(0-indexed\) in the linked list where tail connects to. If `pos` is `-1`, then there is no cycle in the linked list.

**Example 1:**

```text
Input: head = [3,2,0,-4], pos = 1
Output: true
Explanation: There is a cycle in the linked list, where tail connects to the second node.
```

![](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist.png)

**Example 2:**

```text
Input: head = [1,2], pos = 0
Output: true
Explanation: There is a cycle in the linked list, where tail connects to the first node.
```

![](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test2.png)

**Example 3:**

```text
Input: head = [1], pos = -1
Output: false
Explanation: There is no cycle in the linked list.
```

![](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test3.png)
{% endtab %}

{% tab title="Video" %}
{% embed url="https://www.youtube.com/watch?v=zbozWoMgKW0" %}

[https://www.youtube.com/watch?v=MFOAbpfrJ8g](https://www.youtube.com/watch?v=MFOAbpfrJ8g)
{% endtab %}

{% tab title="Sol1" %}
```javascript
/*
Sol1: Using 'HashSet'

// Time complexity : O(n)
// Space complexity : O(n)  extraSpace: for 'Set'
*/
function hasCycle(head) {
  const nodesSeen = new Set();
  while (head != null) {
    if (nodesSeen.has(head)) {
      // it has a 'loop'
      return true;
    } else {
      nodesSeen.add(head);
    }
    head = head.next;
  }

  // it doesnt have a 'loop'
  return false;
}
```
{% endtab %}

{% tab title="Sol2: \[BEST\]" %}
```javascript
/*
Sol2: [BEST] Using 'slow & fast' pointers

// Time complexity : O(n + k) k: no-of-iterations-to-reach-slow-and-fast-node
// Space complexity : O(n)  extraSpace: for 'Set'
*/
function hasCycle(head) {
  if (head == null || head.next == null) {
    return false;
  }

  let slow = head;
  let fast = head;

  // if: anyone reaches 'NULL', that is end of LL, so 'NO-LOOP' availble
  while (slow && fast && fast.next) {
    slow = slow.next;
    fast = fast.next.next;

    if (slow === fast) {
      // if it is a 'LOOP', at some iteration 'slow' & 'fast' will point to the sameNode
      return true;
    }
  }
  return false;
}

```
{% endtab %}
{% endtabs %}



## [15. Majority Element](https://leetcode.com/problems/majority-element)

{% tabs %}
{% tab title="Question" %}
...
{% endtab %}

{% tab title="Video" %}
{% embed url="https://www.youtube.com/watch?v=zOyOwDEF1Rc" %}
{% endtab %}

{% tab title="Sol1" %}
```javascript
/*
Sol1: Using 'HashMap'
*/
// Time complexity : O(n) // Space complexity : O(n)  extraSpace: for 'Map'
function majorityElement(nums) {
  let majorityItem = 0;
  const countMap = new Map();

  for (const no of nums) {
    if (countMap.has(no)) {
      // existing
      countMap.set(no, countMap.get(no) + 1);
    } else {
      // new
      countMap.set(no, 1);
    }
    if (countMap.get(no) > nums.length / 2) {
      majorityItem = no;
      break;
    }
  }

  return majorityItem;
}
```
{% endtab %}

{% tab title="Sol2" %}
```javascript
/*
Sol2: Using 'Sort'
*/
// Time complexity : O(nlogn) // Space complexity : O(1)
function majorityElement(nums) {
  // sort
  nums.sort((a, b) => a - b);
  // middleItem
  return nums[Math.floor(nums.length / 2)];
}

```
{% endtab %}

{% tab title="Sol3: \[BEST\]" %}
```javascript
/*
Sol3: [BEST] Boyer-Moore Voting Algorithm
Assumption: majorityElement always exists in the array
*/
// Time complexity : O(n) // Space complexity : O(1)
function majorityElement(array) {
  // Step 1: Find max element
  let winnerCandidate = null;
  let winnerCandidateVoteCount = 0;

  for (let i = 0; i < array.length; i++) {
    if (winnerCandidateVoteCount === 0) {
      // assume: currItem is our 'winnerCandidate'
      winnerCandidate = array[i];
      winnerCandidateVoteCount = 1;
    } else {
      if (winnerCandidate === array[i]) {
        // saw: 'winnerCandidateVote'
        // increment: 'winnerCandidateVoteCount'
        winnerCandidateVoteCount++;
      } else {
         // saw: 'otherCandidateVote'
        // decrement: 'winnerCandidateVoteCount'
        winnerCandidateVoteCount--;
      }
    }
  }

  return winnerCandidate;
}
```
{% endtab %}

{% tab title="Sol3: \[Modified\]" %}
```javascript
/*
Sol3: [BEST] Boyer-Moore Voting Algorithm
Assumption: 'majorityElement' may or may not exists in the array
*/
function majorityElementModified(array) {

  // Step 1: Find 'winnerCandidate'
  let winnerCandidate = null;
  let winnerCandidateVoteCount = 0;

  for (let i = 0; i < array.length; i++) {
    if (winnerCandidateVoteCount === 0) {
      // assume: currItem is our 'winnerCandidate'
      winnerCandidate = array[i];
      winnerCandidateVoteCount = 1;
    } else {
      if (winnerCandidate === array[i]) {
        // saw: 'winnerCandidateVote'
        // increment: 'winnerCandidateVoteCount'
        winnerCandidateVoteCount++;
      } else {
         // saw: 'otherCandidateVote'
        // decrement: 'winnerCandidateVoteCount'
        winnerCandidateVoteCount--;
      }
    }
  }


  if (winnerCandidateVoteCount == 0) {
    // 'winnerCandidate' not found
    return null;
  }

  // Step 2: double-check if 'winnerCandidate' is majority element?
  let finalCount = 0;
  for (let i = 0; i < array.length; i++) {
    if (winnerCandidate == array[i]) {
      finalCount++;
    }
  }

  // if: finalCount > n.length/2 --> 'winnerCandidate' found
  return finalCount > array.length / 2 ? winnerCandidate : null;
}

```
{% endtab %}

{% tab title="Related" %}
[https://leetcode.com/problems/majority-element-ii/](https://leetcode.com/problems/majority-element-ii/)

[https://leetcode.com/problems/check-if-a-number-is-majority-element-in-a-sorted-array/](https://leetcode.com/problems/check-if-a-number-is-majority-element-in-a-sorted-array/)
{% endtab %}
{% endtabs %}

## [16. Single Number](https://leetcode.com/problems/single-number)

{% tabs %}
{% tab title="Question" %}
Given a **non-empty** array of integers, every element appears _twice_ except for one. Find that single one.

**Note:**

Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

**Example 1:**

```text
Input: [2,2,1]
Output: 1
```

**Example 2:**

```text
Input: [4,1,2,1,2]
Output: 4
```
{% endtab %}

{% tab title="Video" %}
{% embed url="https://www.youtube.com/watch?v=-\_6l\_ijmcgs" %}

[https://www.youtube.com/watch?v=CvnnCZQY2A0](https://www.youtube.com/watch?v=CvnnCZQY2A0)
{% endtab %}

{% tab title="Sol1" %}
```javascript
/*
Sol1: Using 'HashMap'
*/
// Time complexity : O(n) // Space complexity : O(n)  extraSpace: for 'hashSet'
function singleNumber(nums) {
  const hashSet = new Set();
  for (let no of nums) {
    if (hashSet.has(no)) {
      hashSet.delete(no);
    } else {
      hashSet.add(no);
    }
  }

  const itr1 = hashSet.values();
  const result = itr1.next().value;
  return result;
}

```
{% endtab %}

{% tab title="Sol2: \[BEST\]" %}
```javascript
/*
Sol2: [BEST] Using Bit Manipulation - 'XOR'
*/
// Time complexity : O(n) // Space complexity : O(1)
function singleNumber(nums) {
  let result = 0;
  for (let no of nums) {
    // xor:
    result ^= no;
  }
  return result;
}
```
{% endtab %}
{% endtabs %}



## [17. Intersection of Two Linked Lists](https://leetcode.com/problems/intersection-of-two-linked-lists)

{% tabs %}
{% tab title="Question" %}
...
{% endtab %}

{% tab title="Video" %}
{% embed url="https://www.youtube.com/watch?v=\_7byKXAhxyM" %}
{% endtab %}

{% tab title="Sol1" %}
```javascript
/*
Sol1: Using 'HashSet'
*/
// Time complexity : O(n) // Space complexity : O(n)  extraSpace: for 'hashSet'
function getIntersectionNode(headA, headB) {
  let hashSet = new Set();

  // add: 'aLinkedList' allItems in hashSet
  let pa = headA;
  while (pa != null) {
    hashSet.add(pa);
    pa = pa.next;
  }

  if (hashSet.size === 0) {
    return null;
  }

  let pb = headB;
  while (pb != null) {
    if (hashSet.has(pb)) {
      // inter-section: found
      return pb;
    }
    pb = pb.next;
  }

  // no: inter-section: found
  return null;
}

```
{% endtab %}

{% tab title="Sol2: \[BEST\]" %}
```javascript
/*
Sol2: Using 'lengthOfLinkedList'
*/
// Time complexity : O(n) // Space complexity : O(1)
function lengthOfLinkedList(x) {
  let count = 0;
  while (x != null) {
    x = x.next;
    count++;
  }
  return count;
}

function getIntersectionNode(headA, headB) {
  let aLen = lengthOfLinkedList(headA);
  let bLen = lengthOfLinkedList(headB);

  if (aLen > bLen) {
    const diff = aLen - bLen;
    for (let i = 0; i < diff; i++) {
      headA = headA.next;
    }
  } else {
    const diff = bLen - aLen;
    for (let i = 0; i < diff; i++) {
      headB = headB.next;
    }
  }

  // iteratte: until inter-section found
  while (headA != headB) {
    headA = headA.next;
    headB = headB.next;
  }
  return headA;
}
```
{% endtab %}
{% endtabs %}



## [18. Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree)

{% tabs %}
{% tab title="Question" %}
* **'height'** of the Tree is the **maxDepth** of the Tree
{% endtab %}

{% tab title="Video" %}
{% embed url="https://www.youtube.com/watch?v=YT1994beXn0" %}
{% endtab %}

{% tab title="Code" %}
```javascript
// or heightOfBinaryTree
// Time complexity : O(n) 
// Space Complexity: O(h)  extraSpace: reccursive-stack-space (h --> height of the Tree)
function maxDepth(currNode) {
  // base case:
  if (currNode == null) {
    return 0;
  }

  let leftTreeHeight = maxDepth(currNode.left);
  let rightTreeHeight = maxDepth(currNode.right);

  return Math.max(leftTreeHeight, rightTreeHeight) + 1;
}

```
{% endtab %}

{% tab title="Related" %}
* [13. Diameter of Binary Tree](https://leetcode.com/problems/diameter-of-binary-tree)
{% endtab %}
{% endtabs %}

## [19. Find All Numbers Disappeared in an Array](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array)

{% tabs %}
{% tab title="Question" %}
...
{% endtab %}

{% tab title="Video" %}
{% embed url="https://www.youtube.com/watch?v=GHfmIz5ZnWk" %}

[https://www.youtube.com/watch?v=N6uiqEbF0o0](https://www.youtube.com/watch?v=N6uiqEbF0o0)
{% endtab %}

{% tab title="Sol1" %}
```javascript
/*
Sol1: [EASY] Using HashSet
[WRONG] But it uses extraSpace
*/
// Time complexity : O(n) // Space complexity : O(n)  extraSpace: for 'hashSet'
function findDisappearedNumbers(nums) {
  let result = [];
  const hashSet = new Set(nums);

  for (let i = 0; i < nums.length; i++) {
    const val = i + 1;  
    if (!hashSet.has(val)) {
      result.push(val);
    }
  }
  return result;
}
```
{% endtab %}

{% tab title="Sol2: \[BEST\]" %}
```javascript
/*
Sol2: [BEST] By Marking arrIndex's value as 'NEGATIVE'
arr[absVal-1] = -arr[absVal-1];

If i see a number, marking that numbr's --> array[index]'s value as 'NEGATIVE'
E.g. saw, numbr: 8 --> arr[8-1] = - arr[8-1]

- In this way all the numbers that we have seen will be marked as negative. 
- In the second iteration, if a value is not marked as negative (if we find a +ve numbr)
    - That means 'thatIndex + 1' is a disappeared value
    - so just add it to the resul list.
*/

// Time complexity : O(n) // Space complexity : O(1)
function findDisappearedNumbers(nums) {
  let result = [];

  // 1. marking: all the appeard numbers --> array[index]'s --> value as 'NEGATIVE'
  for (let i = 0; i < nums.length; i++) {
    let targetIndex = Math.abs(nums[i]) - 1;
    if (nums[targetIndex] > 0) {
      nums[targetIndex] = -nums[targetIndex];
    }
  }

  // 2. find: index which has a positiveNo (that 'index+1' --is a--> disappearedVal)
  for (let i = 0; i < nums.length; i++) {
    if (nums[i] > 0) {
      // positiveNo: found // disappearedVal = index + 1
      result.push(i + 1);
    }
  }

  return result;
}

```
{% endtab %}
{% endtabs %}

## [20. Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree)

{% tabs %}
{% tab title="Question" %}
...
{% endtab %}

{% tab title="Video" %}
{% embed url="https://www.youtube.com/watch?v=vdwcCIkLUQI" %}
{% endtab %}

{% tab title="Code" %}
```javascript
/*
Sol1: Using Recursion
*/
// Time Complexity: O(n) 
// Space Complexity: O(h)  extraSpace: reccursive-stack-space (h --> height of the Tree)
function invertTree(root) {
  if (root == null) {
    return null;
  }
  const rightTmp = invertTree(root.right);
  const leftTmp = invertTree(root.left);
  root.left = rightTmp;
  root.right = leftTmp;
  return root;
}

/*
function invertTree(root) {
  if (root == null) return null;
  root.left = invertTree(root.right);
  root.right = invertTree(root.left);
  return root;
}
*/
```
{% endtab %}
{% endtabs %}



## [21. Merge Two Binary Trees](https://leetcode.com/problems/merge-two-binary-trees)

{% tabs %}
{% tab title="Question" %}
...
{% endtab %}

{% tab title="Video" %}
{% embed url="https://www.youtube.com/watch?v=p3vVYNngyxs" %}
{% endtab %}

{% tab title="Code" %}
```javascript
/*
617. Merge Two Binary Trees

https://leetcode.com/problems/path-sum-iii/
https://www.youtube.com/watch?v=p3vVYNngyxs
*/

/*
 Sol1: Using Recursion
*/
// Time complexity : O(m) A total of 'm' nodes need to be traversed.
// Here, 'm' represents the minimum number of nodes from the two given trees.

// Space complexity : O(m) The depth of the recursion tree can go upto 'm' in the case of a skewed tree.
// In average case, depth will be O(log m)
function mergeTrees(t1, t2) {
  // base-case:
  if (t1 == null) return t2;
  if (t2 == null) return t1;
  
  // merge: sum
  t1.val = t1.val + t2.val;

  t1.left = mergeTrees(t1.left, t2.left);
  t1.right = mergeTrees(t1.right, t2.right);
  return t1;
}

```
{% endtab %}
{% endtabs %}



## [22. Path Sum III](https://leetcode.com/problems/path-sum-iii)

{% tabs %}
{% tab title="Question" %}
...
{% endtab %}

{% tab title="Video" %}

{% endtab %}

{% tab title="Code" %}
```javascript
....
```
{% endtab %}
{% endtabs %}

## [23. Shortest Unsorted Continuous Subarray](https://leetcode.com/problems/shortest-unsorted-continuous-subarray)

{% tabs %}
{% tab title="Question" %}
...
{% endtab %}

{% tab title="Video" %}
{% embed url="https://www.youtube.com/watch?v=Hg03KTli9co" %}
{% endtab %}

{% tab title="Code" %}
```javascript
/*
581. Shortest Unsorted Continuous Subarray

https://leetcode.com/problems/shortest-unsorted-continuous-subarray/
https://www.youtube.com/watch?v=Hg03KTli9co
*/

/*
 Sol1: Using minIndex & maxIndex
*/
// Time complexity : O(n) // Space complexity : O(1)
function findMinIndex(array, minElement, startIndex) {
  for (let i = 0; i < startIndex; i++) {
    if (minElement < array[i]) {
      return i;
    }
  }
  return startIndex;
}

function findMaxIndex(array, maxElement, endIndex) {
  for (let i = array.length - 1; i > endIndex; i--) {
    if (maxElement > array[i]) {
      return i;
    }
  }
  return endIndex;
}

function findUnsortedSubarray(array) {
  let n = array.length;

  // find: firstOccurence of unSortedArr from 'firstItem'
  let startIndex = 0;
  for (let i = 0; i < n - 1; i++) {
    if (array[i] > array[i + 1]) {
      startIndex = i;
      break;
    }
  }

  // find: firstOccurence of unSortedArr from 'lastItem'
  let endIndex = 0;
  for (let j = n - 1; j > 0; j--) {
    if (array[j - 1] > array[j]) {
      endIndex = j;
      break;
    }
  }

  // Find the minimum and maximum element in the sub array from startIndex to endIndex.
  let maxElement = array[startIndex];
  let minElement = array[startIndex];

  for (let i = startIndex + 1; i <= endIndex; i++) {
    if (maxElement < array[i]) {
      maxElement = array[i];
    }
    if (minElement > array[i]) {
      minElement = array[i];
    }
  }

  // Search the sorted array from 0 to startIndex
  // to find the index at which minimum element will be in sorted array say, minIndex.
  let minIndex = findMinIndex(array, minElement, startIndex);

  // Search the sorted array from endIndex to end of array
  // to find the index at which maximum element will be in sorted array say, maxIndex.
  let maxIndex = findMaxIndex(array, maxElement, endIndex);

  // Sub array between minIndex to maxIndex is the required sub array.
  if (minIndex == maxIndex) {
    console.log("The array is already sorted.");
    return 0;
  } else {
    let subArrLength = 0;
    // Sub array between minIndex to maxIndex is the required sub array.
    for (let i = minIndex; i <= maxIndex; i++) {
      subArrLength++;
    }
    return subArrLength;
  }
}

```
{% endtab %}
{% endtabs %}

..

