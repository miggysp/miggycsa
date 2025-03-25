---
layout: post
title: Sorting Team Teach HW
courses: {'csa': {'week': 6}}
comments: true
type: blogs
permalink: /sortingHW
---


```java
public class SortDemo {

    public static void main(String[] args) {
        int[] arr = {42, 17, 29, 8, 35};
        int comparisons = 0;
        int swaps = 0;

        System.out.println("Original Array:");
        printArray(arr);

        // Insertion Sort Logic
        for (int i = 1; i < arr.length; i++) {
            int key = arr[i];
            int j = i - 1;

            System.out.println("\nInserting " + key + ":");

            while (j >= 0 && arr[j] > key) {
                comparisons++;
                arr[j + 1] = arr[j]; // Shift element right
                j--;
                swaps++;
                printArray(arr);
            }

            // One last comparison if condition fails
            if (j >= 0) comparisons++;

            arr[j + 1] = key;
            printArray(arr);
        }

        System.out.println("\nSorted Array:");
        printArray(arr);
        System.out.println("\nTotal Comparisons: " + comparisons);
        System.out.println("Total Swaps/Shifts: " + swaps);

        System.out.println("\nTime Complexity:");
        System.out.println("Best Case: O(n) when array is already sorted");
        System.out.println("Worst Case: O(n^2) when array is in reverse order");
    }

    public static void printArray(int[] arr) {
        for (int value : arr) {
            System.out.print(value + " ");
        }
    
        System.out.println();
    }
}
SortDemo.main(null)
```
Original Array:
42 17 29 8 35 

Inserting 17:
42 42 29 8 35 
17 42 29 8 35 

Inserting 29:
17 42 42 8 35 
17 29 42 8 35 

Inserting 8:
17 29 42 42 35 
17 29 29 42 35 
17 17 29 42 35 
8 17 29 42 35 

Inserting 35:
8 17 29 42 42 
8 17 29 35 42 

Sorted Array:
8 17 29 35 42 

Total Comparisons: 8
...

Time Complexity:
Best Case: O(n) when array is already sorted
Worst Case: O(n^2) when array is in reverse order



🧮 Array to Sort: [42, 17, 29, 8, 35]

Step 0: Start  
[42, 17, 29, 8, 35]

---

Step 1: Insert 17  
[42, 17, 29, 8, 35]  
[42, 42, 29, 8, 35]   ← shift 42  
[17, 42, 29, 8, 35]   ← insert 17

---

Step 2: Insert 29  
[17, 42, 29, 8, 35]  
[17, 42, 42, 8, 35]   ← shift 42  
[17, 29, 42, 8, 35]   ← insert 29

---

Step 3: Insert 8  
[17, 29, 42, 8, 35]  
[17, 29, 42, 42, 35]  ← shift 42  
[17, 29, 29, 42, 35]  ← shift 29  
[17, 17, 29, 42, 35]  ← shift 17  
[8, 17, 29, 42, 35]   ← insert 8

---

Step 4: Insert 35  
[8, 17, 29, 42, 35]  
[8, 17, 29, 42, 42]   ← shift 42  
[8, 17, 29, 35, 42]   ← insert 35

---

✅ Final Sorted Array:  
[8, 17, 29, 35, 42]
