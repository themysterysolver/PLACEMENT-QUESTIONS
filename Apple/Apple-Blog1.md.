# Apple SDET Questions

## Overview
- This document contains two representative coding problems that have appeared in Apple’s SDET (Software Development Engineer in Test) Online Assesement test in the on-campus round of Anna Univeristy on September 2025.
- Both problems require solid string/array manipulation skills and the ability to translate English rules into deterministic code.
- In addition to coding questions, there were 9 more MCQs which mainly focused on software and quality testing.

## Types of questions asked, preparatory material and resources
- **Topics**: String Manipulation, greedy & DP on arrays, lexicographic ordering.
- **Resources**:
  - HERE ARE SOME OF THE SIMILAR QUESTIONS YOU CAN SOLVE
  - [Longest Increasing Subsequence](https://leetcode.com/problems/longest-increasing-subsequence/description/).
  - [Remove comments](https://leetcode.com/problems/remove-comments/description/)
  - For the MCQs refer to [https://www.geeksforgeeks.org/software-testing/software-testing-basics/].
  - Additionally, refer to class notes or textbook on software testing and Quality assurance as these questions were fairly straightforward.

---

### Question 1 – Custom CSV-style Field Splitter

**Problem Statement**
You are given a single string that encodes zero or more fields separated by commas.
Split the string into a list of fields, obeying **all** of the following rules:

1. A comma (`,`) is the delimiter between fields.
2. A field may be surrounded by balanced single quotes `'...'` **or** balanced double quotes `"..."`.
3. If a field is quoted, the outermost quotes are removed **before** returning the field.
4. Any comma that appears **inside** a quoted field is **kept** as part of the data.
5. Two consecutive quotes inside a quoted field are treated as a single escaped quote (`''` → `'` or `""` → `"`).
6. Unquoted fields are taken exactly as-is (no trimming, no quote removal).

**Input Format**
Single method parameter: `String inputString` (length ≤ 10⁵).
Examples:
- `"abc,123,'H,ello',\"w\"\"o,rld\""`
- `"  noquotes , 'It''s ok' , \"\" , last"`

**Output Format**
Return `List<String>` containing the parsed fields in original order.
Examples:
- `["abc", "123", "H,ello", "w\"o,rld"]`
- `["  noquotes ", "It's ok", "", " last"]`

**Approach**
1. One linear scan with a state machine:
   - `quote = 0` → unquoted state
   - `quote = '\''` → inside single quotes
   - `quote = '\"'` → inside double quotes
2. Accumulate characters into a `StringBuilder`.
3. On delimiter comma (outside any quote) push the current builder content into the result list.
4. Handle doubled quotes for escape.
5. Time complexity: O(n), space: O(n).

**Java Code**
```java
import java.util.*;

public class FieldSplitter {

    public static List<String> splitFields(String input) {
        List<String> res = new ArrayList<>();
        if (input == null || input.isEmpty()) return res;

        int n = input.length();
        int i = 0;
        while (i < n) {
            // skip leading whitespace before each field
            while (i < n && Character.isWhitespace(input.charAt(i))) i++;
            if (i == n) break;

            char quote = 0;
            if (input.charAt(i) == '\'' || input.charAt(i) == '\"') {
                quote = input.charAt(i);
                i++;  // move past opening quote
            }

            StringBuilder sb = new StringBuilder();
            while (i < n) {
                char c = input.charAt(i);
                if (quote != 0) {  // inside quotes
                    if (c == quote) {
                        if (i + 1 < n && input.charAt(i + 1) == quote) { // escaped quote
                            sb.append(quote);
                            i += 2;
                        } else { // closing quote
                            i++;
                            break;
                        }
                    } else {
                        sb.append(c);
                        i++;
                    }
                } else { // unquoted
                    if (c == ',') break;
                    sb.append(c);
                    i++;
                }
            }
            res.add(sb.toString());

            // skip delimiter comma
            if (i < n && input.charAt(i) == ',') i++;
        }
        return res;
    }
}
```

### Question 2 – Maximum Lexicographic Tour with Increasing Distance

**Problem Statement**  
You are given two arrays of equal length:  
- `cities[i]` – unique city names (case-sensitive strings)  
- `distances[i]` – the distance (km) of that city from a fixed western starting point  

You may start from **any** city.  
From the current city you may travel to another city **only if**  
1. the next city’s name is **strictly greater** lexicographically, and  
2. the next city’s distance is **strictly larger** than the current city’s distance.

Find the **maximum number of cities** that can be visited in one such sequence.

**Input Format**  
- Function signature: `int maxCitiesVisitable(String[] cities, int[] distances)`  
- `1 ≤ cities.length ≤ 100 000`  
- City names contain only letters (upper- or lower-case).  
- All distances are positive integers; no two cities share the same distance.

**Output Format**  
Return a single integer – the length of the longest valid sequence.

**Examples**
cities    = ["Z", "A", "B", "C", "D", "E"]
distances = [10,  5,  6,  7,  8,  9]
output    = 5   // (A,5) → (B,6) → (C,7) → (D,8) → (E,9)


**Approach**
1. Combine `(city, distance)` pairs and sort primarily by city name lexicographically.  
2. After sorting, the problem reduces to finding the **Longest Increasing Subsequence (LIS)** on the distance array.  
3. Use patience-sorting LIS with binary search to achieve:  
   - Time complexity: **O(n log n)**  
   - Space complexity: **O(n)**

**Java Code**
```java
import java.util.*;

public class CityTravel {

    /**
     * Returns the maximum number of cities that can be visited while
     * respecting lexicographic order and strictly increasing distances.
     */
    public static int maxCitiesVisitable(String[] cities, int[] distances) {
        if (cities == null || distances == null || cities.length != distances.length)
            return 0;

        int n = cities.length;
        if (n == 0) return 0;

        // Pair city with distance
        record CityDist(String city, int dist) {}
        CityDist[] list = new CityDist[n];
        for (int i = 0; i < n; i++) list[i] = new CityDist(cities[i], distances[i]);

        // Sort lexicographically by city name
        Arrays.sort(list, Comparator.comparing((CityDist cd) -> cd.city)
                                    .thenComparingInt(cd -> cd.dist));

        // Longest Increasing Subsequence on distances
        int[] tails = new int[n];
        int len = 0;
        for (CityDist cd : list) {
            int d = cd.dist;
            int idx = Arrays.binarySearch(tails, 0, len, d);
            if (idx < 0) idx = -(idx + 1);
            tails[idx] = d;
            if (idx == len) len++;
        }
        return len;
    }
}
```

---
## Ending Notes
I wish everyone who is on this journey best of luck!
Sinerely, 
Abhinavh
