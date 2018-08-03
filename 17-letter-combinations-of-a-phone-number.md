# 17. Letter Combinations of a Phone Numbe

# 解题思路**：**

经典的排列问题，直接用回溯法解决。

下面的解法是使用循环实现非递归的回溯法。linshi作为中间变量，每一个数字按下之后的结果。

### 实现代码：

```
// 17. Letter Combinations of a Phone Number
vector<string> letterCombinations(string digits) {
  if (digits.size() == 0) return {};
  map<int, string> digitalMap;
  digitalMap[2] = "abc";
  digitalMap[3] = "def";
  digitalMap[4] = "ghi";
  digitalMap[5] = "jkl";
  digitalMap[6] = "mno";
  digitalMap[7] = "pqrs";
  digitalMap[8] = "tuv";
  digitalMap[9] = "wxyz";
  vector<string> linshi;
  vector<string> res = {""};
  for (int i = 0; i < digits.size(); i++) {
    string tails = digitalMap[digits[i] - 48];
    for (int j = 0; j < res.size(); j++) {
      for (int n = 0; n < tails.size(); n++) {
        linshi.push_back(res[j] + tails[n]);
      }
    }
    res = linshi;
    linshi = {};
  }
  return res;
}
```

### 问题描述：

Given a string containing digits from`2-9`inclusive, return all possible letter combinations that the number could represent.

A mapping of digit to letters \(just like on the telephone buttons\) is given below. Note that 1 does not map to any letters.

![](http://upload.wikimedia.org/wikipedia/commons/thumb/7/73/Telephone-keypad2.svg/200px-Telephone-keypad2.svg.png)

**Example:**

```
Input: "23"

Output: ["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].
```

**Note:**

Although the above answer is in lexicographical order, your answer could be in any order you want.

