
# Well Fargo

**Year:** 2025
**Type:** Placement  

---

## Online Assessment Overview  
- It was an unproctored test for `1.5Hrs` consisting of 3 questions.
- It had `2DSA` questions followed by an `SQL`
- *DSA questions* were of **medium-hard** level difficulty and *sql* question was an easy one if you know `CTE(common table expression)` and `joins`.

---

## Question 1: *Maximising the energy*  
**Description:**  
- You are given an array initial Energy of sue a where aach element represents the starting energy of a particle in space. 
- The energy of particle in reduced by a value called the barier, if the energy becomes less than zero, it is set to zero.
- Your task is to find the maximum possible value of the barrier such that the total of all finalEnergy values is greater than or equal to a given threshold `th`
- `Return:` an integer `int` maximum integer value of the barrier such that sum of energies of all the particles is greater than or equal to `th`.
- The **maximum value of barrier** for which the sum of final energies of all particles is greater than or equal to `th` is **3**.
  
**Examples & Constraints:**  
- Example 1:
  - **n = 5**
  - `inititialEnergy = [4,8,7,1,2]`
  - **threshold = 9** 

```
  Test barrier values of **0 through 4**.
| barrier to test | initialEnergy - barrier | sum of final energies |
|-----------------|-------------------------|-----------------------|
| 0               | 4 8 7 1 2               | 22                    |
| 1               | 3 7 6 0 1               | 17                    |
| 2               | 2 6 5 -1 0              | 13                    |
| 3               | 1 5 4 -2 -1             | 10                    |
| 4               | 0 4 3 -3 -2             | 7                     |
```
> *These columns are calculated for each value in initialEnergy.  
> Negative values are treated as 0 in the sums.*


- Example 2:
    - `n = 4` and `inititalEnergy = [5,2,13,10]`
```
| barrier to test | initialEnergy - barrier | sum of final energies |
|-----------------|-------------------------|-----------------------|
| 6               | -1 -4 7 4               | 11                    |
| 7               | -2 -5 6 3               | 9                     |
| 8               | -3 -6 5 2               | 7                     | 
```
 - ***result = 7***

- Constraints:
    - $2<=n<=10^5$
    - $1<=inititalEnergy[i]<=10^9$
    - $1<=th<=10^4$
    - The sum of initialEnergy > th

**Tags:**  *binary search,array*

**Similar Questions:**  
- [1283. Find the Smallest Divisor Given a Threshold](https://leetcode.com/problems/find-the-smallest-divisor-given-a-threshold/description/)

[Hackerrank challenge link](https://www.hackerrank.com/contests/placement-questions-mit/challenges/maximize-energy-1)

---

## Question 2: *Modified Knapsack problem*  

### Problem Statement

**Description:**  
- The **Knapsack problem** is a well-known problem in the field of computer programming and problem-solving. To make it more interesting, the interviewer uses a modified version of the problem.
- You are given **n items**, where:
- The weight of the *i*-th item is $2^i$.
- The cost of the *i*-th item is `cost[i]`.
- You need to find the **minimum amount of money** required to purchase items such that the combined weight of the purchased items is **at least `minWeight`**.
- Complete the function `getMinimumCost`.
```python
def getMinimumCost(cost: list[int], minWeight: int) -> int:
```
- `int cost[n]`: the cost of each item
- `int minWeight`: the minimum combined weight of the items
- `Return`: `long int`: the minimum amount needed to purchase the items

---


**Examples & Constraints:**  

- Example 1
```
n = 5
cost = [2, 5, 7, 11, 25]
minWeight = 26
```

 - One of the optimal ways to purchase the items is:
     - Buy 2 units of the 0th item.
     - Buy 3 units of the 3rd item.

 - **Total cost** = $2 * 2 + 3 * 11 = 37$
 - **Total weight** = $(2 * 2^0) + (3 * 2^3) = 26$, which is at least `minWeight`.
 - Ans is `37` 


- Example 2:
  - **n = 4**
  - `cost = [10,9,8,10]`
  - **minWeight = 2** 
  - `Ans` is `8`
  - It is optimal to buy 1 units of item 2(0-based)


- Constraints:
    - $1<=n<=30$
    - $1<=COST[i]<=10^9$
    - $1<=minWeight<=10^9$


**Tags:**  *Unbounded knapsack, Dynamic Programming*

**Similar Questions:**  
- [GeeksforGeeks - Minimum Cost to Fill Given Weight in a Bag](https://www.geeksforgeeks.org/problems/minimum-cost-to-fill-given-weight-in-a-bag1956/1)

---


### Thought Process  

---

### Solution - 1

- I was able to solve the `1st` question because I have already solved the similar question which was a major key.
- They are almost the SAME question.
- The idea here is that instead of doing for all the barrier values we can do using bs ,bcoz of constraints.

```
def getMaxBarrier(initialEnergy, th):
    def sum_after_barrier(barrier):
        return sum(max(0, e - barrier) for e in initialEnergy)
    
    low, high = 0, max(initialEnergy)
    ans = 0
    
    while low <= high:
        mid = (low + high) // 2
        if sum_after_barrier(mid) >= th:
            ans = mid      
            low = mid + 1
        else:
            high = mid - 1    
    
    return ans
```
> I am clueless about the 2nd DSA question but the SQL question was dooable.

<br>

> ***ANYONE CAN CONRIBUTE! LET'S BUILD A COMMUNITY!!***
