# Tekion

**Year:** 2025
**Type:** Placement

---

## Online Assessment Overview  
- It was a test for `1.5Hrs` consisting of 2 coding questions and 20 MCQs.
- *DSA questions* were of **easy** and **medium** level difficulty and *MCQs* questions were majorly on Java, Javascript, React, OS, Code and outputs etc...

---

## Question 1

** Problem Statement **

You are given the following data:

- A non-decreasing array of **timestamps**, for example:  
  `[10, 20, 30, 40]` or `[1, 2, 3, 4]`
- An array of **user IDs** (alphanumeric strings) corresponding to each timestamp:  
  `["A", "B", "A", "B"]`
- An array of **actions** (either `"login"` or `"logout"`), corresponding to each timestamp and user:  
  `["login", "login", "login", "logout"]`
- An integer `m` representing the **maximum allowed concurrent logins per user**.

Each user can log in and log out multiple times. The number of concurrent logins for a user increases by one with each `"login"` and decreases by one with each `"logout"` (never goes below zero). If a user's concurrent logins ever exceed `m` after any action, they are considered to have **violated** the concurrent login limit.

Your task is to **return all user IDs who violate the concurrent login limit at any point**, sorted alphabetically.

## Constraints

- `timestamps`, `userIds`, and `actions` are of equal length.
- Each entry in `actions` is either `"login"` or `"logout"`.
- `m` is a positive integer.
- User IDs are alphanumeric.

## Example

### Input

```

timestamps =[^10]
userIds =    ["A", "B", "A", "B"]
actions =    ["login", "login", "login", "logout"]
m = 1

```

### Table

| Timestamp | User | Action | Concurrent logins (A/B) | Violated?      |
|-----------|------|--------|-------------------------|----------------|
| 10        |  A   | login  | 1/0                     | No             |
| 20        |  B   | login  | 1/1                     | No             |
| 20        |  A   | login  | 2/1                     | Yes (A)        |
| 40        |  B   | logout | 2/0                     | -              |

### Output

```

["A"]

```

## Approach

- Track each user's current concurrent login count in a map.
- For each action, update the user's login count based on the action type. (+1 if login, -1 if logout).
- If the user's login count exceeds `m` after any action, add them to the violation list.
- Return all violating user IDs, sorted alphabetically.
