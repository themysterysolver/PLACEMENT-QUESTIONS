# Verizon

**Year:** 2025
**Type:** FTE

---

## Online Assessment Overview

- The test consisted multiple parts ranging from MCQs to Apptitudes
- 2 Coding questions 40 mins (low weightage), 30 MCQs on modern GenAi in 30 mins
- English essay writing type, 240+ words in 25 mins
- Coding round was **easy** difficulty (basic DSA questions)

---

## Question 1: *Number of Steps*
**Description:**
- Alice has to reach the step N. At each step she can take 1 or M steps. Find the minimum number of steps she needs to reach exactly the Nth step.
    - Given `N` and `M`

**Examples:**

- Example 1:
```
Sample Input:
5 3

Sample Output:
3

Explanation:
Alice takes 3 steps first --> reaching 3
Then she takes 1 step --> reaching 4 (she can't take 3 steps as it exceeds 5)
She once again takes 1 step --> reaching the target 5
3 1 1 ==> 3 steps taken
```

**Tags:** `Greedy`, `Math`

---

# Question 2: *Non Decreasing array by combining*

**Description:**

- You are given an array of positive integers. You are allowed a single operation any number of times
    - The operation is as follows: You can pick a subarray and replace it with it's sum.
    - You do this untill your array is in non-decreasing order.
- Return the length of the longest non-decreasing array possible by repeating that operation

**Examples:**

- Example 1:
```
arr = [1, 4, 2, 6, 9]

Output: 4

Explanation:
choose the subarray [2, 6] and replace it with its sum [8]
New array = [1, 4, 8, 9] --> it's in non-decreasing order
Therefore return length of this array which is 4

Alternatively - Pick [4, 2]
New Array = [1, 6, 6, 9] --> non-decreasing (length is still 4)
```

- Example 2:
```
arr = [5, 2, 5, 7]

Output: 3
[5, 2, 5, 7] ==> [5, 7, 7] (non-decreasing)
(note: picking any other subarray result in a smaller final result array)
```

- Example 3:
```
arr = [1, 2, 3, 4]

Output: 4
Already in a non-decreasing way
```

---

## Thought Process
### Solution

- For `question 1` Just looking at the question, we can immediately see that picking M whenever possible 
leads to optimal solution (greedy). We can choose N//M times M, then the remaining step becomes r where,
r = N - M*q (we have chosen M, q times, without exceeding N). The solution becomes q+r.

```python 3

def findNumberofSteps(N, M) -> int:
    q = N//M
    r = N%M

    return q+r

```

- For `question 2` I simply implemented a simulation approach. When finding a element less than previous,
iterate after that element taking sum till you get a sum greater than that, replacing the subarray with that number.

```python 3

def lenNonDecreasingArray(arr: list) -> int:
    i = 1
    while i < len(arr):
        if arr[i] < arr[i-1]:
            j = i
            s = 0
            while j < len(arr) and s < arr[i-1]:
                s += arr[j]
                j += 1
            
            arr = arr[:i] + [s] + arr[j:]
        else:
            i += 1
    return len(arr)

```

```
A better approach for question 2 would be greedy approach.
To maximize the number of blocks you want each block to be as short as possible while still 
respecting the rule that each new block-sum ≥ previous block-sum. 
So scan left→right and for each block start at the current index and enlarge it just until its 
sum is ≥ the previous block-sum. 
That produces the minimal-length block that’s valid, so you leave as many elements as possible 
for future blocks.

Reasoning on why this works and the code is left as an exercise for the readers.
```
