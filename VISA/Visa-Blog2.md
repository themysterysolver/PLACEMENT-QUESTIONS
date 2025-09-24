# VISA

**Year:** 2025
**Type:** Placement  
**Role:** SDE

---

## Online Assessment Overview  

- It happened on *codesignal*
- Total of `4` DSA question were asked of the type easy to medium.
- Test duration is 70 minutes.
- 1st 2 questions were easy and rest are medium.
- The final evauluvation was for 600 points.
- Each had a different question.

---

## Question 1: *Count the Zeroes*  
**Description:**  
- Given a array of non-negative interger `nums`, your task is to calculate how many elements of `nums` have an odd number of occurence of the digit `0`.
> **NOTE** You are not expected to provide the most optimal solution but a solution with TC not worse than $O(nums.length^2)$ will fit within the execution time limit. 

**Examples & Constraints:**  
- Example 1:
    - `nums` = [100,20,1,30,40]
    - idx 1, 3, 4 are counted since they are the elemnts where zero is repeated odd number of times
    - *result = 3* 
- Example 2:
  - `nums` = [250,30,100]
  -  *result = 2* 
- Constraints:
  - They have explicitly said the Expected complexity. For this question $ o(n)^2 $ is acceptable .
  - $1\leq nums.length \leq 10^3$
  -  $1\leq nums[i] \leq 10^3$

**Tags:**  `Arrays`,`strings`

