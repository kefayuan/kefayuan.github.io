---
layout: page
title: Two Pointers
---
# Introduction

Pointer in java is just index, because java does not have a true pointer. Two pointers algrithm is often used for index-based data structure, esp. array or some lists.
In terms of direction of the two pointers, there are fast-slow-pointers, left-right-pointers. Sliding-window-pointers is a special case for fast-slow-pointers.  
The two pointers in fast-slow-pointers move in the same direction, one fast, the other slow, while the two pointers in left-right-pointers move in the different direction, left pointer move to the right, and right-pointer move to the left. Sliding-window-pointers keep a window during the two pointers move.  
Fast-slow-pointers can be used to detect cycle problem. Left-right-pointers is more ofte used in string and array problem. Sliding-window-pointers can solve most of substring problem. 
Illustraion for fast-slow-pointers, left-right-pointers, and sliding-window-pointers  

The basic idea for using two pointers:  
1. initial locations  
2. move strategy 
3. exit conditions for iteration  

# Fast-Slow-Pointers
The two pointers move from the same side. One moves fast, while the other move slow, e.g. the fast pointer move 2 steps each time, and the slow just 1 step. Both pointers move with the different move strategy until the two pointers point to the same element or other exit conditions.
### Problem Types
 * detect if a list contians cycle
 * if a list contains cycle, find the start location of the cycle
 * delete elements
 * find the middle element in list
 * find the last k element in list

