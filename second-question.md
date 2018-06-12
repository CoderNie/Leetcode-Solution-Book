# 1. Two Sum 【easy】

### 解题思路**：**

#### **暴力解法  **O\(N^2\)：

嵌套两层循环：第一层：i 从 0 到 n - 2；第二层：j 从 i + 1 到 n - 1；判断 nums\[i\] + nums\[j\] == target ，如果成立则是正确答案

#### **map解法  **O\(N\*logN\)**：**

从 0 到 n - 1 依次遍历，利用map存放**每一个数值的下标**，在map中寻找是否有使（nums\[i\] + x == target）成立的x的存在，如果存在则返回i和它的下标（即myMap\[ target - nums\[i\] \]\)。

复杂度分析：因为只遍历了一次数组，map每次的查询的时间复杂度为O\(logN\)所以整体复杂度为O\(N\*logN\)、如果这里使用hash\_map可以将查询复杂度降低到O\(1\)，从而使得整体复杂度为O\(N\)，但是hash\_map不是标准的C++库，所以这里没有使用。

#### **考虑边界条件：**

因为这道题题目说明了有且只有一个解，所以不需要考虑边界条件。

### 实现代码：

```
// 1. Two Sum
vector<int> twoSum(vector<int>& nums, int target) {
  map<int, int> myMap;
  vector<int> result;
  for (int i = 0; i < nums.size(); i++) {
    if (myMap.find(target - nums[i]) == myMap.end()) {
      myMap[nums[i]] = i;
    } else {
      result = {myMap[target - nums[i]], i};
      break;
    }
  }
  return result;
}
```

### 问题描述：

Given an array of integers, return **indices **of the two numbers such that they add up to a specific target.

You may assume that each input would have \_**exactly **\_one solution, and you may not use the\_same\_element twice.

**Example:**

```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```



