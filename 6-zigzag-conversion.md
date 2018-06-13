# 6. ZigZag Conversion【medium】

### 解题思路**：**

这道题倒没有特别的方法，就按照题目意思来模拟 Z 字形即可，用一个字符串数组来存放每一行的字符串，最后进行拼接即可。

**考虑边界条件：**

当numRows等于1的时候，因为point无法增加也无法减小，所以没办法共用后面的代码，考虑到numRows等于1的时候，答案就是原字符串，所以这里直接返回s即可。

### 实现代码：

```
// 6. ZigZag Conversion
string convert(string s, int numRows) {
  if (numRows == 1) return s;
  string res;
  bool shouldIncrease = true;
  string strArr[numRows];
  int point = 0;
  for (char c : s) {
    strArr[point] += c;
    if (point == numRows - 1) {
      shouldIncrease = false;
    } else if (point == 0) {
      shouldIncrease = true;
    }
    if (shouldIncrease) {
      point++;
    } else {
      point--;
    }
  }
  for (string str: strArr) {
    res += str;
  }
  return res;
}
```

### 问题描述：

The string`"PAYPALISHIRING"`is written in a zigzag pattern on a given number of rows like this: \(you may want to display this pattern in a fixed font for better legibility\)

```
P   A   H   N
A P L S I I G
Y   I   R
```

And then read line by line:`"PAHNAPLSIIGYIR"`

Write the code that will take a string and make this conversion given a number of rows:

```
string convert(string s, int numRows);
```

**Example 1:**

```
Input: s = "PAYPALISHIRING", numRows = 3
Output: "PAHNAPLSIIGYIR"
```

**Example 2:**

```
Input: s = "PAYPALISHIRING", numRows = 4
Output: "PINALSIGYAHRPI"

Explanation:
P     I    N
A   L S  I G
Y A   H R
P     I
```



