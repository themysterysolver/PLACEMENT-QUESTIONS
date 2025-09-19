# Netradyne

**Year:** 2025  
**Type:** Placement  
**Role:** SDE/Security
---

## Online Assessment Overview  
- Duration `1.5Hrs`
- Test conducted in ***HackerEarth*** platform. Consists of `13` questions => 11MCQ(3-4 OS,DSA,Logical reasoning) followed by `2DSA`
- Each MCQ carried abt 2,4,6 marks. DSA q carried `45` and `60` marks.
- 1st DSA q was not language restricted,the 2nd q must be coded in either c++ or JAVA.

---

## Question 1: *Movie tickets*  
**Description:**  
- Assume that there are 100 slots available for every movie.
- Given Q queries of the following types:
  - `BOOK X Y`
    - Allow a customer with a unique ID X to book a ticket for a movie with the movie ID Y.
    - If the customer has already booked a ticket for the same movie or the movie is sold out, return false.
    - Otherwise, mark the ticket as booked and return true.
   - `CANCEL X Y`
      - Allow a customer with a unique ID X to cancel a booked ticket for a movie with the movie ID Y.
      - If the customer has not booked a ticket for the movie, return false
      - Otherwise, mark the ticket as canceled and retum tue.
    - `IS_BOOKED X Y`
      - Check if a customer with a unique ID X has booked a ticket for the movie with the movie ID Y.
      - Return true if booked, otherwise, return false.
    - `AVAILABLE_TICKETS Y`
      - Return the number of available tickets for the movie with the movie ID Y.

### Class description
- MovieTicket: Represents information about the users and movies
- Public functions: Refers to the types of queries (described above) that must be implemented

### Input format for custom testing
> Note: Use this input format if you are testing against custom input or writing code in a language where we don't provide boilerplate code.
- The first line contains a single integer `Q`, denoting the number of elements in the array.
- Each of the next Q lines contains the **query** (case-sensitive for strings).

### Output format
- Return the result for each function method based on the query


- Software Design Applied knowledge in implementing SOLID principles -> Apply SOLID principles in coding with respect to design by considering performance and efficiency

**Examples & Constraints:**  
- Example 1:
  - Input
  ```
  10
  113000
  AVAILABLE TICKETS 1
  IS BOOKED 11
  CANCEL
  AVAILABLE VICKETS 1
  25 BOOKED 11
  B001-4
  15 BOOKED 15
    
  ```
  - Output
  ```
  Booked Successfully!
  Available ticket count is 99
  Ticked is Booked!
  Canceled Successfully!
  Available ticket count is 100
  Ticket isn't booked!
  Booked Successfully!
  Booked Successfully?
  Ticket isn't booked!
  Couldn't cancel!
  ```
  - Here, the number of quenes are, Q = 10
  - *Query 1*
    - Inputs BOOK 11
    - Outputs Booked Successfully!
    - Explanations Customer 1 successfully booked a ticket for Movie Available tickets for Movie 1 were reduced to 99
  - *Query 2*
    - Inputs AVAILABLE TICKETS 1
    - Outputs Available ticket count is 99
    - Explanations. The system reports 99 available tickets for Movie 1
  - *Query 3*
    - Inputs IS BOOKED 11
    - Outputs Tickets Bookedt
    - Explanations Confirmation that Customer 1 has tooked a ticket for
      Movie 1
  - *Query 4*:
      - Inputs CANCEL 11
      - Outputs Canceled Successfully!
      - Explanations Customer 1 successfully canceled the booking for Movie 1 Available tickets for Movie 1 were increased to 100
  - *Query 5*:
      - Inputs AVAILABLE TICKETS 1
      - Outputs Available ticket count is 100
      - Explanations The system reports 100 available tickets for Movie 1 after cancellation
  - *Query 6*:
    - Inputs IS BOOKED 11
    - Outputs Ticket isn't booked!
    - Explanations. Confirmation that Customer I's booking for Movie 1 is successfully canceled
  - Query 7:
    - Inputs: BOOK 13.
    - Outputs Booked Successfully!
    - Explanations: Customer 1 successfully booked a ticket for Movie 3
  - Query B:
      - Inputs BOOK 14
      - Outputs Booked Successfully!
      - Explanations Customer 1 successfully booked a ticket for Movie 4
  - Query 9:
      - Inputs IS BOOKED 15
      - Outputs Ticket isn't booked!
      - Explanations Venfication that customer 1 hasn't booked a ticket for Movie 5
  - Query 10:
    - Inputs: CANCEL 15
    - Outputs Couldn't cancell
    - Explanations Attempting to cancel a non-booked ticket for Movie 5 by Customer 1, but it fails.
> Note:Your code must be able to print the sample output from the provided sample input. However, your code is run against multiple hidden test cases. Therefore, your code must pass these hidden test cases to solve the problem statement.

