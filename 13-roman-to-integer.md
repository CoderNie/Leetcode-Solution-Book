# 13. Roman To Integer【easy】

### 解题思路**：**

这道题和上一题一样，直接按照转换规则进行转换即可，对每一位进行遍历，注意考虑4和9的特殊情况即可。

### 实现代码：

```
// 13. Roman To Integer
int romanToInt (string s) {
  int res = 0;
  for (int i = 0; i < s.size(); i++) {
    if (s[i] == 'I') {
      res += 1;
    } else if (s[i] == 'V') {
      res += 5;
      if (i - 1 >= 0 && s[i - 1] == 'I') {
        res -= 2;
      }
    } else if (s[i] == 'X') {
      res += 10;
      if (i - 1 >= 0 && s[i - 1] == 'I') {
        res -= 2;
      }
    } else if (s[i] == 'L') {
      res += 50;
      if (i - 1 >= 0 && s[i - 1] == 'X') {
        res -= 20;
      }
    } else if (s[i] == 'C') {
      res += 100;
      if (i - 1 >= 0 && s[i - 1] == 'X') {
        res -= 20;
      }
    } else if (s[i] == 'D') {
      res += 500;
      if (i - 1 >= 0 && s[i - 1] == 'C') {
        res -= 200;
      }
    } else if (s[i] == 'M') {
      res += 1000;
      if (i - 1 >= 0 && s[i - 1] == 'C') {
        res -= 200;
      }
    }
  }
  return res;
}
```

### 问题描述：

Roman numerals are represented by seven different symbols: `I`,`V`,`X`,`L`,`C`,`D`and`M`.

```
Symbol        Value
I             1
V             5
X             10
L             50
C             100
D             500
M             1000
```

For example, two is written as`II` in Roman numeral, just two one's added together. Twelve is written as,`XII`, which is simply`X`+`II`. The number twenty seven is written as`XXVII`, which is`XX`+`V`+`II`.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not`IIII`. Instead, the number four is written as`IV`. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as`IX`. There are six instances where subtraction is used:

* `I`can be placed before`V`\(5\) and`X`\(10\) to make 4 and 9. 
* `X`can be placed before`L`\(50\) and`C`\(100\) to make 40 and 90. 
* `C`can be placed before`D`\(500\) and`M`\(1000\) to make 400 and 900.

Given a roman numeral, convert it to an integer. Input is guaranteed to be within the range from 1 to 3999.

**Example 1:**

```
Input: "III"
Output: 3
```

**Example 2:**

```
Input: "IV"
Output: 4
```

**Example 3:**

```
Input: "IX"
Output: 9
```

**Example 4:**

```
Input: "LVIII"
Output: 58
Explanation: C = 100, L = 50, XXX = 30 and III = 3.
```

**Example 5:**

```
Input: "MCMXCIV"
Output: 1994
Explanation: M = 1000, CM = 900, XC = 90 and IV = 4.
```



