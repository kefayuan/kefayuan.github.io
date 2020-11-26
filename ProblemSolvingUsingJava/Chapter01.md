---
layout: page
title:  Tools and Measurement 
---

# Measurement
> If you can't measure it, you can't improve it.
>
> -- <cite>Peter Drucker</cite> 


Criteria:CPR(Correctness, Performance, Readability)  

Many problems have more than one solutions. As of a software problem, it is more often that the problem has different algorithms to implement it, e.g. sort. There are many different sorting methods, for a instance, the following two code snippets.  
```java
public void bubbleSort(int[] arr) {  
    int n = arr.length;  
    int temp = 0;  
    for(int i=0; i < n; i++){  
        for(int j=1; j < (n-i); j++){  
             if(arr[j-1] > arr[j]){  
                  //swap  
                  temp = arr[j-1];  
                  arr[j-1] = arr[j];  
                  arr[j] = temp;  
             }    
        }  
   }  
}  
```
```java
public void quickSort(int arr[], int begin, int end) {
  if (begin < end) {
    int partitionIndex = partition(arr, begin, end);
    quickSort(arr, begin, partitionIndex-1);
    quickSort(arr, partitionIndex+1, end);
    }
}
private int partition(int arr[], int begin, int end) {
    int pivot = arr[end];
    int i = (begin-1);
    for (int j = begin; j < end; j++) {
        if (arr[j] <= pivot) {
            i++;
            int temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;
        }
    }
    int temp = arr[i+1];
    arr[i+1] = arr[end];
    arr[end] = temp;
    
    return i+1;
}
```
These two kinds of sorting can solve your problem, but which one is more efficient? How do you know it without running the code to test it?  
In computer science, the concept Complexity is used to analyze the efficiency: time complexity and space complexity. Time complexity describes the amount of time it takes to run an algorithm. Space complexity measures how much memory an algorithms needs when running an algorithm.  

# Tools



