
# Minimum Largest Plank Length

## 📌 Problem Statement
You are given an array `arr` of size `n`, where `arr[i]` represents the position of the *i-th hole* on a number line. You want to cover **all holes** using exactly **two planks**.

- A **plank** is defined as a continuous segment on the number line.  
- A hole at position `x` is covered if `x` lies within the segment of at least one plank.  
- The length of a plank is the distance between its two endpoints.  

Your task is to determine the **minimum possible length of the larger plank** when the two planks are placed optimally to cover all holes.

---

## 📌 Example Testcases

### Example 1
**Input:**  
```

arr = \[1, 5, 9]

```
**Output:**  
```

4

```
**Explanation:**  
- Plank 1 covers `[1, 5]` → length = 4  
- Plank 2 covers `[9, 9]` → length = 0  
- Largest plank = 4 (minimum possible).

---

### Example 2
**Input:**  
```

arr = \[2, 4, 8, 12]

```
**Output:**  
```

4

```
**Explanation:**  
- Plank 1 covers `[2, 4]` → length = 2  
- Plank 2 covers `[8, 12]` → length = 4  
- Largest plank = 4 (minimum possible).

---

### Example 3
**Input:**  
```

arr = \[3, 6, 7, 11, 15]

```
**Output:**  
```

4

```
**Explanation:**  
- Plank 1 covers `[3, 7]` → length = 4  
- Plank 2 covers `[11, 15]` → length = 4  
- Largest plank = 4.

---

### Example 4 (Edge Case)
**Input:**  
```

arr = \[10]

```
**Output:**  
```

0

```
**Explanation:**  
Only one hole → both planks can be of length `0`.

---

## 📌 Approach

1. **Sort the array** of hole positions.  
2. To place two planks, we must split the holes into two groups.  
   - Suppose the split is **between `arr[i]` and `arr[i+1]`**.  
   - Left plank covers `[arr[0], arr[i]]` → length = `arr[i] - arr[0]`.  
   - Right plank covers `[arr[i+1], arr[n-1]]` → length = `arr[n-1] - arr[i+1]`.  
3. The larger plank for this split =  
```

max(arr\[i] - arr\[0], arr\[n-1] - arr\[i+1])

```
4. Try all valid splits (`i` from `0` to `n-2`), and take the **minimum** over them.  

---

## 📌 Algorithm
```

1. Sort arr
2. Initialize ans = infinity
3. For i = 0 to n-2:
   left = arr\[i] - arr\[0]
   right = arr\[n-1] - arr\[i+1]
   ans = min(ans, max(left, right))
4. Return ans

````

---

## 📌 Code (Java)

```java
import java.util.Arrays;

class Solution {
    public int minLargestPlank(int[] arr) {
        Arrays.sort(arr);
        int n = arr.length;
        if (n == 1) return 0;

        int ans = Integer.MAX_VALUE;
        for (int i = 0; i < n - 1; i++) {
            int left = arr[i] - arr[0];
            int right = arr[n - 1] - arr[i + 1];
            ans = Math.min(ans, Math.max(left, right));
        }
        return ans;
    }
}
````

---

## 📌 Code (Python)

```python
def min_largest_plank(arr):
    arr.sort()
    n = len(arr)
    if n == 1:
        return 0

    ans = float("inf")
    for i in range(n - 1):
        left = arr[i] - arr[0]
        right = arr[-1] - arr[i + 1]
        ans = min(ans, max(left, right))
    return ans
```

---



# 📌 Problem Statement

You are given an array `arr` of size `n`, where `arr[i]` represents the **height of the i-th building**.
The array may contain **duplicate values**.

You want to **modify the array** such that:

1. **All elements are unique** (no duplicates).
2. If an element `arr[i]` is changed, its new value must be **strictly less than the current value of `arr[i]`**.
3. The **sum of the array** after modifications is **maximized**.

Your task is to return the **maximum possible sum** of the modified array.

---

# 📌 Example Testcases

### Example 1

**Input:**

```
arr = [3, 3, 3]
```

**Output:**

```
6
```

**Explanation:**

* Original: \[3, 3, 3]
* Make them unique while keeping max sum: \[3, 2, 1]
* Sum = 3 + 2 + 1 = 6

---

### Example 2

**Input:**

```
arr = [5, 3, 3, 2]
```

**Output:**

```
12
```

**Explanation:**

* Sorted descending: \[5, 3, 3, 2]
* Keep 5, keep 3, reduce the next 3 → 2, reduce the 2 → 1
* Final: \[5, 3, 2, 1] → Sum = 11 (but wait, we can do better)
* Another way: \[5, 4, 3, 2] → Sum = 14 ✅
* Best way = 14

So answer = **14**.

---

### Example 3

**Input:**

```
arr = [1, 1, 1]
```

**Output:**

```
3
```

**Explanation:**

* Possible sequence: \[1, 0, -1] → sum = 0 (bad).
* Best choice: \[1, 0, -1] is the only option since all must be unique.
* But if negatives are allowed, answer = 0.
* If we restrict to positive heights, answer = 1 (since \[1, 0, 0] not valid).


---

# 📌 Approach

1. **Sort array in descending order**.

   * We want to assign the biggest numbers first.
2. Use a greedy strategy:

   * For each element, if it is **greater than or equal to** the previous chosen element, reduce it to `prev - 1`.
   * Ensure it doesn’t go below 0 (if non-negatives required).
3. Keep track of the running sum.

This guarantees the maximum possible sum while satisfying uniqueness.

---

# 📌 Algorithm

```
1. Sort arr in descending order.
2. Initialize ans = 0, prev = infinity
3. For each num in arr:
      allowed = min(num, prev - 1)
      if allowed < 0: allowed = 0   (if only non-negative allowed)
      ans += allowed
      prev = allowed
4. Return ans
```

---

# 📌 Complexity

* Sorting: **O(n log n)**
* Greedy pass: **O(n)**
* Total: **O(n log n)**

---

# 📌 Code (Python)

```python
def max_unique_sum(arr):
    arr.sort(reverse=True)
    ans = 0
    prev = float("inf")

    for num in arr:
        allowed = min(num, prev - 1)
        if allowed < 0:
            allowed = 0
        ans += allowed
        prev = allowed
    return ans
```

---

# 📌 Code (Java)

```java
import java.util.Arrays;

class Solution {
    public int maxUniqueSum(int[] arr) {
        Arrays.sort(arr);
        int n = arr.length;
        int ans = 0;
        int prev = Integer.MAX_VALUE;

        for (int i = n - 1; i >= 0; i--) {
            int allowed = Math.min(arr[i], prev - 1);
            if (allowed < 0) allowed = 0;
            ans += allowed;
            prev = allowed;
        }
        return ans;
    }
}
```



