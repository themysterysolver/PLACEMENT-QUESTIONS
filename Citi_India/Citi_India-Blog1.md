# Citi Bank India

- **Year:** 2025  
- **Type:** Placement 
- **Role:** SDE
---

## Online Assessment Overview  

-  The test duration was `1.5 hrs`, this used the same platform as `SAP Labs`.
-  Total of 3 questions were asked.
-  All three are very easy in difficulty.
-  **NOTE:** you could submit your solution only once.
-  `TIP:` write custom inputs and crosscheck your answers before submitting.
- There weren't any kind of proctoring(No camera,no microphone,no screenshare checks) 

---

## Question 1: *largest_pothole*  
**Description:**  

There is a road consisting of `N` segments (numbered from `0` to `N-1`) described by an array `R` of integers. 
The K-th segment is described by an integer `R[K]`. If the segment is smooth (there is no pothole in it). 
then **R[K] = 0** otherwise it contains a pothole of depth **R[K]**). Consecutive potholes join together and create a larger group of potholes.
The pothole indicator is the number of consecutive single potholes that have joined into a pothole group, 
multiplied by the depth of the deepest pothole among them. 
For example, the indicator for a group of three consecutive joined potholes of sizes *[1, 4, 1] is 3 \* 4=12.*
What is the largest pothole indicator on the entire road?
<br>
Write a function
``` python []
def solution(R)
```
that given an array R of N integers, returns the largest pothole indicator on the road.


**Examples & Constraints:**  
- Example 1:
Given R = [0, 2, 1, 1, 0, 4, 1] the function should return 8. The potholes in the fragment [2, 1, 1] join into one pothole group.
It is made of three segments and the deepest pothole among them is of depth 2, so its pothole indicator is equal to 3 \* 2=6.
The potholes in the fragment [4, 1] join into another pothole group.
It is made of two consecutive potholes and the deepest pothole among them is of depth 4, so its pothole indicator is equal to 2 \* 4=8

- Example 2:
  Given R = [1, 4, 1, 0, 5, 2, 3, 0, 8] the function should retum 15. The
   consecutive potholes that join into three larger pothole groups are as follows
  [1,4,1] with indicator 3*4=12 and [5,2,3] with indicator 3 * 5 = 15.
with indicator.
the largest pothole indicator is `15`

- Example 3:
  
  Given R = [9, 8, 7, 0, 0, 0, 2, 3, 6, 4] the function should return 27. The consecutive potholes that join into two larger pothole groups are as follows:
  [9.8,7] with indicator 3\*9 = 27
[2,3,6,4] with indicator 4\*6=24
The largest pothole indicator is 27.

- Example 4:

Given R = [0, 0, 0] the function should retum 0. There are no potholes on the road, so the highest pothole indicator is equal to 0.

- Constraints:
  -  Write an efficient algorithm for the following assumptions,
      - `N` is an integer within the range [1...100000]
      - Each element inside `R` is in the range [0...9]

**Tags:**  `Arrays`

## Question 2: *remove_five*  
**Description:**  

- Write a function solution that, given an integer `N`, returns the maximum possible value obtainable by deleting one `'5'` digit from the decimal representation of `N`.
   It is guaranteed that `N` will contain at least one 5 digit.


**Examples & Constraints:**  
- Example 1: Given N = 15958 the function should return 1958. 
- Example 2: Given N = - 5859 the function should return-589.
- Example 3: N = - 5000 the function should retum 0. After deleting the '5', the only digits in the number are zeroes, so its value is 0.
- Constraints: 
  Assume that
    - N is an integer within the range [-999,995..99,9995]
    - N contains at least one 5 digit in its decimal representation
    - N consists of at least two digits in its decimal representation
In your solution, focus on correctness. The performance of your solution will not be the focus of the assessment.

**Tags:**  `strings`

---

## Question 3: *max_perimeter_triangle*  
**Description:**  

