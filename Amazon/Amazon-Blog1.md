# Amazon

- **Year:** 2025  
- **Type:** Placement
- **Role:** SDE1
---

## Online Assessment Overview  

- The test comrises of 4 section
  - Coding challange(DSA) . Two questions and 70minutes.
    -  Both were of type easy-medium.
    -  All kinds of coding-laguages are allowed.
    -  Test platform was `Hackerrank`
    -  It was proctored only for tab swithching. They didn't proctor screen sharing nor asked for camera access,which made me lil sad.
    -  You have to think strongly to solve the problem and have a good problem understanding.
    -  You have 15 test cases. 3 public and 12 privates. I was lucky enough to see the inputs of the hidden testcases. Because `stdout` was enabled. Make use of this ^_^.
    -  You will have 3 options Run, Run all tetscases,submit. After checking all testcases always submit the code.
  - Working at Amazon (10mins Estimated time of completion,actually it is  untimed) - scenario based questions.
  - Your engineering work style (7mins Estimated time of completion,actually it is  untimed)- simple questions on how you approach a problem solving. Made up of MCQ.
  - Your work style(Estimated 6 minutes,untimed) - similar to above but had,more likely and most likely between given 2 statements.

---

## Question 1: *Coding question 1*  
**Description:**  

- An amazon distribution specialist needs to process `n` packages from different distribution centers,the center of `ith` package is represnted by an array `centers[i]`.
  The specialist is allowed to perform one operation at a time.Each operation is described below,
  - 1. If the queue has two or more packages,the specialist can choose 2 packages x and y from the queue if they are from different distribution centers. i.e) centers[x]
!=centers[y] and process both of them.
  - 2.If the queue has one more packages,the specialist can choose on package `x` from the queue and process it.

- Note : After processing a package it gets rmeoved form the queue,and the rest of the packages which are currently not processsed come together keeping the order same as before.
- Given *n packages* and an array `centers`,find the minimum number of operations that the specialist has to perform to process all the packages.

- **Function description** : the function *findMinimumOperations* in the editor below
    - *findMinumOperations* has the following parameters.
    - `int centers[n]` : the distribution center of each package.
- Returns: `int` the minimum number of operations that the specialist has to perform to process all of the packages.

**Examples & Constraints:**  
- Example 1:
  - Given `n=5` and centers = [3,7,5,6,6]
  
  
  |operation|x|y|centers|
  |---|---|---|---|
  |1.|1|5|[7,5,6]|
  |2.|1|3|[5]|
  |3.|1|-|[]|

  - The specialist needs to perform 3 operations to process all of the packages.

   
- Example 2:
  - Given `n=4` and centers = [1,3,1,2]
  
  
  |operation|x|y|centers|
  |---|---|---|---|
  |1.|1|4|[3,1]|
  |2.|1|3|[]|

  - Hence the specialist needs to perform 2 operations to process all of the packages.

- Constraints:
  -   $1 \leq n\leq 10^5$
  -   $1 \leq centers[i] \leq 10^9$

**Tags:**  `Array` , `Counting` , `Hash table` , `Greedy` , `Heap` 

**Similar Questions (if any):**  
- None

