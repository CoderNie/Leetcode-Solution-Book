# 2. Add Two Numbers【medium】

### 解题思路**：**



### 实现代码：

```
// 7. Reverse Integer
int reverse(int x) {
  long result = 0, longX = abs((long)x);
  while (longX > 0) {
    result = result * 10 + longX % 10;
    longX /= 10;
  }
  result = (x > 0) ? result : -result;
  if (result > INT32_MAX || result < INT32_MIN) {
    return 0;
  } else {
    return (int)result;
  }
}
```

### 问题描述：

Given a 32-bit signed integer, reverse digits of an integer.

**Example 1:**

```
Input: 123
Output: 321
```

**Example 2:**

```
Input: -123
Output: -321
```

**Example 3:**

```
Input: 120
Output: 21
```

**Note:**  
Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: \[−2^31,  2^31 − 1\]. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.

