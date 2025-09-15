# Athenahealthcare

**Year:** 2025  
**Type:** Placement  
**Role:** SDE  
---

## Online Assessment Overview  

- Test duration was `70 mins` in *HackerRank*  
- 10 MCQs and 2 Coding questions.  
- MCQ questions were from basic CS, loops, prefix/infix/postfix conversions, different sorting algorithms, and questions on tail recursion.  
- There were different sets which varied in complexity from easy–medium–hard. Some sets of questions were straightforward, others were tricky.  

---

## Question 1: **Minimizing Array Cost by Insertion**  

**Description:**  
You are given an array of integers. The *cost* of the array is defined as:  

\[
\text{cost} = \sum_{i=1}^{n-1} (arr[i] - arr[i-1])^2
\]

You are allowed to insert **one new element** at any position in the array. The goal is to minimize the overall cost after insertion.  

**Examples & Constraints:**  
- Example:  
  - Input: `[1, 10]`  
  - Original cost: \((10 - 1)^2 = 81\)  
  - If you insert `5`: cost = \((5 - 1)^2 + (10 - 5)^2 = 16 + 25 = 41\)  
  - Minimum cost = 41  

- Constraint:  
  - Array length ≤ 1000  
  - Elements are integers  

**Tags:**  `Greedy`, `Math`, `Array`  

---

### Thought Process  
- First, calculate the original cost of the array.  
- The main observation is that the cost is high if there exists a pair of elements with a large difference.  
- To reduce the cost, you should insert a number between the pair contributing the **maximum squared difference**.  
- Intuitively, inserting the average of the two numbers in such a pair minimizes the squared difference.  
  - Example: For pair `(a, b)`, the cost is \((b - a)^2\).  
  - If we insert `m = (a+b)/2`, then new cost = \((m-a)^2 + (b-m)^2 = 2*((b-a)/2)^2 = (b-a)^2 / 2\).  
  - Thus, the cost for that pair is halved.  

---

### Solution (Java Code)  

```java
import java.util.*;

public class MinimizeArrayCost {

    // Function to compute cost of an array
    private static int computeCost(int[] arr) {
        int cost = 0;
        for (int i = 1; i < arr.length; i++) {
            int diff = arr[i] - arr[i - 1];
            cost += diff * diff;
        }
        return cost;
    }

    // Function to insert an element to minimize cost
    private static int[] minimizeAndInsert(int[] arr) {
        int n = arr.length;
        int bestReduction = 0;
        int insertPos = -1;
        int insertValue = -1;

        for (int i = 1; i < n; i++) {
            int a = arr[i - 1];
            int b = arr[i];
            int pairCost = (b - a) * (b - a);

            // Insert average between a and b
            int m = (a + b) / 2;
            int newPairCost = (m - a) * (m - a) + (b - m) * (b - m);

            int reduction = pairCost - newPairCost;
            if (reduction > bestReduction) {
                bestReduction = reduction;
                insertPos = i;
                insertValue = m;
            }
        }

        // Build new array with inserted element
        int[] newArr = new int[n + 1];
        for (int i = 0, j = 0; i < newArr.length; i++) {
            if (i == insertPos) {
                newArr[i] = insertValue;
            } else {
                newArr[i] = arr[j++];
            }
        }
        return newArr;
    }

    public static void main(String[] args) {
        int[] arr = {1, 10};
        System.out.println("Original Array: " + Arrays.toString(arr));
        System.out.println("Original Cost: " + computeCost(arr));

        int[] newArr = minimizeAndInsert(arr);
        System.out.println("New Array: " + Arrays.toString(newArr));
        System.out.println("Minimized Cost: " + computeCost(newArr));
    }



> ***ANYONE CAN CONRIBUTE! LET'S BUILD A COMMUNITY!!***
