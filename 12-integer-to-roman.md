# 12. Integer To Roman【medium】

### 解题思路**：**

这道题没有特别多技巧，直接按照转换规则进行转换即可，对每一位进行遍历，注意考虑4和9的特殊情况即可。

在查看Leetcode讨论区的时候还看到了一种脑洞大开的“全部映射法”，这里贴上来给大家欣赏一下，也开拓了一下思路，这种方法告诉我们在情况不多的时候，可以考虑一下这种思路，代码更为简洁。

### 实现代码：

```
// 12. Integer to Roman
string intToRoman(int num) {
  map<int, char> romanMap;
  romanMap[1] = 'I';
  romanMap[5] = 'V';
  romanMap[10] = 'X';
  romanMap[50] = 'L';
  romanMap[100] = 'C';
  romanMap[500] = 'D';
  romanMap[1000] = 'M';
  string res;
  for (int i = 3; i >= 0; i--) {
    int fold = pow(10, i);
    if (num / fold == 9) {
      res += romanMap[fold];
      res += romanMap[fold * 10];
    } else if (num / fold == 4) {
      res += romanMap[fold];
      res += romanMap[fold * 5];
    } else if (num / fold > 0) {
      if (num / fold >= 5) {
        res += romanMap[fold * 5];
        num -= 5 * fold;
      }
      for (int i = 0; i < num / fold; i++) {
        res += romanMap[fold];
      }
    }
    num %= fold;
  }
  return res;
}
// 脑洞大开的全部映射法
string intToRoman(int num) {
  string M[] = {"", "M", "MM", "MMM"};
  string C[] = {"", "C", "CC", "CCC", "CD", "D", "DC", "DCC", "DCCC", "CM"};
  string X[] = {"", "X", "XX", "XXX", "XL", "L", "LX", "LXX", "LXXX", "XC"};
  string I[] = {"", "I", "II", "III", "IV", "V", "VI", "VII", "VIII", "IX"};
  return M[num/1000] + C[(num%1000)/100] + X[(num%100)/10] + I[num%10];
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

Given an integer, convert it to a roman numeral. Input is guaranteed to be within the range from 1 to 3999.

**Example 1:**

```
Input: 3
Output: "III"
```

**Example 2:**

```
Input: 4
Output: "IV"
```

**Example 3:**

```
Input: 9
Output: "IX"
```

**Example 4:**

```
Input: 58
Output: "LVIII"
Explanation: C = 100, L = 50, XXX = 30 and III = 3.
```

**Example 5:**

```
Input: 1994
Output: "MCMXCIV"
Explanation: M = 1000, CM = 900, XC = 90 and IV = 4.
```



