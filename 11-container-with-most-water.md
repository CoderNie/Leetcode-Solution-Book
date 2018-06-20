# 11. Container With Most Water【medium】

### 解题思路**：**

这道题可以考虑暴力枚举的方式，复杂度应该是O\(N^2\)，嵌套循环即可实现，下面重点讲复杂度只有O\(N\)的**头尾标记法**。

考虑到：

**容器的容量 = 两端中较矮的板子长度（L） \* 两端的距离（d）**

在数组两端设置头尾标记，以头尾标记为容器的两端，假设头标记对应的板子长度比较短，那么现在 容器的容量 = 头标记板子 \* 头尾标记的距离。那么以头标记为一端的所有容器的容量必然小于当前容器，因为其他以头标记为一端的容器的**L**一定小于或等于当前容器，而距离**d**一定小于当前容器。所以这些容器都可以无需遍历，因此让头标记向尾部移动一个单位；假设尾标记对应的板子长度比较短，则以此类推，让尾标记向头部移动一个单位，直至头尾标记相遇则停止寻找。

### 实现代码：

```
// 11. Container With Most Water
int maxArea(vector<int>& height) {
  int res = 0, i = 0, j = height.size() - 1;
  while (i != j) {
    res = max(res, (j - i) * min(height[i], height[j]));
    if (height[i] > height[j]) {
      j--;
    } else {
      i++;
    }
  }
  return res;
}
```

### 问题描述：

Givennnon-negative integersa1,a2, ...,an, where each represents a point at coordinate \(i,ai\).nvertical lines are drawn such that the two endpoints of lineiis at \(i,ai\) and \(i, 0\). Find two lines, which together with x-axis forms a container, such that the container contains the most water.

Note: You may not slant the container andnis at least 2.

