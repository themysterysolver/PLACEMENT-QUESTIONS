# Samsung

- **Year:** 2025 
- **Type:** Placement
- **Role:** SDE
---

## Online Assessment Overview  

- 3hrs -> 1 question (medium-hard)
- Question can be solved in 4 languages `c,c++,PY,JAVA`
- **IMPORTANT NOTE abt IDE**,
  - The test will happen in `Samsung SW Certificate certificate`,the IDE wasn't user friendly.This is a software which was asked to install by samsung.
  - It is strict in proctoring,it doesn't allow any kind of tab switches,screenshots,or screen switches,applications,notification.It just zooms in and doesn't let's u go out.
  - you have to enter `userID` and `password` make sure you have to note it before you enter the application. Because once you enter it,you can't go back.
  - Now let's come to IDE. It was really bad tbh. Python users are just dead. You have to intend each line using tab space from the first using backspace first.If not you get an intendation error.
  - You have to get input and output(this is not a bad thing) but the output format is different,you have to only print the answer in the format they specified using format specifier using `#`.It might vary during your time,but check it out guys. 
  - custom input can be given,you have few test cases to pass.
- 50 test cases in total
---

## Question 1: *Flight*  
**Description:**  

- You are given a game of flight. which is `N*5` matrix.
- You are given a flight which is in the center of the game.
- You can move either left or right or stay in the same position.
- The game always shows you the visible 5*5 portion of the game.
- The board contains `0` empty cell, `1` coins , `2` robot.
- Each time you move the flight left or right,the board moves down that is the bottom most rows dissapears and the to row enters the game's visible range.
- You have one nuclear weapon in your flight.You can use it only once.But when you use it,all the `R` in the visible region of the board dissapears.
- When u colide with coins,you take it.If u meet a robot it snatches a coin.
- If the coin coint reaches -1 before reaching the end of the game,u loose.
- Maximise the number of coins that can be obtained by doing these operations.
- If there is now way to reach to the end with some coins,you loose.
- Initially you have `0` coins and you start initially at position 2 in obased array.

#### Input format

- You will `t` an integer which tell how many test cases will be given.
- Followed by `t` test cases with ,
  - 1st line consisting of integer `k`
  - Next `k` lines is a space seperated numbers 0,1,2 

**Examples & Constraints:**  
- Example 1:  
- Example 2:   
- Constraints:
  - $1 \leq n \leq 50$
  - $width = 5$

**Tags:**  `dfs`,`matrix`,`backtracking`,`simulation`

**Similar Questions (if any):**  

- [Minesweeper](https://leetcode.com/problems/minesweeper/description/)

---

### Thought Process  
- It might worked,I simulated the problem.I made a mistake in printing the result with format specifier. So I got 0/50.But my logic wokred for 3/5 visible test cases.
- I just simulated the problem using dfs and backtracking.
 

---

### Solution  

```python []
n = 8

flag = [False]
maxi = [0]

def dfs(idx,toDo,coins,pos):
    if idx == n:
        if coins<0:
            return
        flag[0] = True
        maxi[0] = max(maxi[0],coins)
    else:
        if coins<0:
            return
        for d in [-1,0,1]:
            x=pos+d
            if x<0 or x>=5:
                continue
            val = 0
            if nums[idx][x] == 2:
                val = -1
            elif nums[idx][x] == 1:
                val = 1
            if toDo:
                sidx = set()
                for i in range(idx+1,min(idx+1,n)):
                    for j in range(5):
                        if nums[i][j] ==  2:
                            sidx.add((i,j))
                            nums[i][j] = 0
                dfs(idx+1,False,coins+val,x)
                for a,b in sidx:
                    nums[a][b] = 2
            else:
                dfs(idx+1,True,coins+val,x)

nums = []
for y in [1,2,3]:
    dfs(0,True,0,y)
print(maxi[0])

                
            
    
```


// Your solution here
> ***ANYONE CAN CONRIBUTE! LET'S BUILD A COMMUNITY!!***