- An array A consisting of N integers is given. A triplet of indices (P, Q , R ) is called a triangle if 0 <= P < O < R < N and
  - A[P]+A[Q] > A[R]
  - A[P]+A[R] > A[Q]
  - A[Q]+A[R] > A[P] 
The perimeter of such a triangle equals A[P]+A[Q]+A[R]

> **NOTE:** Note that the inequality must hold between the indices P, Q, R, but it is accepted that e.g. A[P]=A[Q]. Consider the following array A = [8,4,8,9,7]
Triplet (0,2,3) forms a triangle of perimeter 8+8+9 = 25

 - write a function,

```puthon3 [ ]
 def solution(A)
```

- that, given an array A of N integers, returns the maximum perimeter of any triangle in this array. The function should return -1 If there are no triangles possible.

**Examples & Constraints:**  
- Example 1:
  - A = [10,2,5,1,8,20]
  - Now the triplet [0,2,4] is a trangle and as penmeter equals 10 + 3 + 8 = 23
  - There is no other triangle in this array with a larger penmeter
  - Now that the inequalities must hold between the indices P,Q,R but it is accepted that eg API ALQ Consider the following array A 
- Example 2:
  - A =[5,10,18,7,8,3]
  - The function should return 25 with max perimeter 1,3 and 4 
- Example 3:
  - A = [10,20,30]
  - you should return -1
   
- Constraints:
  - Write an efficient algorithm for the following assumptions
  - N is an integer within the range [0..100,000]
  - Each element of an array is an integer within a range [1..100,000,000] 
  

**Tags:**  `sorting`, `math`,`string`

**Similar Questions (if any):**  
- [Largest perimter triangle-leetcode](https://leetcode.com/problems/largest-perimeter-triangle/description/)



---


### Thought Process  

- For the 1st q,it's just a single parse answer,we just need to count the length and also need to maintain maximum ,when we reach zero we reset them
- For the 2nd q,we just try all possible scenarios,I don't want to take any chance for +ve and -ve numbers,so I handled them seperately.
  - Sice we are asked to maximise the number I removed all possible `5` by converting given number as string. I used string splicing here.
  - For negative number I found the minum number possible
  - For positive I foudn the maximum number possible. 
- For the 3rd q,I am really glad I already solved this q in leetocde few month back. 3 loops would fail. But the logic is as follows. We sort the array,so
  array is in non-decreasing(increasing) order. This way for triplet P,Q,R  we always know Q+R>P and R+P>Q (R is the largest). Thus we need to check for only the P+Q>R condition,
  we can iterate backwards and return the 1st perimeter.
---

### Solution  

- For 1st q,
```python3 []
def solution(R):
    cMax = 0 
    maxi = 0 
    l = 0
    for num in R:
        if num != 0:
            l += 1
            cMax = max(cMax, num)
            maxi = max(maxi, cMax * l)
        else:
            l = 0
            cMax = 0
    return maxi
print(solution([4,3,5,0,0,9,2,8,0,100,1]))
```

- For 2nd q,

``` python3 []
def solution(N):
    if N <= 0:
        N*=-1
        num = str(N)
        mini = float("inf")
        for i in range(len(num)):
            if num[i] == '5':
                mini = min(mini, int(num[:i] + num[i+1:]))
        return -(mini)
    else:
        num = str(N)
        maxi = float("-inf")
        for i in range(len(num)):
            if num[i] == '5':
                maxi = max(maxi, int(num[:i] + num[i+1:]))
        return maxi
print(solution(5975))
print(solution(-5975))
```

- For 3rd q,

``` python3 []
def solution(A):
    A.sort()
    for i in range(len(A)-1,1,-1):
        if A[i-2]+A[i-1]>A[i]:
            return A[i-2]+A[i-1]+A[i]
    return -1
print(solution([8,9,8]))
print(solution([1,2,3,4,5]))
print(solution([10,20,30]))



```


> ***ANYONE CAN CONRIBUTE! LET'S BUILD A COMMUNITY!!***
