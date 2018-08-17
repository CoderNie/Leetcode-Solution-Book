# 28. Implement strStr\(\)

# 解题思路**：**

字符串匹配算法，选择比较多，最容易的就是**暴力匹配**，高阶一点可以使用**KMP**，这里简单起见，采用暴力解法，嘻嘻。

### 实现代码：

```
// 28. Implement strStr()
int strStr(string haystack, string needle) {
  if (needle.size() == 0) return 0;
  int hLen = haystack.size(), nLen = needle.size();
  for (int i = 0; i < hLen; i++) {
    if (hLen - i < nLen) {
      return -1;
    } else {
      if (haystack.substr(i, nLen).compare(needle) == 0) {
        return i;
      }
    }
  }
  return -1;
}
```

### 问题描述：

Implement strStr\(\).

Return the index of the first occurrence of needle in haystack, or**-1**if needle is not part of haystack.

**Example 1:**

```
Input: haystack = "hello", needle = "ll"
Output: 2
```

**Example 2:**

```
Input: haystack = "aaaaa", needle = "bba"
Output: -1
```

**Clarification:**

What should we return when`needle`is an empty string? This is a great question to ask during an interview.

For the purpose of this problem, we will return 0 when`needle`is an empty string. This is consistent to C's strstr\(\) and Java's indexOf\(\).

