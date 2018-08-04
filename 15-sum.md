# 15. 3Sum【medium】

### 解题思路**：**

**双指针法**枚举，复杂度O\(N^2\)。

首先，对数组进行排序。然后，从第一个数字 i 开始遍历，每一层遍历中有两个指针 p, q 分别指向该数字后续的数组中的头尾两端，通过判断这三个数组的和与0的关系，移动头尾指针：

**如果和大于0，尾指针前移；如果和小于0，头指针后移；如果和等于0，分别移动头尾指针。**

这里注意要考虑到数组中处理出现重复数字的情况。

**如果 i 与 i - 1重复则直接跳过该项的遍历，如果 p 重复则 p++，如果 q 重复则 q++。**

**考虑边界条件：**

当输入数组长度不足3时，返回空字符串数组。

### 实现代码：

```
// 15. 3Sum
vector<vector<int> > threeSum(vector<int>& nums) {
  vector<vector<int> > res;
  if (nums.size() < 3) return res;
  sort(nums.begin(), nums.end());
  int p, q, sum;
  for (int i = 0; i < nums.size() - 2; i++) {
    if (nums[i] > 0) 
      break;
    else if (i > 0 && nums[i] == nums[i - 1]) 
      continue;
    p = i + 1;
    q = nums.size() - 1;
    while (p < q) {
      sum = nums[i] + nums[p] + nums[q];
      if (sum == 0) {
        res.push_back({nums[i], nums[p], nums[q]});
        while (nums[p] == nums[p + 1] && p < q)
          p++;
        p++;
        while (nums[q] == nums[q - 1] && p < q)
          q--;
        q--;
      } else if (sum > 0) {
        while (nums[q] == nums[q - 1] && p < q)
          q--;
        q--;
      } else {
        while (nums[p] == nums[p + 1] && p < q)
          p++;
        p++;
      }
    }
  }
  return res;
}
```

### 问题描述：

Given an array`nums`of_n\_integers, are there elements a_, _b_, _c in_`nums`_such that a_+_b_+_c_= 0? Find all unique triplets in the array which gives the sum of zero.

**Note:**

The solution set must not contain duplicate triplets.

**Example:**

```
Given array nums = [-1, 0, 1, 2, -1, -4],

A solution set is:
[
  [-1, 0, 1],
  [-1, -1, 2]
]
```



