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

## Question 1:   
**Description:**  

- You are given an array of size `n` (where `n` is always even).
- Your task is to pair up all elements of the array into exactly `n/2` pairs such that:
  - 1. **All pairs have the same sum.**
  - 2. This common sum is as **large as possible**.
- Finally, return the **sum of the products of all pairs**.
- If pairing up with equal sum is not possible then return `-1`

---


**Examples & Constraints:**  
- Example 1:  
  - Input: arr = [4,2,1,5]
  - We can pair `(1, 5)` and `(2, 4)`.
  - Each pair sums to `6`, which is the maximum possible equal sum.
  - Compute sum of products:

  ```
  (1*5) + (2*4) = 5 + 8 = 13
  ```

 - Output: 13

**Tags:**  
$None$

**Similar Questions (if any):**  
$None$

---


## Question 2: Mallecious Printer   
**Description:**  

- You are given a graph which is constructed from `from_arr` and `to_arr` of same length.Each element of `from_arr` is mapped to `to_arr` and ***vise_cersa***. (idk why they named it `from` and `to`)
- There are `n` nodes.which is `1` to `n`
- You are also given an array of array `query`. Each query *may* says about *the level order printing of the graph* starting from `1`.
- There are `k` queries, you should return a resultant string `r` which is composed of `0` and `1` such that `1` says the queries is in proper order and `0` if not.
- Note the graph is connected and doens't have loops. 

---


**Examples & Constraints:**  
- Example 1:  
  - Input: `from_arr` = [1,1,2] , `to_arr` = [2,3,4] , `n` =4 , `queries` = [[1,2,3,4],[1,3,2,4],[2,1,3,4],[1,2,4,3]]  
  - Output: `result` = "1100"
  
  <img width="360" height="338" alt="image" src="https://github.com/user-attachments/assets/b249dc31-d9e8-40e8-bca2-c5ee6d913990" />
  
  -  for `query 0,1` it is possible to get the order since level wise this is proper
  -  but for `query 2` it can't start with `2` hence `0`
  -  for `query 3` ,`4` can't come before `2` coz 2 is not in the same level. 

**Tags:**  `graphs`,`bfs`,`sets`

**Similar Questions (if any):**  
$None$

---


### Thought Process  

- My thought process for `q1` is to sort it and use 2pointer to solve,but I am not sure it's the correct approach.
- But it solved 13/15 test cases

<br>

- For `q2` I did a smart way I did `bfs` and stored each level's resultant in an array `bfs` as sets.
- And for each query `q` in `query` I traversed `bfs` array linearly checking if the element is in that particular set which is the level.
- This solved `5/15` test cases,I believe my question and understanding of question is correct.If not I request those who attended tekion to help and correct. 
 


---

### Solution

$None$

---

> ***ANYONE CAN CONRIBUTE! LET'S BUILD A COMMUNITY!!**
