# 2. Add Two Numbers【medium】

### 解题思路**：**

从左到右遍历链表，依次相加，每一个位置生成一个新的结点即可。

时间复杂度：O\( max\( len\(l1\), len\(l2\) \) \)

**考虑边界条件：**

1.进位的的处理：carry表示进位，当最后一位还有进位时，即使 l1 和 l2 均为NULL的情况下，还需要生成一个新的结点，所以while的条件中加入了 carry != 0 判断项。

2.返回头结点：当头结点为NULL的时候记录头结点，并且让p等于头结点；后续情况让 p-&gt;next 等于新的结点，并让 p 指向 p-&gt;next。

### 实现代码：

```
// 2. Add Two Numbers
ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
    ListNode *front = new ListNode(0), *p = front;
    int sum = 0, carry = 0;
    while (l1 != NULL || l2 != NULL || carry != 0) {
        sum = carry + (l1 != NULL ? l1->val : 0) + (l2 != NULL ? l2->val : 0);
        carry = sum / 10;
        ListNode *newNode = new ListNode(sum % 10);
        p->next = newNode;
        p = p->next;
        if (l1 != NULL) l1 = l1->next;
        if (l2 != NULL) l2 = l2->next;
    }
    return front->next;
}
```

### 问题描述：

You are given two **non-empty **linked lists representing two non-negative integers. The digits are stored in**reverse order**and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

**Example**

```
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
Explanation: 342 + 465 = 807.
```