[Hackerrank Challenge Link](https://www.hackerrank.com/contests/placement-questions-mit/challenges/package-processing)

---

## Question 2: *Coding question 2*  
**Description:**  

- **AWS provies scalable systems. A set of `n` servers are used for horizontal scaling an application.**. The goal is to have the computation power of servers in non-decreasing order. To do so, you can increase the computation power of each server in any contiguous segment by `x`. Choose the value of `x` such that after the computational powers are in non-decreasing order, the sum of `x` values is minimum.

- **Function description** : complete the function *findMinimumSum* in the editor below.
  - *findMinimumSum*: has the following parameter(s):
  - `int power[n]:` the computational powers of n different servers.

- **Returns** ; int: the minimum possible sum of integers required to make the array non-decreasing.

**Examples & Constraints:**  
- Example 1:
  - There are n = 5 servers and their computational power = [3,4,1,6,2]
    <img width="474" height="77" alt="image" src="https://github.com/user-attachments/assets/c171e85e-b2e4-48b7-9b19-219ce0314e2c" />
  - Add 3 units to the subarray(2,4) and 4 units to the subarray(4,4). The final arrangement to the servers is [3,4,4,9,9]. The answer is 3+4 = 7.

    <img width="462" height="165" alt="image" src="https://github.com/user-attachments/assets/557c275c-ee0c-4fe6-97cc-f51f66d19a65" />
    <img width="466" height="159" alt="image" src="https://github.com/user-attachments/assets/e8e78d4e-a828-4177-8f58-14b49747ac98" />

- Example 2:
  - For n = 3 and power = [3,2,1]
  - Add 11 unit to the subarray (1,2) and 1 unit to the subarray(2,2). The final agreement of servers is [3,3,3].
  - Thus the answer is 2.

- Example 3:
  - For n = 4 and power [] = [3,5,2,3].
  - Add 3units to the subarray(2,3)..The final aggregation of servers is [3,5,5,6].
  - Hence the answer is 3.

- Constraints:
  - $1 \leq n \leq 10^5$
  - $1 \leq power[i] \leq 10^9$

**Tags:**  `array` , `prefix sum` , `greedy`  

**Similar Questions (if any):**  
- None

[Hackerrank Challenge Link](https://www.hackerrank.com/contests/placement-questions-mit/challenges/server-scaling)


---

### Thought Process  

- Initially I was scared and didn't understand both the q. Took a deep breath and read both the qns again,and I was able to solve them >_< . 
  - For question1,I did simulation which was $O(N^2)$ which failed few of the large test cases obviously. I did simulation using deque.
    - Then I thought we could minimze the cost by counting greedily using max fequencies and greedily pair them my choosing minimum of them which makes count operation faster by updating them as a whole.

  - For question2, I first viewed the constraint making it impossible to use time complexity O(N^2)$. And my though process went like this.
    - Since we need the array in ascending order we should always need to increment the element be value `x` greater than the previous element and this value should persist throught the answer thus I called it prefix `p`.
    - Thus I used this p to calculate the overall higher element than just checking difference or greatness between adjacent elements.
    - If the `p` isn't enough to satisfy the condition I just add it to the prefix and continue the above process. 

---

### Solution  

- Question1, simulation and brute force.

```python 3[]
from collections import Counter,deque
def min_operations(centers):
    q = deque(centers)
    count = 0
    while q:
        if len(q) == 1:
            q.popleft()
        else:
            flag = False
            for i in range(1,len(q)):
                if q[i] != q[0]:
                    q.remove(q[i]) 
                    q.popleft()
                    flag = True
                    break

            if not flag:
                q.popleft()
        count+=1
    return count

n = 5
centers = [3, 7, 5, 6, 6]
print(min_operations(centers))
```

- Question1, optimized using counting.
```python 3[]
from collections import Counter
import heapq
def findMinimumOperations(centers):
#Write your code here
    c = Counter (centers)
    heap = []
    for key,val in c.items():
        heapq.heappush (heap, (-val, key))
    count = 0
    while heap:
        if len(heap)>=2:
            v1,k1 = heapq.heappop(heap)
            v2,k2 = heapq.heappop(heap)
            v1*=-1
            v2*=-1
            mini = min(v1, v2)
            count+=mini
            v1-=mini
            v2-=mini
            if v1>0:
                heapq.heappush (heap, (-v1, k1))
            if v2>0:
                heapq.heapush (heap, (-v2, k2))
        else:
            v1,_ = heapq.heappop (heap)
            count+=v1*-1
    return count
print(findMinimumOperations([3,7,5,6,6]))
I
```

- Question2, using prefix logic.
```python3 []
def findMinimumSum(nums):
    p = 0 #prevIncrements
    print(nums)
    for i in range(1,len(nums)):
        if nums[i]+p>nums[i-1]+p:
            continue
        else:
            diff = nums[i-1]-nums[i] 
            p+=diff
    return p
print(findMinimumSum([3,2,1]))
```

> ***ANYONE CAN CONRIBUTE! LET'S BUILD A COMMUNITY!!***-/*+
> 