[Hackerrank challenge link](https://www.hackerrank.com/contests/placement-questions-mit/challenges/count-the-zeroes-2)

---

## Question 2: *The drone problem*  

**Description:**  
- There is a drone delivery system using drones in linear warehose. The warehouse is represented as a number line initially starting at position `0` and ending at position `target`(`target>0`).Along this line, there are *charging stations* placed at certain positions, reprensted by an array `stations`,
  where `stations[i]` is the position of the *ith* charging station.

- Each drone has a limited battery that allows it to traverse it to a maximum of 10 units after being fully charged. For example, if a drone is charged at position `12`, it can travel to position `12`,`13`,`14`..,up to position`22` *(inclusive)*, but cannot reach position `23` or beyond without recharging.
- Your delivery protocol requires the following steps:
  - From your current position ,pick up the cargo and carry it on foot to the nearest charging station ahead of you. If there are no more stations ahead, carry the cargo on foot to the target position.
  - Deploy a fully charged drone from this station and send it with the cargo as far as possble towards the target. If the target hasn't been reached, walk to the point where the drone landed to retrieve the cargo, then repeat from step 1.
-  Your *task* is to calculate the total distance over which you must carry the cargo on foot from position `0` to position `target` 

> **NOTE** You are not expected to provide the most optimal solution but a solution with TC not worse than `O(stations.length*target)` will fit within the execution time limit.


**Examples & Constraints:**  
- Example 1:
  - `target = 23 ` and `stations = [7, 4, 14]` the output should be `solution(target, stations) = 4`
  - Starting at `0`, you find the nearest station at position `stations [1] = 4` so you carry the cargo on foot for ***4 units*** to get there, and then deploy a drone that travels to ***position 14***
  - There is another station at `14` (`stations [2] = 14`), which you use to deploy another drone that reaches the target position target `23`
  - Therefore, you camed the cargo on foot only units in total.

- Example 2:
    - For `target = 27` and `stations = [15, 7, 3, 10]` , the output should be `solution(target, stations) = 7`
    - Starting at position `0`, you find the nearest station ahead is at position `stations[2]=3`. So you carry the cargo on foot for ***3 units*** to get there, and then deploy a drone that travels to `position 13`.
    - From position `13` the nearest station ahead is at position `stations[0]= 15`, which requires carrying the cargo on tool for ***2 more units***, and from there your drone reaches `position 25`
    - There are no more stations ahead, so you cary the cargo on foot for 2 more units to the target poten
    - Therefore you caried the cargo on foot `3+2+2=7 units` in total
  
- Constraints:
  - $1 \leq target \leq 1000 $
  - $0 \leq stations.length \leq 200$   !!! WATCH OUT HERE
  - $1 \leq stations[i]<target \leq 200 $

**Tags:**  `Greedy`, `simulation`

[Hackerrank challenge link](https://www.hackerrank.com/contests/placement-questions-mit/challenges/optimal-drone-deployment)

---

## Question 3:  **Library Insurance**  
**Description:**  

 - You are given a sequence of `operations` that represent ***activities*** in a library. Each operation is one of the types `acquisition`, `checkout`, or `reclassify`
 -  Operations are provided in the following
    - ["acquisition", "<book category>", "<quantity>", "<price>"] -the library acquires **<quantity>** books of **<book category>**, each valued at **<price>** for insurance purposes.
    - ["checkout", "<book category>", "<quantity>"] - patrons borrow **<quantity>** books of book category. If books of the specified category have different insurance values, the least valuable ones should be checked out first. It is guaranteed that the library will always have enough books to fulfill all checkout requests.
    - ["reclassify", "<book category>", "<quantity>", "<original price>", "<new price"]-the library reclassifies ***<quantity>*** books of ***<book category>*** to a more valluabile edition. It is guaranteed that there are **<quantity>** books of the specified category with the **<original price>** value.

- Your function should calculate the *total insurance value of all books checked out after processing the entire sequence of operations*. **Return an array representing the insurance value of books for each Checkout-operation.**

> `Note` you are not expected to provide the most optimal solution but a solution with time complexity less than $(operations.length^)$.

**Examples & Constraints:**  
- Example 1:
    - Input
      ```
      operations = [
        ["acquisition", "fiction", "2", "100"],
        ["acquisition", "reference", "3", "60"],
        ["checkout", "fiction", "1"],
        ["checkout", "reference", "1"],
        ["reclassify", "reference", "1", "60", "100"],
        ["checkout", "reference", "1"].
        ["checkout", "reference", "1"]
      ]
      ```
    - the output should be `solutions(operations) = [100, 60, 60, 100]`
    - `["acquisition", "fiction", "2", "100"]` - the library acquires fiction books, each valued at 100
    - `["acquisition", "reference", "3", "60"]` - the library acquires 3 reference books, each valued at 60
    - `["checkout", "fiction", "1"]` - a patron checks out 1 fiction book valued at 100, so the neurance value is 1 x 100 100
    - `["checkout", "reference", "1"]` a patron checks out 1 reference book valued at 60, so the Insurance value is 1 x 60 = 60.
    - `["reclassify", "reference", "1", "60", "100"]` one reference book is reclassified and its value becomes 100
    - `["checkout", "reference", "1"]` -a patron checks out 1 reference book. There are 2 reference books in the library with values of 60 and 100 and the one with the value of 60 should be checked out first, so the insurance value is 1 x 60 60
    - `[checkout", "reference", "1"]` a patron checks out 1 reference book. There is 1 Heference book in the library with the value of 100 so the insurance value is 1 x 100 = 100
      

  
- Constraints:
  - $1 \leq operations.length \leq 100$ 

**Tags:**  `Array`, `Strings` , `Design System` ,`heap` ,`set` , `HashMap`

[Hackerrank challenge link](https://www.hackerrank.com/contests/placement-questions-mit/challenges/library-insurance)

---

## Question 4: *Longest common prefix*  
**Description:**  
- Given length of  arrays of numbers, `firstArray` and `secondArray` Return the *length* of the `longest common prefix (LCP)` between any pair of numbers from different arrays or `0` if no common prefix is found.
- A prefix of a number is a number formed by one or more of its digits, starting from its highest digit. For example, `123` is a prefix of the number `12345` and `2` is a prefix of the number `234`. A common prefix of two numbers is a number, which is a prefix of both. For instance, longest mmon prefix (LCP) of `5655359` and `56554` is `5655` and there is no common prefix of `123` and `456`

 **Examples & Constraints:**  
- Example 1:
  - For firstArray [25, 288, 2655, 54546, 54, 555] and secondArray [2, 255, 26, 244, 26, S. 54547] the output should be ***solution(firstArray, secondArray) = 4*** 
 - The best pair is `54546` from the first array and `54547` from the second array with the LCP `5454` where 5454 is of length `4`.

- Example 2:
  - For FirstArray[25, 288, 2655, 544, 54, 555] and secondArray [2, 255, 266, 248, 26, 5, 5444444] the output should be ***solution(firstArray, secondArray) = 3***
  - The best pair is `544` from 1st array and `5444444` from second array. hence LCP is 544,thus ans is 3. 


- Constraints:
  - $1 \leq firstArray.length \leq 10^5$
  - $1 \leq secondArray.length \leq 10^5$
  - $1 \leq firstArray[i] \leq 10^9$
  - $1 \leq secondArray[i] \leq 10^9$

**Tags:**  `Trie` ,`DFS` , `Hashmap`

 **Similar Questions:**  
 - [3043.Length of longest common prefix](https://leetcode.com/problems/find-the-length-of-the-longest-common-prefix/)
   - Here in this question we have done one way around,but for our question we should construct `2` tries and need to traverse them both!

[Hackerrank challenge link](https://www.hackerrank.com/contests/placement-questions-mit/challenges/longest-common-prefix-65)

---

### Thought Process  
- `q1` is just  a simple counting problem
- `q2` can be done greedily,since constraint is small we can iterate and find out the answer.
- `q3` is a pure simulation,but the processing of each query is annoying and takes time.
- `q4` can be done by 2tries.

---

### Solution - 2

```
def droneAndDistance(stations,target):
    if not stations:
        return target
    steps, curr = 0, 0
    stations = set(stations)
    while curr<target:
        if curr in stations:
            curt+=10
        else:
            steps += 1
            curr += 1
    return steps
```

### Solution - 4

- The below solution works for LCP for all pairs!

```
class TrieNode:
    def __init__(self):
        self.child = dict()
        self.end = False

class Trie:
    def __init__(self):
        self.root = TrieNode()
    
    def __insert__(self,word):
        current = self.root
        for w in word:
            if w not in current.child:
                current.child[w] = TrieNode()
            current = current.child[w]
        current.end = True

    def startsWith(self,word):
        count = 0
        current = self.root
        for w in word:
            if w in current.child:
                count+=1
                current = current.child[w]
            else:
                return count
        return count
class Solution:
    def longestCommonPrefix(self, arr1: List[int], arr2: List[int]) -> int: ## arr1--->firstArray ,arr2---->secondArray
        arr1 = list(map(str,arr1))
        arr2 = list(map(str,arr2))

        myTrie = Trie()
        for w in arr2:
            myTrie.__insert__(w)

        maxi = 0
        for w in arr1:
            maxi=max(maxi,myTrie.startsWith(w))

        myTrie = Trie()
        for w in arr1:
            myTrie.__insert__(w)


        for w in arr2:
            maxi=max(maxi,myTrie.startsWith(w))
        return maxi
```



// Your solution here
> ***ANYONE CAN CONRIBUTE! LET'S BUILD A COMMUNITY!!***
