---
layout: page
title: Two Pointers
---
# Introduction

Pointer in java is just index, because java does not have a true pointer. Two pointers algrithm is often used for index-based data structure, esp. array or some lists.
In terms of direction of the two pointers, there are fast-slow-pointers, left-right-pointers. Sliding-window-pointers is a special case for fast-slow-pointers.  
The two pointers in fast-slow-pointers move in the same direction, one fast, the other slow, while the two pointers in left-right-pointers move in the different direction, left pointer move to the right, and right-pointer move to the left. Sliding-window-pointers keep a window during the two pointers move.  
Fast-slow-pointers can be used to detect cycle problem. Left-right-pointers is more ofte used in string and array problem. Sliding-window-pointers can solve most of substring problem. 


The basic idea for using two pointers:  
1. initial locations.  
2. move strategy.  
3. exit conditions for iteration.    

# Fast-Slow-Pointers
The two pointers move from the same side. One moves fast, while the other move slow, e.g. the fast pointer move 2 steps each time, and the slow just 1 step. Both pointers move with the different move strategy until the two pointers point to the same element or other exit conditions.  
Illustraion for fast-slow-pointers  
### Solution Template 
1. initial locations, usually slow = 0, fast = 1 for the index.  
2. move strategy, e.g, slow++, fast +=2.  
3. exit conditions for iteration, in most cases, the fast pointer catch up the slow pointer.    

### Problem Types
 * detect if a list contians cycle
 * if a list contains cycle, find the start location of the cycle
 * delete elements
 * find the middle element in list
 * find the last k element in list

### Problems
 * 283, 27, 26-80, 141 

# Left-Right-Pointers
The two pointers stay in different sides of an ordered array, usually one is in left, the other right, that's also the reason why it is called left-right-pointers. The two pointers then start to meet.  
Illustraion for  left-right-pointers  
### Solution Template  
1. initial locations, usually left = 0, right = length - 1 for the index.  
2. move strategy, e.g, left++, right--.  
3. exit conditions for iteration, in most castes, the exit condition is right < left.  

### Problem Types
 * part sum in ordered array
 * reverse array  
 * binary search
 
### Problems
 * 167, 125, 344, 345, 11, 633 
 
# Sliding-Window-Pointers
Window is a collection of elements defined by start and end index in an array or a string, the start and end index are inclusive range, e.g. for index betwen i and j, [i,j], j-i is called distance. Sliding window slide with the fixed distance. If the window slide 1 element, the window index  range change from [i,j] to [i+1, j+1]. Using sliding window, the double nested loop can be converted into a single layer iteration, which change the 2-dimensional loop to 1-dimensional loop, this means the time complexity can be degraded from O(n<sup>2</sup>) to O(n).  
Illustraion for sliding-window-pointers  

### Solution Template
 1. initial locations. Usually left = 0, right = -1, the inclusive range [left,right] is the window.  
 2. move strategy. This is the most hard part for sliding-window-pointers. 
   - expand the window: increase right pointer until the elements in the window satify the requirement and find a solution.
   - shrink the window: increase left pointer until the elements in the window don't satify the requirement any more.
   - find next possible solution. put left pointer forward, repeat the expand and shrink step.
 3. exit conditions for iteration. Right ponter reach the end, iteration finished.

```java
int left = 0, right = 0;
while (right < s.size()) {`
    // expand window
    window.add(s[right]);
    right++;

    while (window needs shrink) {
        // shrink window
        window.remove(s[left]);
        left++;
    }
}
```
### Problem Types
 * substring or subarray 
 
### Problems
 * 209, 3, 438, 76
 
### Problem on Leetcode: Minimum Window Substring  
> Given two strings s and t, return the minimum window in s which will contain all the characters in t. If there is no such window in s that covers all characters in t, return the empty string "".  
> 
> **Note** that If there is such a window, it is guaranteed that there will always be only one unique minimum window in s.  
> **Example 1:**  
> **Input:** s = "ADOBECODEBANC", t = "ABC"  
> **Output:** "BANC" 
> 
> **Example 2:**  
> **Input:** s = "a", t = "a"  
> **Output:** "a"  
> 
> **Constraints:**
> * 1 <= s.length, t.length <= 105  
> * s and t consist of English letters. 
> 
> **Follow up:** Could you find an algorithm that runs in O(n) time?
 

