# Tekion  
**Year:** 2025  
**Type:** Placement  

---

## Online Assessment Overview  
The assessment was of **1.5 Hrs** consisting of:  
- **2 Coding Questions**  
- **20 MCQs**  

Difficulty level:  
- Coding: *Easy to Medium*  
- MCQs: Mostly on **Java, JavaScript, React, OS, Code and Outputs**  

---

## Question 1  

### Problem Statement  

You are given a matrix of size **n × m** (where `n ≥ m`).  
Each element in the matrix represents a **vulnerability score**.  

The task is to select **(m – 1) rows** such that the **minimum of the maximum vulnerabilities in each column** is achieved.  

**Explanation:**  
1. For any selected rows, find the **maximum vulnerability per column**.  
2. From these column-wise maximums, take the **minimum value**.  
3. Choose `(m – 1)` rows so that this resulting value is minimized.  

---

### Constraints  
- `n ≥ m`  
- Matrix elements are integers (vulnerability scores).  
- Output should be the minimized **minimum-of-maximum vulnerability** across columns.  

---

### Example  

**Input**  
n = 4, m = 3

Matrix = [

[5, 7, 9],

[1, 6, 8],

[3, 4, 2],

[9, 5, 6]

]


**Process (illustration):**  

- Select `m – 1 = 2` rows.  

➡️ Choice 1: Rows `[5, 7, 9]` and `[1, 6, 8]`  
- Column-wise maximums → `[5, 7, 9]`  
- Minimum among them = **5**  

➡️ Choice 2: Rows `[1, 6, 8]` and `[3, 4, 2]`  
- Column-wise maximums → `[3, 6, 8]`  
- Minimum among them = **3**  

Other combinations can be checked similarly.  

**Output**  
3


---

### Approach  

- Iterate over all possible selections of `(m – 1)` rows.  
- For each selection:  
  - Compute the maximum vulnerability for each column.  
  - Take the minimum of these values.  
- Keep track of the smallest such value.  
- Return it as the final answer.  

---

### Pseudocode  

```python
from itertools import combinations

def minimize_vulnerability(matrix, n, m):
    rows = range(n)
    best = float('inf')
    
    for subset in combinations(rows, m - 1):
        col_max = [max(matrix[i][j] for i in subset) for j in range(m)]
        val = min(col_max)
        best = min(best, val)
    
    return best

# Example usage
matrix = [
    [5, 7, 9],
    [1, 6, 8],
    [3, 4, 2],
    [9, 5, 6]
]
print(minimize_vulnerability(matrix, 4, 3))  # Output: 3

