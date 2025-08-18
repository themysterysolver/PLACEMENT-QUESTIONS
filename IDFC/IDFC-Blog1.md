# IDFC

**Year:** 2025
**Type:** Placement 

---

## Online Assessment Overview  

- Test happened in their platform.
- It had both *technical MCQ* and *coding* [2 DSA Questions] .
- MCQ's were focused on `OOPS,networks,DSA,language oriented,aptitude`.
- The coding round lasted `40 mins`
- Both were **easy** in difficulty.
- *Weightage is more towards MCQs*

---

## Question 1: *Spiral Matrix*  
**Description:**  
- You are given an integer number `n` which is ***odd*** .construct a square matrix starting from center of the matrix with number 1 and winding outwards as a spiral.
- Find the *sum of diagonals of such matrix*.

**Examples & Constraints:**  

- Example 1: `n = 3`
  - Output is `1+5+9+3+7 = 25`
```
5 4 3
6 1 2
7 8 9
```  
- Example 2: `n = 5 `
  - Output is `1+9+25+5+17+3+13+7+21 = 101`
```
17 16 15 14 13
18  5  4  3 12
19  6  1  2 11
20  7  8  9 10
21 22 23 24 25

```
- Example 3: `n = 7`
  - Output is `261`
```
43 44 45 46 47 48 49
42 21 22 23 24 25 26
41 20  7  8  9 10 27
40 19  6  1  2 11 28
39 18  5  4  3 12 29
38 17 16 15 14 13 30
37 36 35 34 33 32 31


```
**Tags:**  `Math`,`Matrix`,`Simulation`

---

## Question 2: *Reverse the String*

**Description:**

- You are given a string `s`.
- Construct and return the reversed string.

**Examples & Constraints:**

- Example 1: `s = "hello"`
  - Output: `"olleh"`

- Example 2: `s = "placements"`
  - Output: `"stnemalcp"`
  
**Tags:** `String`, `Two-Pointer`, `Simulation`


---
## Thought Process  
### Solution  

- For `question 1` I did the long way in the TEST,I simulated the matrix and then found out the matrix sum.Which took me a lot of time.
```python3 []
def spiral(n):
    mat = [[0]*n for _ in range(n)]
    x = y = n//2
    sq = n*n
    num = 1
    mat[x][y] = num
    num += 1
    directions = [(0,1),(-1,0),(0,-1),(1,0)] #R,U,L,D
    step = l = 1
    while num<sq:
        for idx,(dx,dy) in enumerate(directions):
            for _ in range(l):
                if num>sq:
                    break
                x += dx
                y += dy
                mat[x][y] = num 
                num += 1
            if idx&1 == 1:
                l+=1
    
    sumx = 1
    c = n//2
    for i in range(n):
        for j in range(n):
            if i == j and i!=c:
                sumx+=mat[i][j]
            if i+j == n-1 and i!=c:
                sumx+=mat[i][j]
    display(mat)
    return sumx

def display(mat):
    for row in mat:
        print(row)
    print('----------')
print(spiral(5))
print(spiral(7))
    
```

- I did the math way and the smart way just recognizing the pattern,there is ***no need to generate the matrix***,we just need to track the *number* and *running sum*

```python 3[]
'''
17 16 15 14 13
18  5  4  3 12
19  6  1  2 11
20  7  8  9 10
21 22 23 24 25 
'''

def spiral(n):
    sumx = 1
    curr = 1
    diff = 2
    sq = n*n
    while curr<sq:
        for _ in range(4):
            curr += diff
            #print(curr)
            sumx+=curr
        diff += 2
    #print('----------------')
    return sumx
#print(spiral(5))

for i in range(20):
    print(i,spiral(i))
```
```JAVA []
public class spiral {

    public static int diagonalSum(int N) {
        if (N == 1) return 1;

        long runner = 1;
        long sum = 1;
        long difference = 2;

        while (runner < N * N) {
            for (int i = 0; i < 4; i++) {
                runner += difference;
                if (runner > N * N) {
                    break;
                }
                sum += runner;
            }
            difference += 2;
        }

        return (int) sum;
    }

    public static void main(String[] args) {
        for(int i=0;i<20;i++){
            System.out.println("Diagonal sum for N=" + i + " is: " + diagonalSum(i));
        }
        
    }
}

```

- For the 2nd question I just returned `return s[::-1]`


> ***ANYONE CAN CONRIBUTE! LET'S BUILD A COMMUNITY!!***
