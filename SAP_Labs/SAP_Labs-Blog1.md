# SAP Labs

**Year:** 2025 
**Type:** Placement  

---

## Online Assessment Overview  
- Test duration was `1hr 50min`.
- consist of `2DSA` questions of **medium to hard** complexity.
- This test happened in SAPs platform and we could submit only once.
- we can run the code how many time ever we want,but sumbisssion is once.Once you submit it you can't change it remember that.
- we could give our own custom test cases and constraints were clearly given,IDE was user friendly.

---

## Question 1: *Maximum square in a boxes*  
**Description:**  
- you are given an array `arr` where each element is an integer.
- Each element represents the number of vertical stacks of boxes of `unit 1` .
- Find the length of maximum possible square.  

**Examples & Constraints:**  
- Example 1:
- `arr` = [3,2,5,4,3,4]
- Highlighted regions is the maximum sq possible which is `3`,hence `result` is `3`
  <br>
  
    <img width="394" height="331" alt="image" src="https://github.com/user-attachments/assets/4774bbad-b33a-4d71-b9fd-f24a852ebeca" />

- Example 2:
  - `arr` = [2,2,2]
  - Highlighted regions is the maximum sq possible which is `2`,hence `result` is `2`
    <br>

    <img width="199" height="155" alt="image" src="https://github.com/user-attachments/assets/ef1b91d7-87fa-4452-b638-c00a326f8a6a" />

- Example 3:
  - `arr` = [5]
  - No possible sq hence `-1`,hence `result` is `-1`.

    <br>

    <img width="228" height="281" alt="image" src="https://github.com/user-attachments/assets/d523c8e8-acf5-48d9-9335-bd5c9ed466ec" />

- Example 4:
    - `arr` = [3,2,5,7,6,7,5,1,2]
    - No possible sq hence `-1`,hence `result` is `-1`.
  
      <br>

  <img width="513" height="407" alt="image" src="https://github.com/user-attachments/assets/309d730b-3d54-4f11-b988-4fed5c449703" />

    
- Constraints:
  - $1<=arr[i]<=10^8$
  - $1<=array.length<=10^8$ 

**Tags:**  *arrays*,(maybe *monotonic stack* or *matrix*)

**Similar Questions (if any):**  
- [221.Maximal Square](https://leetcode.com/problems/maximal-square/description/))  
- [84.Largest Histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/)  

---

## Question 2: *Time for ambulance to reach Hospitals*  
**Description:**  
- You are given an integer `n` which is the number of vertices.
- you are given an array of array `edges`.
- Each element of `edges` are array of size `2` they mark the road between `[u,v]`.
- We are also given an `ambulance` which is in an Hospital.
- You have to find the *minimum time required time to reach all hospitals* ,if not return `-1`


**Examples & Constraints:**  
- Example 1:
  - `n` = 5 , `edges` = [[1,2],[2,3],[2,5],[3,4]] , `ambulance` = [1,4]
  - It would take `2` units of time to cover all hospitals and that is the answer  `2`.

  <br>
  <img width="707" height="473" alt="image" src="https://github.com/user-attachments/assets/156fb499-2739-4679-b747-d76a8a9c74df" />

- Example 2:
  - `n` = 3 , `edges` = [] , `ambulance` = [1,2,3]
  - since all ambulance can cover all the hospitals the answer  `0`.

  <br>
<img width="395" height="315" alt="image" src="https://github.com/user-attachments/assets/867df24d-3e38-4797-b611-e809d400fe9c" />

- Example 3:
  - `n` = 3 , `edges` = [[1,2]] , `ambulance` = [1,3]
  - It would take `1` unit of time to cover all hospitals and thus the answer  `1`.

  <br>
  <img width="265" height="276" alt="image" src="https://github.com/user-attachments/assets/4035b3f6-c84d-4e8a-b749-6413adf2adf5" />

  - Example 4:
  - `n` = 4 , `edges` = [[1,2],[2,3]] , `ambulance` = [1]
  - Hospital `4` is left out. Ths=us the answer is `-1`

  <br>
  <img width="370" height="337" alt="image" src="https://github.com/user-attachments/assets/b976e479-10cb-40c2-a2d9-c3587503658d" />


 
- Constraints:
  - $0<=edges[i]<=10^4$
  - $1<=n,ambulance<=10^4$

**Tags:**  *bfs*

**Similar Questions (if any):**  
 

---

### Thought Process  

 - for the `first question` you could create a matrix then do maximal area question but it would result in `MLE` and `TLE`.
 - for the `2nd questions` we could do `bfs` and use hashmap to store *min time to reach that hospital*. This hasmap helps us to find the disconnected hospitals. 

---



> ***ANYONE CAN CONRIBUTE! LET'S BUILD A COMMUNITY!!***
