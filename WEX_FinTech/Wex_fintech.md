# WEX Fintech

- **Year:** 2025
- **Type:** Placement
- **Role:** SDE

---

## Online Assessment Overview  

- The test consist of `2sections` =>   `MCQ` and `Coding`.
- There were 15MCQ  5 questions were from basic programming(variables and loops),basic q from oops,networks and os.
- The `2dsa` q were of type easy to medium.
- The test happened in **Hire pro**.

---

## Question 1: *Bishop after K Moves*  
**Description:**  
- You are given a board of ize `m*n` starting from (1,1).
- You are given a bishop position `(x,y)` and integer `k`,the k denotes the number of moves the bishop can move.
- In a single move a bishop can go in any diagonal direction.
- return the maximum number of squares can be covered from k moves.
- $bishop(int m,int n,int k,int x,int y)$

**Examples & Constraints:**  
- Example 1:
  -  Given a `m = 5` , `n = 6` , `k = 2` , `x  = 2` , `y = 2`
  -  The answer is `15`

  <img width="318" height="272" alt="image" src="https://github.com/user-attachments/assets/7107eccf-ea61-46d4-bd74-738994060538" />

  
- Example 2:
 - Given a `m = 3` , `n = 7` , `k = 2` , `x  = 1` , `y = 1`
 - The answer is `7`
  <img width="380" height="198" alt="image" src="https://github.com/user-attachments/assets/c685b41a-2d92-4265-b375-ec60755d184f" />

   
- Constraints:
  - $1 \le m,n  \le 10^3$
  - $1 \le k<m,n  \le 10^3$
  - $1 \leq x  \leq m$
  - $1 \leq y  \leq n$
    
**Tags:**  `matrix` , `sets`, `q` , `simulation` ,   `bfs`

**Similar Questions:**  
- [2596. Check Knight Tour Configuration](https://leetcode.com/problems/check-knight-tour-configuration/description/)

## Question 2: *Prime which ends with K*  
**Description:**  

 - you are given `N` and `K`.
 - You should find the first `N` prime numbers that ends with the digit `K`.
 - Add 2,5 to this N numbers and print the resultant array in ascending order.

**Examples & Constraints:**  
- Example 1:
  - Given N = 5, K = 3
  - 3, 13, 23, 43, 53 ends with 3
  - After the final operation the ans would be `2 3 5 13 23 43 53`
- Example 2:
  - Given N = 15, K = 7
  - 7, 17, 37, 47, 67, 97, 107, 127, 137, 157, 167, 197, 227, 257, 277
  -  After the final operation the ans would be `2 5 7 17 37 47 67 97 107 127 137 157 167 197 227 257 277`
- Example 3:
  - Given N = 10, K = 1
  - 11 31 41 61 71 101 131 151 181 191
  - After the final operation the ans would be `2 5 11 31 41 61 71 101 131 151 181 191`
- Constraints:
  -  $1 \le N \le 1001$
  -  $1 K takes the value ***1,3,7***

**Tags:**  `String` , `math` , `sorting`
 

**Similar Questions (if any):**  
- [204. Count Primes](https://leetcode.com/problems/count-primes/description/)

> NOTE: For both the questions,make sure you just use print as final result.Don't need to return anything. If anything in stdop other than answer,it would be considered wrong.

---

### Thought Process  
- For the `1stQ` I just simulated the problem. But lots of hidden testcases failed. I am giving my solution below,if u could debug,and find new approach let me know.
  -  I found my mistake!
- For the `2ndQ` since the constraint is small I generated all the primes and checked if they end with `k` ,and I did the operation. Here also I failed,if you could fix it,pls do!
  - Fixed my code ,you could check the wrong code in the git log named `ab1b2b6c0fa1e9550fc76869f93911d1211a2d12`, try `git show` or search it in the commit history.

---

### Solution - 1  

```
from collections import deque

def bishop(m,n,k,x,y):
    q = deque([(x,y)])
    visited = set()
    visited.add((x,y)) #missed this in OA!
    values = 1#already given!
    
    for _ in range(k):
        l = len(q)
        for _ in range(l):
            x,y = q.popleft()
            for dx,dy in [(1,1),(-1,-1),(-1,1),(1,-1)]:
                nx,ny = x,y
                for _ in range(m):
                    nx,ny = nx+dx,ny+dy
                    if nx<1 or ny<1 or nx>m or ny>n or (nx,ny) in visited:
                        continue
                    else:
                        values+=1
                        visited.add((nx,ny))
                        q.append((nx,ny))
            #print(q)
    def dis(key):
        matrix = [[0]*(n+1) for _ in range(m+1)]
        for x,y in key:
            matrix[x][y] = 1
        for row in matrix:
            print(row)
        print('---------')
    #print(sorted(list(visited)))
    #dis(visited)
    print(values)
    
bishop(5,6,2,2,2)
bishop(3,7,2,1,1)
    
```

### Solution - 2

```
def primeEndsWithK(N,K):
    def isPrime(num):
        if num < 2:
            return False
        for i in range(2,int(num**0.5)+1):
            if num%i == 0:
                return False
        return True
    
    count = 0
    i = 2
    ans = []
    while count!=N:
        if isPrime(i) and str(i)[-1] == str(K):
            count+=1
            ans.append(i)
        i+=1
    ans.extend([2,5])
    ans.sort()
    for p in ans:
        print(p,end=' ')
    print()
        
primeEndsWithK(10,1)
primeEndsWithK(5,3)
```


> ***ANYONE CAN CONRIBUTE! LET'S BUILD A COMMUNITY!!***
