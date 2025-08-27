# VISA Placement Assessment 2025

**Type:** Placement

---

## Overview

- **Duration:** 70 minutes
- **Questions:** 4 coding questions
- **Focus:** Simulation and design, mostly on arrays and strings.

---

## Question 1: Ups and Downs

**Description:**  
You are given an array consisting of only the characters `"U"` (up) and `"D"` (down). You start at position `0`.  
Each `"U"` increases your position by 1, and each `"D"` decreases your position by 1.

**Task:**  
After processing the entire array, return:
- `"U"` if your final position is above the starting point,
- `"D"` if your final position is below the starting point,
- `""` (empty string) if you end up exactly at the starting point.

**Example 1:**
```

Input:
moves = ["U", "D", "D", "U", "U", "U"]

Process:
Start at 0
U: 1
D: 0
D: -1
U: 0
U: 1
U: 2

Output:
"U"

```

---

## Question 2: Number of Cycles

**Description:**  
You are given an array of resources, each being either `"A"` or `"P"`, with all `"A"`s appearing before any `"P"`s (the array is of the form `["A", ..., "A", "P", ..., "P"]`).  
You are also given a positive integer `resourceConstraint`.

**Process:**  
On each cycle, choose one of the following options:

1. **Option 1:** If there are at least `resourceConstraint` `"P"`s:
    - Remove exactly `resourceConstraint` `"P"`s from the array.
    - Append one new `"A"` to the end of the `"A"` block (just before the first "P", or at the end if no "P" remains).
2. **Option 2:** If not enough `"P"`s for option 1, but at least one `"A"`:
    - Change the last `"A"` in the array into a `"P"`.
3. **Option 3 (Halt):** If neither option is possible, halt the process.

**Goal:**  
Return the **total number of cycles** completed until the process halts.

---

**Example:**
```

Input:
resources = ["A", "A", "A", "P", "P", "P"]
resourceConstraint = 2

```

| Cycle | State                       | Action                                       |
|-------|-----------------------------|----------------------------------------------|
| 1     | ["A", "A", "A", "P", "P", "P"] | Remove 2 P, add 1 A → ["A", "A", "A", "A", "P"]  |
| 2     | ["A", "A", "A", "A", "P"]   | Change last A → P → ["A", "A", "A", "P", "P"]      |
| 3     | ["A", "A", "A", "P", "P"]   | Remove 2 P, add 1 A → ["A", "A", "A", "A"]        |
| 4     | ["A", "A", "A", "A"]        | Change last A → P → ["A", "A", "A", "P"]          |
| 5     | ["A", "A", "A", "P"]        | Change last A → P → ["A", "A", "P", "P"]          |
| 6     | ["A", "A", "P", "P"]        | Remove 2 P, add 1 A → ["A", "A", "A"]             |
| 7     | ["A", "A", "A"]             | Change last A → P → ["A", "A", "P"]               |
| 8     | ["A", "A", "P"]             | Change last A → P → ["A", "P", "P"]               |
| 9     | ["A", "P", "P"]             | Remove 2 P, add 1 A → ["A", "A"]                  |
| 10    | ["A", "A"]                  | Change last A → P → ["A", "P"]                    |
| 11    | ["A", "P"]                  | Change last A → P → ["P", "P"]                    |
| 12    | ["P", "P"]                  | Remove 2 P, add 1 A → ["A"]                       |
| 13    | ["A"]                       | Change last A → P → ["P"]                         |
| 14    | ["P"]                       | Halt (not enough P, no A)                         |

**Output:**  
```

14

```
(It took 14 cycles before halting.)

---

## Question 2: Phone Charging

**Description**
You want to watch videos on your phone for exactly `t` minutes.  
You have access to a set of *n* different batteries. Each battery has a given `capacity[i]` (total minutes it can provide, once fully charged) and after being depleted, it needs `recharge[i]` minutes before it can be used again.

You start with all batteries fully charged at minute 0.  
You always pick batteries in order (`0, 1, ..., n-1`), looping back to the first battery after the last.  
At any moment, if all batteries are recharging and you haven’t yet finished `t` minutes of phone use, you must return `-1` (unable to complete task).

**Return:**  
- The total number of **full batteries used** if you successfully reach `t` minutes.  
- `-1` if it is impossible.

---

## Constraints

- `1 <= n == len(capacity) == len(recharge) <= 10^4`
- `1 <= capacity[i], recharge[i], t <= 10^6`
- All values in `capacity` and `recharge` are positive integers.

---

## Example

**Input**
```

t = 16
capacity =[^2][^5][^6]
recharge =[^1][^4]

```

**Process:**

- Start at time 0.
- Use battery 0 for 2 minutes (0-2), battery 1 for 5 minutes (2-7), battery 2 for 6 minutes (7-13).
- Needed so far: 13 minutes. All three batteries must recharge before they're available again.
- Next, check if any battery is ready to use:
    - Battery 0: finished at 2, can recharge for 12 → ready at 14.
    - Battery 1: finished at 7, can recharge for 1 → ready at 8.
    - Battery 2: finished at 13, can recharge for 4 → ready at 17.
- At `time = 13` (after using battery 2), battery 1 is ready at 8 (before 13), so you can use battery 1 again.
- Use battery 1 from 13 to 18 (5 more minutes).
- Total watched minutes: 18 (passes required 16).
- The full batteries used: battery 0 (once), battery 1 (once) , battery 2 (once) = **3 in total.
- Note: You didn't use the battery 2 fully the second time **.

**Output**
```

3

```

---

## Notes

- Always use batteries in cyclic order.
- Each use must use the battery’s *full* capacity at once; partial use is not allowed (except the last one).
- If you need to use a battery but it’s still recharging, skip to the next available battery in the sequence.
- If you are ever unable to continue (no battery is available and t minutes not yet reached), return `-1`.
