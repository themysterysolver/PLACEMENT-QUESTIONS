# Apple

**Year:** 2025  
**Type:** Placement  
**Role:** SDE
---

## Online Assessment Overview  

- Duration of the test is `1Hr 50mins`
- It has *12q* in total *10 MCQS* and *2 coding question-dsa*
- MCQ focused on basics of programming(c++,java),aptitude,OS(paging , LRU),Networks(Bit rate calculations with RTT and TCP) which had a weightage of *2points*
- Both the DSA questions were of they type ***mid(Easy-medium) level***. Lot of folks were able to solve if they are good at both problem solving,logical thinking and DSA. 
- This happened in their own platform which was unique and user friendly *coderpad* ,
  - They gave all the test cases to be passed.
  - There were no hidden one test cases,each tets case had a **name** and `IP` along with it's `OP`
  - The examiniee wants you to pass all the tetscases in small time.
- I don't think `TLE` is possible in given questions since eveything is straight forward.
  
> **NOTE:** Turn off all your notification on ur lap since the platform is sensitive to all kind of disturbance and you will be kicked it out without any warning.  

---

## Question 1: *Cost to run the hotel*  
**Description:**  

- You are given a hotel with lots of tables to occupy called `available`
- You are also a given an array `people` which denotes the time when a person comes to the hotel and occupy the seat if available,each person is denoted by  their id
  `id` which is `people[i]`.
- *Eg:* `[1,1,2,2,3,4,5,3,4,5]`
  - The 1st one(id) indicates the person with id one reaches the hotel
  - The 2nd one(id) indicates the person left the the seat.
- A person can occupy a **seat** if *available* ,else
- wait for the seats to be empty or get bored and leave the queue.
- You are also given `cost` which maps to the people's id to the index of cost.
- If a customer is already visited, he is charged atmost once.But he can still occupy the seats. 
- Your task it to calculate the total cost the *hotel earned* by `EOD`
  
**Examples & Constraints:**  
- Example 1: *available* = 2  people = [1,2,1,2,3,0,2,1,4,3,0,1,4] cost = [10,20,30,40,50]
    - `idx = 0` => *1* enters thus avail becomes 1
    -  `idx = 1` => *2* enters thus avail becomes 0
    -  `idx = 3` => *1* leaves the hotel,pays for the seat which is cost[`1`] = *20*,hence avail becomes *1*
    -  `idx = 4` => *3* enters thus avail becomes 0
    -  `idx = 5` => *0* waits in the q
    -  `idx = 6` =>  *1* leaves the hotel,pays for the seat which is cost[`2`] = *30*,hence avail becomes *1* and *0* occupies the avail.The net avail is 0. Total cost = 50.
    -  `at idx 7,8` => both `1,4` enters the q
    -  `idx = 9` => *3* pays and leaves, `1` enters
    -  `idx = 10` => `1` just leaves since he already visited the hotel
    -  `idx = 11` => `4` pays and leaves
    -  Hence `total = 150`
      
- Example 2: *available* = 1  people = [1,0,0,1,2,2,1,1] cost = [10,20,30]
    - `idx = 0` => *1* enters thus avail becomes 0
    - `idx = 1` => *0* enters waiting room
    - `idx = 3` => *0* get's bored and leaves the hotel,because no seats is available
    - `idx = 4` => *1* pays and leaves, avail becomes 1
    - `at idx 5,6` => *2 enters,leaves and pays
    - `at idx 7,8` => no need to pay since he has already visited.
    - Hence `total = 20+30 = 50`

- Example 3: *available* = 2  people = [1,0,3,3,0,3,3,1] cost = [10,20,30,100]
  - `idx = 0` => *1* enters thus avail becomes 1
  - `idx = 1` => *0* enters thus avail becomes 0
  - `idx = 2,3` => *3* enters and leaves,since it's bored
  - `idx = 4` => `0` leaves and pays,avail becomes one and total becomes `10`.
  - `idx = 5,6` => *3* enters,leaves and pays, avail becomes back to 1 again and cost becomes `110`
  - `idx = 7` => *1* leaves and pays,  cost ..`130`
- Example 4: *available* = 2  people = [1,0,3,2,4,5,3,0,2,4,5,3,3,1] cost = [10,20,30,100,60,70]
  - Here at `idx = 2,3,4,5` *3,2,4,5* enters the **queue**
  -  `idx = 6` => *3* leaves(bored)
  -  `idx = 7` => *0* pays and leaves,`2` enters the avilable room and leaves
  -  `idx = 8,9` => similar tot hat of above step
  -  the next indices are similar to the above example
  -  `total` = 10(@7)+30(@8)+60(9@)+70(@10)+20(@14) = **190** 
- Constraints:
  <br>
  $1 \leq available \leq 100$
  <br>
  $cost.length = max(people[i])$  

**Tags:**  `Arrays`, `sets`, `queue`, `simulation`



---

## Question 2: *Score board of a tennis game*  
**Description:**  

- Tennis game follows the below rules
- The 1st win is considered as `15` points, the second one is `30` and the third one is `40`.
- A player wins if he is in 
- A player is said to be in,
    - **Advantage:** 
    - **Duece:**
    - **Game:**
    - If he has scored more than `40 points`
- You are given list `score` which consist of number of wins be each player.
- You should return the `points table` as per the diagram given above.
  
**Examples & Constraints:**  
- Example 1:  score = [`P1`] , result = "P1 15" 
- Example 2:  score = [`P1`,`P2`,`P2`] , result = "P1 15 - P2 30" 
- Example 3:  score = [`P1`,`P2`] result = "15a"
- Constraints:
    - $1 \leq score.length \leq 20 $

**Tags:**  `counting`,`simulation`,`hash table`




### Thought Process  
Explain how you approached the problem. Mention key observations, edge cases, and possible optimizations.  

---

### Solution  
*(Keep your code and explanation separate from the problem statement)*  


> ***ANYONE CAN CONRIBUTE! LET'S BUILD A COMMUNITY!!***
