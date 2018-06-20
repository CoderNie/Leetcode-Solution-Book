# 14. Longest Common Prefix【easy】

### 解题思路**：**

这道题从头到尾每一个字符遍历，如果出现不同或者已经不够长，则把已知的共同前缀返回即可。

**考虑边界条件：**

当输入字符串数组为空时，返回空字符串""。

### 实现代码：

```
// 14. Longest Common Prefix
string longestCommonPrefix(vector<string>& strs) {
  if (strs.size() == 0) return "";
  int length = 0;
  while (true) {
    if (strs[0].size() < length + 1) break;
    for (int i = 0; i < strs.size() - 1; i++)
      if (strs[i + 1].size() < length + 1 || strs[i][length] != strs[i + 1][length])
        return strs[0].substr(0, length);
    length++;
  }
  return strs[0].substr(0, length);
}
```

### 问题描述：

Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string`""`.

**Example 1:**

```
Input: ["flower","flow","flight"]
Output: "fl"
```

**Example 2:**

```
Input: ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
```



