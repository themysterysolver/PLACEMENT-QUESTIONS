
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
- [1300. Sum of Mutated Array Closest to Target](https://leetcode.com/problems/sum-of-mutated-array-closest-to-target/)
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


**Tags:**  *Unbounded knapsack, Greedy*

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
### Solution - 2

The key idea here is the fact that weight of item[i] = $2^i$. This means every heavier item weighs an exact multiple of every lighter item.
- Define gain ratio as $\frac{weight[i]}{cost[i]}$.
- Let's take two items item[i] and item[j], i < j and their costs as A and B respectively.
- ratio[i] = $\frac{2^i}{A}$, ratio[j] = $\frac{2^j}{B}$.
- If we compare the ratios, $x = \frac{ratio[i]}{ratio[j]} = \frac{2^i * B}{A * 2^j}$ = $2^{i - j} * \frac{B}{A}$.
- Suppose we take 1 unit of item[j]. This will cost B. To fill the same weight, we can take $2^{j - i}$ units of item[i]. This will cost $2^{j - i} * A$.
- If we compare the cost of B with cost of A to fill the same weight, we get $\frac{B}{2^{j - i} * A} = 2^{i - j} * \frac{B}{A} = x$.
- So, if $x < 1$, item[j] costs less and has higer ratio, it is always better to take item[j] to fill $2^j$ units of weight and if $x > 1$, it is always better to take $2^{i - j}$ units of item[i] to fill the same weight.

Hence, we can sort the items in descending order of gain ratio.

- However, this runs into a small issue where the remaining weight to be filled is less than the weights of the items with biggest gain and we cannot pick partial items. 
- Take for example minWeight = 6. costs = [15, 3, 5, 9], weights = [1, 2, 4, 8].
ratios = $[1/15, 2/3, 4/5, 8/9]$ = [0.067, 0.67, 0.8, 0.89].
- The biggest ratio is for item 3. But we can only choose in whole numbers. This gives us a cost of 9, whereas the optimal way is to pick 1 unit of item 1 and 1 unit of item 2 to give a cost of 8.
- To achieve this, we iterate through the items sorted by gain and check how many counts of each is needed to fill the remaining weight. If we get a count >= 1, we stop. Because we have to pick atleast 1 unit of this item, anything else with lesser gain will inevitably cost more, so stop here.
- Then calculate the costs of these items and pick the one with the lowest cost. Subtract this weight from minWeight and repeat the process till we get non-positive minWeight.


```
def knapsack(costs, min_weight):
    #Weight/Cost and keep track of index
    ratio = [(2 ** i / c, i) for i, c in enumerate(costs)] 
    ratio.sort(reverse=True)
    cost = 0
    while min_weight > 0:
        choices = []
        for r, i in ratio:
            number = min_weight // (2 ** i) #Floor division because whole numbers
            found = False
            if number == 0:
                number = 1 #Partial pick not possible, so turn 0 into 1
            else:
                found = True
            choices.append((number * costs[i], number * (2 ** i), i))
            if found:
                break
        pick = min(choices)
        min_weight -= pick[1]
        cost += pick[0]

    return cost
```

<br>

> ***ANYONE CAN CONRIBUTE! LET'S BUILD A COMMUNITY!!***
