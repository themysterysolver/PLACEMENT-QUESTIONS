# Athenahealthcare

**Year:** 2025  
**Type:** Placement 
**Role:** SDE
---

## Online Assessment Overview  

- Tets duration was `70mins` in *hackerrank*
- 10 MCQs and 2 Coding questions.
- MCQ question were from basic cs,loops,prefix,infix,postfix conversions,differetn sorting algorithms,questions on tail recursion were aksed for me.
- There were different sets,which varied in complexity from easy-medium-hard. some set of questions were staright,other question were hard .

---

## Question 1: *K-Smallest substring*  
**Description:**  

- Given a binary string `s` ,and an integer number `k` find a substring such that it follows the below rules!
  - There are exactly `k` ***one's*** in the substring
  - The substring obtained is of smallest length
  - The susbtring is the lexicographically smalllest one.
    
**Examples & Constraints:**  
- Example 1:
  - `s = 0101101` , `k = 3`
  - possible subarrays are `01011`,`1101`,`1011`.
  - Ans => `1011` which follows both the rules!  
- Example 2:
  - `s = 10101` , `k = 2`
  -  possible optimal subarrays are `101`,`0101`
  -  Ans => `101`
- Constraints:
  - $1 \leq s.length \leq 10^3$
  - $1 \leq s[i] \leq 10^3$ 

**Tags:**  `Sliding window` , `string`

> `NOTE` : The second question I got is `Palindromic algorithm` ,I am not sure about the question. If any contributors have the question,kindly contribute!

---

### Thought Process  

- For the `1st` question I could have brute forced all subarrays instead of doing sliding window. But I was strong with my though ptocess and proceeded further.
  - What I did is I moved my *window* with `k` as the limit. I stored them in `ans`.
  -  Then I removed the *LHS* `0` from my `ans` because we want minimal(smallest substring)` then I chosse the smallest length,then lexicographically smallest among them.

---

### Solution  


```python3 []
from collections import defaultdict
def kthSmallestSubstring(s,k):
    count,start = 0,0
    res = []
    for i in range(len(s)):
        if s[i] == '0':
            continue
        else:
            count+=1
            if count == k:
                while count == k:
                    res.append(s[start:i+1])
                    if s[start] == '1':
                        count-=1
                    start+=1
    ans = []
    for r in res:
        ans.append(r[r.index('1'):])
    hash = defaultdict(list)
    for a in ans:
        hash[len(a)].append(a)
    small = min(hash)
    return min(hash[small])
print(kthSmallestSubstring("0101101",3))
print(kthSmallestSubstring("10101",2))
```


> ***ANYONE CAN CONRIBUTE! LET'S BUILD A COMMUNITY!!***
