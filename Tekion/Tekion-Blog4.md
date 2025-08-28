# Tekion

**Year:** 2025
**Type:** Placement 

---

## Online Assessment Overview  
The assessment was of **1.5 Hrs** consisting of:  
- **2 Coding Questions**  
- **20 MCQs**  


---

## Question 1: *Visible Towers*  
**Description:**  
You are given **n towers** in the form of an array, where `tower[i]` represents the **height** of the *i-th* tower.  

For each tower at index `i`, you need to determine the **number of towers it can see** on both its **left** and **right** sides.  

- A tower `i` can see another tower `j` if:  
  - `j` is to the left or right of `i`, and  
  - there is no taller tower **in between** `i` and `j` that blocks the view.  

Return an array `result` of size `n` where `result[i]` is the number of towers that the `i-th` tower can see.  

**Examples & Constraints:**  
- Example 1:
   - Input: towers = [3, 6, 2, 4, 5]
   - Output: [1, 4, 3, 3, 3] 
   **Explanation:**  
    - Tower 0 (height 3) → can see only Tower 1 (height 6). → count = 1  
    - Tower 1 (height 6) → can see Towers [0, 2, 3, 4]. → count = 4  
    - Tower 2 (height 2) → can see Towers [1, 3, 4]. → count = 3  
    - Tower 3 (height 4) → can see Towers [2, 4]. → count = 3  
    - Tower 4 (height 5) → can see Towers [1, 2, 3]. → count = 3  
    So the final result is `[1, 4, 3, 3, 3]`.  

- Example 2:
    - Input: towers = [1, 2, 3]
    - Output: [1, 2, 2]
    **Explanation:**  
    - Tower 0 (height 1) → can see Tower 1. → count = 1  
    - Tower 1 (height 2) → can see Towers [0, 2]. → count = 2  
    - Tower 2 (height 3) → can see Towers [0, 1]. → count = 2  

- Constraints:
- `1 <= n <= 10^5`  
- `1 <= tower[i] <= 10^9`  

**Tags:**  
`Arrays`,`Two Pointers` 

**Similar Questions (if any):**  
- [LeetCode 1944 – Number of Visible People in A Queue](https://leetcode.com/problems/number-of-visible-people-in-a-queue/description/)  

---

### Thought Process  
I thought of a brute force approach. For each index i , I went to the left as well right for each index. Keep track of the maximum height reached once a tower with height less than the maximum we stop the count.This was repeated for both left and right.

It passed 7/15 testcases there were tle and also some wrong answers.

---

### Solution  
```java
import java.util.*;

public class VisibleTowers {

    public static int[] visibleTowers(int[] arr) {
        int n = arr.length;
        int[] res = new int[n];

        for (int i = 0; i < n; i++) {
            // check left
            int max_h = 0;
            for (int j = i - 1; j >= 0; j--) {
                if (arr[j] > max_h) {
                    res[i]++;
                    max_h = arr[j];
                }
                if (arr[j] >= arr[i]) {
                    break; // block further view
                }
            }

            // check right
            max_h = 0;
            for (int j = i + 1; j < n; j++) {
                if (arr[j] > max_h) {
                    res[i]++;
                    max_h = arr[j];
                }
                if (arr[j] >= arr[i]) {
                    break; // block further view
                }
            }
        }

        return res;
    }

    public static void main(String[] args) {
        int[] arr = {3, 6, 2, 4, 5};
        int[] result = visibleTowers(arr);
        System.out.println(Arrays.toString(result));  // [1, 4, 3, 3, 3]
    }
}
``` 


// Your solution here
> ***ANYONE CAN CONRIBUTE! LET'S BUILD A COMMUNITY!!***