#### Limits

- Time Limit 10 sec(s) for each input file
- Memory Limit 256 MB
- Source Limit: 1024 KB
      
- Constraints:
  - $1 \leq Q \leq 5000$
  - $1 \leq X, Y \leq 10^3$

**Tags:**  `Design` , `HashTable`


## Question 2: *String pattern expansion*  
**Description:**  
- Refer the link below.Exact same problem!

**Tags:**  `stack`

**Similar Questions (if any):**  
- [Decode the string]((https://www.geeksforgeeks.org/problems/decode-the-string2444/1))  

---

### Thought Process  

- The 1st question is pretty straight forward. The problme I faced are,
  - Getting input and processing the queries.
  - Create class and function defenition.
  - There is no distinction between debug output and actual output.Also,the output is limited by 10-15lines which makes debugging hard.
  - Having constraints for 100 Seats I can't possible type BOOK 1 1,BOOK 2 1,.....and so on to check my output.
  - All the `Strings` which should be displayed was little irritating,I had `!` and cases sensitive characters.
- But if u wanna learn approach we could just do this with `2` hash tables. one to map the user->movie relation and another to counf the movie->avaialble seat realtion.

- The 2nd question is using stack and very famous problem. I solved it yesterday,so it was fun. This q is lang specific to JAVA.

---

### Solution - 1

```python3 []

from collections import detauitdict

class MovieTiket:
  def __init__(self):
    self.movieUser = defaultdict(set)
    self.movieCount = dict()
  def book(self,X,Y): #X-userID and Y-movieID
    if Y in self.movieCount:
      if X in self.movieUser[Y] or self.movieCount[Y] l = 0 :
         return "Ticket isn't booked!"
      self.movieUser[Y].add(X)
      self.movieCount [Y]-=1
      return "Booked Successfully!"
    else:
      self.movieCount [Y] = 99
      self.movieUser[Y].add(X)
      return "Booked Successfully!"
  def cancel(self,X,Y):
    if X in self.movieUser [Y]:
      self.movieUser[Y].remove(X)
      self.movieCount [Y]+=1:
      return "Canceled Successfully!"
  else:
    return "Couldn't cancel!"
  def isBooked(self,X,Y):
    if X in self.movieUser[Y]:
      return "Ticket is Booked!"
    else:
      return "Ticket isn't booked!"
  def availableTickets (self,Y):
    if self.movieCount [Y]>0:
      return "Available ticket count is "+self.movieCount [Y]
    else:
      return "Ticket isn't available!"


n = int(input())
m = MovieTiket()
for _ in range(n):
  q = input()
  qa = q.split()
  if qa[0] == 'BOOK':
    print(m.book(int(qa[1]),int(qa[2])))
  elif qa[0] == 'CANCEL':
    print(m.cancel(int(qa[1]), int(qa[2])))
  elif qa[0] == 'AVAILABLE_TICKETS':
    print(m.availableTickets(int(qa[1])))
  elif qa[0] == 'IS_BOOKED':
    print(m.isBooked (int(qa[1]),int(qa[2])))
```

### Solution - 2

```Java [ ]
class Solution {
    public String decodedString(String s) {
        Stack<String> stack = new Stack<>();
        Stack<Integer> numStack = new Stack<>();
        int num = 0;

        for (char c : s.toCharArray()) {
            if (Character.isDigit(c)) {
                num = num * 10 + (c - '0');r
            } else if (c == '[') {
                stack.push("[");
                numStack.push(num);
                num = 0;
            } else if (c == ']') {
                // Pop until '['
                StringBuilder temp = new StringBuilder();
                while (!stack.isEmpty() && !stack.peek().equals("[")) {
                    temp.insert(0, stack.pop());
                }
                stack.pop();
                int count = numStack.pop();
                StringBuilder repeated = new StringBuilder();
                for (int i = 0; i < count; i++) {
                    repeated.append(temp);
                }
                stack.push(repeated.toString());
            } else {
                stack.push(String.valueOf(c));
            }
        }

        StringBuilder result = new StringBuilder();
        for (String str : stack) {
            result.append(str);
        }

        return result.toString();
    }
}

```
```Python [ ]
class Solution:
    def decodedString(self, s):
        # code here
        stack = []
        numStack = []
        num = 0
        for c in s:
            if c.isdigit():
                num*=10
                num+=int(c)
            elif c == '[':
                stack.append(c)
                numStack.append(num)
                num = 0
            elif c!=']':
                stack.append(c)
            else:
                string = ''
                while stack and stack[-1]!='[':
                    el = stack.pop()
                    string = el+string
                stack.pop()
                stack.append(string*numStack.pop())
                
        return ''.join(stack)
```


// Your solution here
> ***ANYONE CAN CONRIBUTE! LET'S BUILD A COMMUNITY!!***
