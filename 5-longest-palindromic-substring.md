# 5. Longest Palindromic Substring【medium】

### 解题思路**：**

#### 暴力解法 O\(N^3\)：

字符串有 n\(n-1\)/2 个子串，对每个子串进行检测，看其是否是回文子串。因此复杂度为 O\(N^3\)。

#### 从字符串中间开始扩展 O\(N^2\)：

把字符串的每个点分别当成回文子串的中间点，开始往两端扩展，不断检测，直到两端不相等为止。因此复杂度为 O\(N^2\)。

#### 动态规划 O\(N^2\)：

用 dp\[i\]\[j\] 表示下标为 i 开头 j 结尾的子串是否是回文子串。

转移方程：dp\[i\]\[j\] = \(dp\[i + 1\]\[j - 1\] && s\[i\] == s\[j\]\) 【含义：当且仅当子串首尾两端相等，且去除首尾两端依旧是回文串时，该子串才会是回文串】

初始条件：对于每个长度为1的子串 dp\[i\]\[i\] 都为回文串；对于每个长度为2的子串 dp\[i\]\[i + 1\]，当其首尾两端相等时，其为回文串，否则不是。

### 实现代码：

```
// 5. Longest Palindromic Substring (动态规划)
string longestPalindrome(string s) {
  int length = s.size();
  if (length == 0) return s;
  int resI = 0, resJ = 0;
  bool dp[length + 1][length + 1];
  for (int i = 0; i <= length; i++)
    dp[i][i] = true;
  for (int i = 0; i < length; i++) {
    if (s[i] == s[i + 1]) {
      dp[i][i + 1] = true;
      if (resJ - resI < 1) {
        resI = i;
        resJ = i + 1;
      }
    } else {
      dp[i][i + 1] = false;
    }
  }
  for (int gap = 2; gap < length; gap++) {
    for (int i = 0; i + gap < length; i++) {
      int j = i + gap;
      if (s[i] == s[j] && dp[i + 1][j - 1]) {
        dp[i][j] = true;
        if (resJ - resI < j - i) {
          resI = i;
          resJ = j;
        }
      } else {
        dp[i][j] = false;
      }
    }
  }
  return s.substr(resI, resJ - resI + 1);
}
```

### 问题描述：

Given a string **s**, find the longest palindromic substring in **s**. You may assume that the maximum length of **s **is 1000.

**Example 1:**

```
Input: "babad"
Output: "bab"
Note: "aba" is also a valid answer.
```

**Example 2:**

```
Input: "cbbd"
Output: "bb"
```



