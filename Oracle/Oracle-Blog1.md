# Oracle 

**Year:** 2025
**Type:** Placement  
**Role:** OFSS FTE
---

## Online Assessment Overview  

-  It consist of `32q`, `2DSA` and `30MCQ`.
-  Coding question were of easy-mid medium difficulty.
-  `15Q` of *aptitude* which was from cloud,networks,ML,reading comprehension,OS.
-  `15Q` *technical* was wasked from DSA,design systems,web dev,java,threads,deadlocks.
-  The 30q were really hard. So focus on reading the below topics.

---

## Question 1: *Valid keys*  
**Description:**  
- A cyber security firm has discovered a new type of encryption being used by a group of hackers. The encryption key will be a *valid key*, which is a number that has *exactly 3 factors* (or divisors). For example, 4 is a valid key because it has exactly 3 factors: 1, 2. and 4. But 6 is not a valid key because it has 4 factors: 1. 2. 3. and 6.
- Given an array keys of `length n`, **find the number of valid keys in the range** `[1, keys[i]]`, both inclusive, for each $0 \leq i \le n$
>Note:
a is called a divisor of b if there is an integer c such that $a*c=b$ .
Only positive integers are taken into account for counting divisors.

- Function Description: Complete the function getValidKey in the editor below.
- getValidkey has the following parameter: `long_int numbers[n]` : *an array of integers*.
- Returns(int): an array of integers containing the answer for each query.

**Examples & Constraints:**  
- Example 1:
  - Given, n = 2 , keys = [5,11]
    - `key[0]=5` => `4` has only 3 divisors `1,2,4` => `count=1`
    - `key[1]=11` => `4` and `9` => `count=2`
    - Thus the ans is [1,2]
- Example 2:
  - Given, n = 2 , keys = [10,15]
  - For both `10` and `15` => the valid numbers are `4` and `9`. Hnece the count is `2` for both.
  - Return `[2,2]`
- Example 3:
  - Given, n = 1 , keys = [100]
  - Ans is `[4]`
- Constraints:
  - $1 \leq n \leq 10^5$
  - $1 \leq keys[i] \leq 2.5*10^(13)$  

**Tags:**  `prefix`, `array` , `dp` , `counting` , `math`

## Question 2: *Bullish Trend Detection*  
**Description:**  
- You are bullding a backend server for a stock analytics platform, You have an array
named `stockPrices` where `stockPrices[i]` denotes the price of the stock in the `ith` month. A bulish trend of size `k` is an interval of size k months such that the stock prices increase strictly throughout those months.
- Implement a function that calculates the number of bullish trends of size k.
- The function `calculateBullish` Trends takes the following inputs:
  - int stockPrices[n]: the stock prices for `n` months
  - int k: the analysis parameter
- The function should return an integer, the number of bullish trends of size k.
> Note: If the interval length is 1, each subarray of length 1 is highly profitable.




**Examples & Constraints:**  
- Example 1:
  - stockPrices = [5,3,5,7,8] k = 3
  - The interval `[3,5,7]` and `[5,7,8]` are striclty increasing
  - ans is 2
  - These are the intervals of k months in which the stock prices are strictly increasing:
    
- Example 2:
  -   stockPrices = [1,2,3,3,4,5] k = 3
  -   The interval `[1,2,3]` and `[3,4,5]` are striclty increasing
  - ans is 2
- Constraints:
  -  $1 \leq k \leq n \leq 2*10^5$
  -  $1 \leq stockprices[i] \leq 10^9$

**Tags:**  `hash table`

---

### Thought Process  
- For the *1stq* I found divisors for each number.I had the idea to store the previously computed count in `pre` to quick access.
- For the *2ndq* Discontinuity is handled by hash.By default each day has one,this is the base case.


Approach 2 for question 1:

- Divisors always come in pairs. If $a * b = n$, both $a$ and $b$ are divisors of $n$, unless $a = b$, which means $n$ is a perfect square.
- Any $n$ has atleast two divisors - 1 and itself. So, for $n$ to have exactly 3 divisors, it must be a square number and that too square of a prime.
- So, it is enough to count the number of squares of primes less than $key[i]$.
- Or equivalently, it is enough to count the number of primes less than $\sqrt{key[i]}$.
---

### Solution 1

```
def getValidKeyCount(keys):
  def isvalid(num):
    divisors = set()
    for i in range(1,int(num**0.5)+1):
      if num%i== 0:
        divisors.add(i)
        divisors.add(num//i)
    return 3 == len(divisors)
  pre = [0]*(max(keys)+1)
  count = 0
  for i in range(1, max(keys)+1):
    if isvalid(i):
      count+=1
    pre[i] = count
  #print(pre)
  # for i in range(len(pre)):
  # print(i,pre[i])
  #pass
  return [pre[i] for i in keys]
print(getValidKeyCount([5,11]))
```

### Solution 2

```
def calculateBullishTrends(stockPrices, k):
  hash = {i:1 for i in range(len(stockPrices))}
  count = 0
  for i in range(1,len(stockPrices)):
    if stockPrices[i]>stockPrices[i-1]:
      hash[i]+=hash[i-1]
  for key, val in hash.items():
    if val>=k:
      count+=1
  return count
print(calculateBullishTrends([1,2,3,3,4,5],3))
```


> ***ANYONE CAN CONRIBUTE! LET'S BUILD A COMMUNITY!!***
