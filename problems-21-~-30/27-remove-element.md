# 27.Remove Element

# 解题思路**：**

按照题意，把数组中不重复出现的数字保存在数组前端即可。

### 实现代码：

```
// 26. Remove Duplicates from Sorted Array
int removeDuplicates(vector<int>& nums) {
  if (nums.size() == 0) return 0;
  int j = 1;
  for (int i = 1; i < nums.size(); i++) {
    if (nums[i] != nums[i - 1]) {
      nums[j++] = nums[i];
    }
  } 
  return j;      
}
```

### 问题描述：

Note that the input array is passed in by **reference**, which means modification to the input array will be known to the caller as well. Internally you can think of this:

```
// nums is passed in by reference. (i.e., without making a copy)
int len = removeDuplicates(nums);

// any modification to nums in your function would be known by the caller.
// using the length returned by your function, it prints the first len elements.
for (int i = 0; i < len; i++) {
    print(nums[i]);
}
```



