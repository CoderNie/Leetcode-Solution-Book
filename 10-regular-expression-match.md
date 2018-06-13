# 10. Regular Expression Matching【hard】

### 解题思路**：**

动态规划思想解答这道题：

用 dp\[i\]\[j\] 表示 s 的前 i 个字符组成的字符串和 p 的 前 j 个字符组成的字符串是否匹配。

转移方程：

当 p\[j - 1\] == '\*' 时：

当 p\[j - 1\] != '\*' 时，

### 实现代码：

```
// 10. Regular Expression Matching
bool isMatch(string s, string p) {
  int n = s.size();
  int m = p.size();
  // initial
  bool dp[n + 1][m + 1];
  for (int i = 0; i < n + 1; i++) {
    for (int j = 0; j < m + 1; j++) {
      dp[i][j] = false;
    }
  }
  // start
  dp[0][0] = true;
  for (int i = 1; i < n + 1; i++) {
    dp[i][0] = false;
  }
  for (int j = 1; j < m + 1; j++) {
    if (j % 2 == 0) {
      dp[0][j] = dp[0][j - 2] && p[j - 1] == '*';
    } else {
      dp[0][j] = false;
    }
  }
  // trans
  bool compare;
  for (int i = 1; i < n + 1; i++) {
    for (int j = 1; j < m + 1; j++) {
      if (p[j - 1] != '*') {
        dp[i][j] = dp[i - 1][j - 1] && (s[i - 1] == p[j - 1] || p[j - 1] == '.');
      } else {
        compare = (s[i - 1] == p[j - 2] || p[j - 2] == '.');
        dp[i][j] = dp[i][j - 2] || (dp[i - 1][j - 2] && compare) || (dp[i - 1][j] && compare);
      }
    }
  }
  return dp[n][m];
}
```

### 问题描述：

Given an input string \(`s`\) and a pattern \(`p`\), implement regular expression matching with support for`'.'`and`'*'`.

```
'.' Matches any single character.
'*' Matches zero or more of the preceding element.
```

The matching should cover the**entire**input string \(not partial\).

**Note:**

* `s`could be empty and contains only lowercase letters`a-z`
* `p`could be empty and contains only lowercase letters`a-z`, and characters like `.` or `*`.

**Example 1:**

```
Input:
s = "aa"
p = "a"
Output: false
Explanation: "a" does not match the entire string "aa".
```

**Example 2:**

```
Input:
s = "aa"
p = "a*"
Output: true
Explanation: '*' means zero or more of the precedeng element, 'a'. Therefore, by repeating 'a' once, it becomes "aa".
```

**Example 3:**

```
Input:
s = "ab"
p = ".*"
Output: true
Explanation: ".*" means "zero or more (*) of any character (.)".
```

**Example 4:**

```
Input:
s = "aab"
p = "c*a*b"
Output: true
Explanation: c can be repeated 0 times, a can be repeated 1 time. Therefore it matches "aab".
```

**Example 5:**

```
Input:
s = "mississippi"
p = "mis*is*p*."
Output: false
```



