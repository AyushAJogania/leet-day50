# leet-day50

# Problem Description

You are given a string `s` and a dictionary of words `dictionary`. The goal is to break the string `s` into one or more non-overlapping substrings such that each substring is present in the dictionary. The objective is to minimize the number of extra characters left over in the string `s` after the optimal breaking.

## Example

**Input:**

```
s = "leetscode"
dictionary = ["leet", "code", "leetcode"]
```

**Output:**

```
1
```

**Explanation:**

One possible way to break `s` optimally is into two substrings: "leet" from index 0 to 3 and "code" from index 5 to 8. There is only 1 unused character (at index 4), so the output is 1.

## Constraints

- 1 <= `s.length` <= 50
- 1 <= `dictionary.length` <= 50
- 1 <= `dictionary[i].length` <= 50
- `dictionary` contains distinct words.
- Both `dictionary[i]` and `s` consist of only lowercase English letters.

# Approach

We can use dynamic programming to solve this problem efficiently. We define `DP[i]` as the minimum number of extra characters left over if we break up `s[0:i]` optimally.

1. Initialize a map `m` to store the dictionary words and their counts.
2. Define a recursive function `c(i, s, dp)` to calculate the minimum extra characters for the substring `s[i:]`. If `i` is greater than or equal to the length of `s`, return 0.
3. If `dp[i]` is not -1 (indicating it has already been calculated), return `dp[i]`.
4. Initialize `ans` to `INT_MAX`.
5. Update `ans` as the minimum of:
   - 1 + `c(i + 1, s, dp)` (indicating we don't use the current character)
   - For each substring `k` starting from `s[i:]` and ending at the end of `s`, if `k` is in the dictionary (`m[k]` is nonzero), update `ans` as the minimum of `ans` and `c(j + 1, s, dp)` where `j` is the index of the end of substring `k`.
6. Set `dp[i]` to `ans` and return it.

Finally, call the `c` function with `i` initially set to 0 to find the minimum number of extra characters left over for the entire string `s`.

# Complexity Analysis

- Time Complexity: O(N^2) where N is the length of the string `s`. In the worst case, we may have to consider all possible substrings.
- Space Complexity: O(N) for the `dp` array and O(M) for the `m` map, where M is the total number of characters in the dictionary words.

# Summary

This problem can be efficiently solved using dynamic programming with memoization to find the minimum number of extra characters left over when breaking up a string into dictionary words optimally.
