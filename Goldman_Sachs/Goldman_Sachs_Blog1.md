# Goldman Sachs

**Year:** 2025

**Type:** Internship

---

## Online Assessment Overview  

- It was an unproctored test for `2 hours` consisting of multiple components.
- It had `3 DSA` questions, `15 MCQ + Aptitude` questions, and `1 behavioral` question
- MCQ's were focused on `C, C++, Java, OOP concepts, SQL`
- The coding round was of **medium** difficulty
- DSA questions covered topics like bit manipulation, greedy algorithms, and sorting

---

## Question 1: *Minimizing Product-Sum Difference*  
**Description:**  
- You are given N substances. Each has two values:
  - `G[i]` → Growth boost
  - `T[i]` → Toxicity
- Choose at least one substance such that the difference between `|Product of all chosen G[i] – Sum of all chosen T[i]|` is minimized.

**Examples & Constraints:**  

- Example 1: 
```
Sample Input:
3
3 8
5 8
4 4

Sample Output:
0

Explanation:
Subset {3, 5, 4} → Product = 3×5×4 = 60, Sum = 8+8+4 = 20 → |60–20| = 40
Subset {3, 5} → Product = 15, Sum = 16 → |15–16| = 1
Subset {5, 4} → Product = 20, Sum = 12 → |20–12| = 8
Subset {3, 4} → Product = 12, Sum = 12 → |12–12| = 0 ✅
Hence output = 0
```

**Tags:** `bit manipulation`, `brute force`, `subset enumeration`

---

## Question 2: *Employee Mentorship System*

**Description:**

- Each employee has two attributes:
  - `A` = Skill
  - `B` = Exposure
- There are two operations:
  - `E A B` → Add employee with attributes (A, B)
  - `Q i` → Employee i requests a mentor
- Mentorship rules:
  - Mentor must have Skill ≥ A[i] and Exposure ≥ B[i]
  - Among all valid mentors:
    - Prefer the one with smallest exposure difference
    - If tie → choose the one with smallest skill difference
  - Once chosen, a mentor cannot be reused

**Examples & Constraints:**

- Example 1:
```
Sample Input:
6
E 8 8
E 2 4
E 5 6
Q 2
E 6 2
Q 4

Sample Output:
3
1

Explanation:
There are 6 operations.
E 8 8 → Employee 1 joins with skill = 8, exposure = 8.
E 2 4 → Employee 2 joins with skill = 2, exposure = 4.
E 5 6 → Employee 3 joins with skill = 5, exposure = 6.
Q 2 → Employee 2 is seeking mentorship.
We now look for employees who have skill ≥ 2 and exposure ≥ 4.

Valid mentors: Employee 1 (8,8), Employee 3 (5,6)
Exposure differences: Employee 1 = 4, Employee 3 = 2 ✅ smaller
So mentor = Employee 3

E 6 2 → Employee 4 joins with skill = 6, exposure = 2.
Q 4 → Employee 4 seeks mentorship (skill ≥ 6, exposure ≥ 2)
Only Employee 1 (8,8) is available as mentor.
So mentor = Employee 1
```

**Tags:** `greedy algorithm`, `simulation`, `priority matching`

---

## Question 3: *Custom Sorting by Factor Count*

**Description:**

- You are given an array. Sort it based on:
  1. Number of factors (descending order)
  2. If tie → by value (descending order)

**Examples & Constraints:**

- Example 1:
```
arr = [10, 6, 8]

Factors:
10 → {1,2,5,10}   → count = 4
6  → {1,2,3,6}    → count = 4
8  → {1,2,4,8}    → count = 4

All same → sort by value

Output: 10 8 6
```

**Tags:** `sorting`, `number theory`, `factor counting`

---

## Thought Process  
### Solution  

- For `question 1` I used bitmasking to generate all possible subsets and calculated the minimum difference. The key insight is that we need to check all 2^N - 1 non-empty subsets.

```cpp
#include <iostream>
#include <vector>
#include <cmath>
#include <climits>
using namespace std;

int findMinDifference(int N, vector<int> &G, vector<int> &T) {
    int minDiff = INT_MAX;
    
    // Loop through all subsets using bitmask
    for (int mask = 1; mask < (1 << N); ++mask) {
        int productG = 1;
        int sumT = 0;
        
        for (int i = 0; i < N; ++i) {
            if (mask & (1 << i)) {
                productG *= G[i];
                sumT += T[i];
            }
        }
        
        int diff = abs(productG - sumT);
        minDiff = min(minDiff, diff);
    }
    
    return minDiff;
}
```

- For `question 2` I implemented a simulation approach where I store all employees and for each query, find the best mentor based on the given criteria.

```cpp
#include <iostream>
#include <vector>
#include <string>
#include <climits>
using namespace std;

struct Employee {
    int A, B; // Skill and Exposure
};

void printID(int N, string operations[][3]) {
    vector<Employee> employees;
    vector<bool> mentorUsed(N + 1, false);
    
    for (int i = 0; i < N; ++i) {
        string type = operations[i][0];
        
        if (type == "E") {
            int A = stoi(operations[i][1]);
            int B = stoi(operations[i][2]);
            employees.push_back({A, B});
        }
        else if (type == "Q") {
            int idx = stoi(operations[i][1]) - 1;
            
            int reqA = employees[idx].A;
            int reqB = employees[idx].B;
            
            int minBDiff = INT_MAX;
            int minADiff = INT_MAX;
            int bestId = -1;
            
            for (int j = 0; j < employees.size(); ++j) {
                if (j == idx || mentorUsed[j]) continue;
                
                int mentorA = employees[j].A;
                int mentorB = employees[j].B;
                
                if (mentorA >= reqA && mentorB >= reqB) {
                    int bDiff = mentorB - reqB;
                    int aDiff = mentorA - reqA;
                    
                    if (bDiff < minBDiff || (bDiff == minBDiff && aDiff < minADiff)) {
                        minBDiff = bDiff;
                        minADiff = aDiff;
                        bestId = j;
                    }
                }
            }
            
            if (bestId == -1)
                cout << "NE" << endl;
            else {
                mentorUsed[bestId] = true;
                cout << bestId + 1 << endl;
            }
        }
    }
}
```

- For `question 3` I counted factors efficiently using the √n method and then used custom sorting with a comparator.

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

// Function to count number of factors of a number
int countFactors(int num) {
    int count = 0;
    for (int i = 1; i * i <= num; ++i) {
        if (num % i == 0) {
            count++;
            if (i != num / i) 
                count++;
        }
    }
    return count;
}

void factorCount(int N, int arr[]) {
    vector<pair<int, int>> v; // {factorCount, number}
    
    for (int i = 0; i < N; ++i) {
        int factors = countFactors(arr[i]);
        v.push_back({factors, arr[i]});
    }
    
    // Sort in descending factor count, then by descending number
    sort(v.begin(), v.end(), [](pair<int, int> a, pair<int, int> b) {
        if (a.first != b.first) 
            return a.first > b.first;
        return a.second > b.second;
    });
    
    // Print only the numbers in sorted order
    for (auto p : v) {
        cout << p.second << " ";
    }
    cout << endl;
}
```

> ***ANYONE CAN CONTRIBUTE! LET'S BUILD A COMMUNITY!!***
