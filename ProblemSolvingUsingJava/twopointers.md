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
Fast-Slow-Pointers is also called "tortoise and the hare algorithm" which was degigned by Robert W. Floyd and used originally to detect cycles in a directed graph. 
Floyd's Cycle Detection Algorithm(The Tortoise and The Hare)  
Brent's Cycle Detection Algorithm(The Teleporting Turtle)   
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
 
### [Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/)  
> Given n non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it can trap after raining. 
> 
> 
> **Example 1:**  
> ![](images/rainwatertrap.png)
> **Input:** height = [0,1,0,2,1,0,1,3,2,1,2,1]"  
> **Output:** 6  
> **Explaination:** The above elevation map (black section) is represented by array [0,1,0,2,1,0,1,3,2,1,2,1]. In this case, 6 units of rain water (blue section) are being trapped.
> 
> **Example 2:**  
> **Input:**  height = [4,2,0,3,2,5]  
> **Output:**  9 
> 
> **Constraints:**
> * n == height.length  
> * 0 <= n <= 3 * 104
> * 0 <= height[i] <= 105
>  

### Analyisis
Text  
Ilustration 


```java
public static int trap(int[] height){
    if(Objects.isNull(height)||height.length==0){
        return 0;
    }
    int left=0, right =height.length -1;
    int leftMax =height[left];
    int rightMax=height[right];
    int res = 0;
    while (left < right){
        if(leftMax < rightMax){
           res += leftMax - height[left];
           left++;
           leftMax = max( leftMax ,height[left]);
        }else{
           res += rightMax - height[right];
           right--;
           rightMax = max( rightMax, height[right]);
        }
    }
    return res;
    }
```
 
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
 
### Problem:
### [Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/)
> Given two strings s and t, return the minimum window in s which will contain all the characters in t. If there is no such window in s that covers all characters in t, return the empty string "".  
> 
> **Note** that If there is such a window, it is guaranteed that there will always be only one unique minimum window in s.  
> 
> 
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

### Analyisis
Text  
best practice using hashmap..  
Ilustration 


```java
public static String minWindow(String s, String t) {
   //key:value -> the frequency of char in t
    Map<Character, Long> tTable = Collections.unmodifiableMap(
           t.chars().mapToObj(ch -> (char) ch)
                   .collect(Collectors.groupingBy(Character::valueOf, Collectors.counting()))
   );

    //key:value -> the frequency of char in window
   Map<Character, Long> winTable=new HashMap();
   int winLeft = 0, winRight = 0;
   int winHits = 0;

   // the start and end index of result in s
   int start = 0,winLength = s.length()+1; //set any impossible value for default window size

   while (winRight < s.length()) {
       // rightChar is the next char expanded into window
       char rightChar = s.charAt(winRight);
       // expand window
       winRight++;
       // if char is valid, record it and update window table
       if (tTable.containsKey(rightChar)) {
           winTable.put(rightChar, winTable.getOrDefault(rightChar, 0l) + 1);
           if (winTable.get(rightChar).equals(tTable.get(rightChar))){
               winHits++;
           }
       }
       // t pattern exists in the window, but the window is not minimized yet
       while (winHits == tTable.size()) {
           //temporally record the result, it might be the minimized, but not sure.
          if (winRight - winLeft < winLength) {
              //currently the minimized substring
               start = winLeft;
               winLength = winRight - winLeft;
           }

           // leftChar will be deleted from window, which means window move to the left
           char leftChar = s.charAt(winLeft);
           // shrink window
           winLeft++;
           // try to find update window table
           if (tTable.containsKey(leftChar)) {
               if (winTable.get(leftChar).equals(tTable.get(leftChar)) ){
                   winHits--;
               }
               winTable.put(leftChar, winTable.get(leftChar) - 1);
           }
       }
   }

    boolean founded = winLength <  s.length()+1;
    if (founded){
        return s.substring(start, start+winLength);
    } else {
        return "";
    }
}
```
          s="cabwefgewcwaefgcf"  
          t="cae"  
          expected="cwae"  

