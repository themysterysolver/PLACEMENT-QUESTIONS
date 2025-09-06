# VISA

**Year:** 2025
**Type:** Placement  
**Role:** SDE

---

## Online Assessment Overview  

- It happened on *codesignal*
- Total of `4` DSA question were asked of the type easy to medium.
- Test duration is 70minutes.
- 1st 2 questions were easy and rest are medium.
- The final evauluvation was for 600points.
- Each had a different question.

---

## Question 1: *Count the Zeroes*  
**Description:**  
- Given a array of non-negative interger `nums`,your task is to calculate how many elements of `nums` have an odd number of occurence of the digit `0`.
> **NOTE** You are not expected to provide the most optimal solution but a solution with TC not worse than $O(nums.length^2)$ will fit within the execution time limit. 

**Examples & Constraints:**  
- Example 1:
    - `nums` = [100,20,1,30,40]
    - idx 1,3,4 are counted since  they are the elemnts where zero is repeated odd number of times
    - *result = 3* 
- Example 2:
  - `nums` = [250,30,100]
  -  *result = 2* 
- Constraints:
  - They have explicitly said the Expected complexity. For this question $ o(n)^2 $ is acceptable .
  - $1\leq nums.length \leq 10^3$
  -  $1\leq nums[i] \leq 10^3$

**Tags:**  `Arrays`,`strings`


## Question 2: *The drone problem*  

**Description:**  
- There is a drone delivery system using drones in linear warehose.The warehouse is represented as a number lineinitially starting at position `0` and ending at position `target`(`target>0`).Along this line,there are *charging statios placed at certain positions,reprensted by an array `stations`,
  where `stations[i]` is the position of the *ith* charging station.

- Each drone has a limited battery that allows it to trave it to a maximum of 10units after being fully charged. For exampl,if a drone is charged at position `12`,it can travel to position `12`,`13`,`14`..,up to position`22` *(inclusive)*,but cannot reach position `23` or beyond without recharging.
- Your delivery prototcl requires the following steps:
  - From your current position,pick up the cargo and carry it on foot to the neares charging station ahead of you. I f there are no mote stations ahead,carry the cargo on foot to the target position.
  - Deploy a fully charged drone from this station and send it with the cargo as far as possble towards the target.If the target hasn't been  reached,walk to the point where the drone landed to retrieve the cargo,then repeat from step1.
-  Your *task* is to calculate the total distance over which you must carry the cargo on foot from position `0` to position `target` 

> **NOTE** You are not expected to provide the most optimal solution but a solution with TC not worse than `O(station.length*target)` will fit within the execution time limit.


**Examples & Constraints:**  
- Example 1:
  - `target = 23 ` and `stations = [7, 4, 14]` the output should be `solution(target, stations) = 4`
  - Starting at `0`, you find the nearest station at position `stations [1] = 4` so you carry the cargo on foot for ***4 units*** to get there, and then deploy a drone that travels to ***position 14***
  - There is another station at `14` (`stations [2] = 14`), which you use to deploy another drone that reaches the target position target `23`
  - Therefore, you camed the cargo on foot only units in total.

- Example 2:
    - For `target = 27` and `stations = [15, 7, 3, 10]` , the output should be `solution(target, stations) = 7`
    - Starting at position `0`, you find the nearest station ahead is at position `stations[2]=3` . So you carry the cargo on foot for ***3 units*** to get there, and then deploy a drone that travels to `position 13`.
    - From position `13` the nearest station ahead is at position `stations[0]= 15` ,which requires carrying the cargo on tool for ***2 more units***, and from there your drone reaches `position 25`
    - There are no more stations ahead, so you cary the cargo on foot for 2 more units to the target poten
    - Therefore you caried the cargo on foot `3+2+2=7 units` in total
  
- Constraints:
  - $1 \leq target \leq 1000 $
  - $0 \leq stations.length \leq 200$   !!! WATCH OUT HERE
  - $1 \leq stations[i]<target \leq 200 $

**Tags:**  `Greedy`, `simulation`

## Question 3: *Library Insurance calculation*  
**Description:**  
 

**Examples & Constraints:**  
- Example 1: 
- Example 2: ...  
- Constraints: ...  

**Tags:**  `Array`, `Strings` , `Design System` ,`heap` ,`set` , `HashMap`
 
---

### Thought Process  
Explain how you approached the problem. Mention key observations, edge cases, and possible optimizations.  

---

### Solution  
*(Keep your code and explanation separate from the problem statement)*  


// Your solution here
> ***ANYONE CAN CONRIBUTE! LET'S BUILD A COMMUNITY!!***
