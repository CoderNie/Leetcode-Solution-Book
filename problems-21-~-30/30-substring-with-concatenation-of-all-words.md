# 29. Devide Two Integers

# 解题思路**：**

这道题如果用减法去实现会造成时间复杂度过高，从而导致时间溢出，所以这里采用位运算法，从 2 的 31 次方开始除，一直除到 2 的 0 次方，为了防止内存溢出，我们把结果和中间变量保存在 long 类型中的。

### 实现代码：

```
// 29. Divide Two Integers
int divide(int dividend, int divisor) {
  if (dividend > INT32_MAX || dividend < INT32_MIN || divisor > INT32_MAX || divisor < INT32_MIN) return INT32_MAX;
  long son = abs((long)divisor), father = abs((long)dividend), res = 0, base = 1, sum = 0;
  for (int i = 31; i >= 0; i--) {
    if (sum + (son << i) <= father) {
      sum += son << i;
      res += base << i;
    }
  }
  if ((dividend >= 0 && divisor > 0) || (dividend < 0 && divisor < 0)) {
    return (res > INT32_MAX) ? INT32_MAX : res;
  } else {
    return (-res < INT32_MIN) ? INT32_MAX : -res;
  }
}
```

### 问题描述：

Given two integers`dividend`and`divisor`, divide two integers without using multiplication, division and mod operator.

Return the quotient after dividing`dividend`by`divisor`.

The integer division should truncate toward zero.

**Example 1:**

```
Input: dividend = 10, divisor = 3
Output: 3
```

**Example 2:**

```
Input: dividend = 7, divisor = -3
Output: -2
```



