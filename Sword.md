## Table of Contents
|序号|题目|难度|标签|LeetCode|
|:-:|:-|:-:|:-|:-:|
|1|[]()||||
|2|[]()||||
|3|[]()||||
|4|[二维数组中的查找](#4-二维数组中的查找)|Easy|`数组`|240|
|5|[]()||||
|6|[]()||||
|7|[]()||||
|8|[]()||||
|9|[用两个栈实现队列](#9-用两个栈实现队列)|Easy|`栈` `队列`|~|
|10|[]()||||
|11|[]()||||
|12|[]()||||
|13|[]()||||
|14|[]()||||
|15|[]()||||
|16|[]()||||
|17|[]()||||
|18|[]()||||
|19|[]()||||
|20|[]()||||
|21|[]()||||
|22|[]()||||
|23|[]()||||
|24|[反转链表](#24-反转链表)|Easy|`链表`|206|
|25|[]()||||
|26|[]()||||
|27|[]()||||
|28|[]()||||
|29|[顺时针打印矩阵](#29-顺时针打印矩阵)|Easy|`数组`|54|
|30|[包含min函数的栈](#30-包含min函数的栈)|Easy|`栈`|155|
|31|[]()||||
|32|[]()||||
|33|[]()||||
|34|[]()||||
|35|[]()||||
|36|[]()||||
|37|[]()||||
|38|[]()||||
|39|[]()||||
|40|[]()||||
|41|[数据流中的中位数](#41-数据流中的中位数)|Hard|`堆` `排序`|295|
|42|[]()||||
|43|[]()||||
|44|[]()||||
|45|[]()||||
|46|[]()||||
|47|[]()||||
|48|[]()||||
|49|[]()||||
|50|[]()||||
|51|[数组中的逆序对](#51-数组中的逆序对)|Hard|`归并算法` `逆序对`|~|
|52|[两个链表的第一个公共节点](#52-两个链表的第一个公共节点)|Easy|`链表`|160|
|53|[]()||||
|54|[]()||||
|55|[]()||||
|56|[]()||||
|57|[]()||||
|58|[]()||||
|59|[]()||||
|60|[]()||||
|61|[]()||||
|62|[]()||||
|63|[]()||||
|64|[]()||||
|65|[]()||||
|66|[]()||||
|67|[]()||||
|68|[]()||||
|69|[]()||||
|70|[]()||||
|71|[]()||||
|72|[]()||||
|73|[]()||||
|74|[]()||||
|75|[]()||||
|76|[]()||||
|77|[]()||||
|78|[]()||||
|79|[]()||||
|80|[]()||||


### 1.
### 2.
### 3.

### 4. 二维数组中的查找
🥉在一个 n * m 的二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。
```
现有矩阵matrix如下:
[
  [1,   4,  7, 11, 15],
  [2,   5,  8, 12, 19],
  [3,   6,  9, 16, 22],
  [10, 13, 14, 17, 24],
  [18, 21, 23, 26, 30]
]
给定 target = 5，返回 true。
给定 target = 20，返回 false。
```
---

标签: `数组`<br>
时间复杂度:`O(N+M)` 空间复杂度:`O(1)`
```c++
class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
        if (matrix.empty()) return false;
        int i = 0, j = matrix[0].size() - 1;
        //🪁从矩阵的右上角开始寻找,target等于当前值时返回true,否则继续(小于时往左,大于时往下)
        while (i < matrix.size() && j >= 0) {
            if (target == matrix[i][j]) return true;
            target > matrix[i][j] ? i++ : j--;
        }
        return false;
    }
};
```

### 5.
### 6.
### 7.
### 8.

### 9. 用两个栈实现队列
🥉用两个栈实现一个队列。队列的声明如下，请实现它的两个函数 appendTail 和 deleteHead ，分别完成在队列尾部插入整数和在队列头部删除整数的功能。(若队列中没有元素，deleteHead 操作返回 -1 )
```
输入：["CQueue","appendTail","deleteHead","deleteHead"] [[],[3],[],[]]
输出：[null,null,3,-1]
```
---

标签: `栈` `队列`<br>
时间复杂度:`O(1)` 空间复杂度:`O(N)`
```c++
class CQueue {
public:
    CQueue() {}
    
    void appendTail(int value) {
        //🪁使用双栈实现数据的逆序存放,从而栈顶为队列首部元素
        stack<int> temp;
        while (!data.empty()) {
            temp.push(data.top());
            data.pop();
        }
        data.push(value);
        while (!temp.empty()) {
            data.push(temp.top());
            temp.pop();
        }
    }
    
    int deleteHead() {
        if (data.empty()) return -1;
        int top = data.top();
        data.pop();
        return top;
    }

private:
    stack<int> data;
};
```

### 10.

### 11.
### 12.
### 13.
### 14.
### 15.
### 16.
### 17.
### 18.
### 19.
### 20.

### 21.
### 22.
### 23.

### 24. 反转链表
🥉定义一个函数，输入一个链表的头节点，反转该链表并输出反转后链表的头节点。
```
输入: 1->2->3->4->5->NULL 输出: 5->4->3->2->1->NULL
```
---

标签: `链表`<br>
时间复杂度:`O(N)` 空间复杂度:`O(1)`
```c++
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        ListNode *new_head = NULL;
        while (head) {
            ListNode *temp = head->next;
            head->next = new_head;
            new_head = head;
            head = temp;
        }
        return new_head;
    }
};
```

### 25.
### 26.
### 27.
### 28.

### 29. 顺时针打印矩阵
🥉输入一个矩阵，按照从外向里以顺时针的顺序依次打印出每一个数字。
```
输入：matrix = [[1,2,3],[4,5,6],[7,8,9]] 输出：[1,2,3,6,9,8,7,4,5]
输入：matrix = [[1,2,3,4],[5,6,7,8],[9,10,11,12]] 输出：[1,2,3,4,8,12,11,10,9,5,6,7]
```
---

标签: `数组`<br>
时间复杂度:`O(N)` 空间复杂度:`O(1)`
```c++
class Solution {
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        vector<int> res;
        if (matrix.empty()) return res;
        int x1 = 0, y1 = 0;
        int x2 = matrix.size() - 1, y2 = matrix[0].size() - 1;

        while (x1 <= x2 && y1 <= y2) {
            int x = x1, y = y1;
            //🪁每次只遍历最外边的一圈,单独处理只有一行或一列的情况
            if (x1 == x2) {
                while (y <= y2) res.push_back(matrix[x1][y++]);
            } else if (y1 == y2) {
                while (x <= x2) res.push_back(matrix[x++][y1]);
            } else {
                while (y != y2) res.push_back(matrix[x1][y++]);
                while (x != x2) res.push_back(matrix[x++][y2]);
                while (y != y1) res.push_back(matrix[x2][y--]);
                while (x != x1) res.push_back(matrix[x--][y1]);
            }
            x1++; y1++; x2--; y2--;
        }
        return res;
    }
};
```

### 30. 包含min函数的栈
🥉定义栈的数据结构，请在该类型中实现一个能够得到栈的最小元素的 min 函数在该栈中，调用 min、push 及 pop 的时间复杂度都是 O(1)。
```
push(x) —— 将元素 x 推入栈中。
pop() —— 删除栈顶的元素。
top() —— 获取栈顶元素。
min() —— 检索栈中的最小元素。
```
---

标签: `栈`<br>
时间复杂度:`O(1)` 空间复杂度:`O(N)`
```c++
class MinStack {
public:
    /** initialize your data structure here. */
    MinStack() {}
    
    void push(int x) {
        data.push(x);
        //🪁若新数据小于等于最小栈的栈顶元素时,将其压入最小栈
        if (mins.empty() || x <= mins.top()) mins.push(x);
    }
    
    void pop() {
        //🪁当且仅当最小栈栈顶元素等于待弹出元素时才弹出
        if (mins.top() == data.top()) mins.pop();
        data.pop();
    }
    
    int top() {
        return data.top();
    }
    
    int min() {
        return mins.top();
    }
private:
    stack<int> data;
    stack<int> mins;
};
```

### 31.
### 32.
### 33.
### 34.
### 35.
### 36.
### 37.
### 38.
### 39.
### 40.


### 41. 数据流中的中位数
🏅️如何得到一个数据流中的中位数？如果从数据流中读出奇数个数值，那么中位数就是所有数值排序之后位于中间的数值。如果从数据流中读出偶数个数值，那么中位数就是所有数值排序之后中间两个数的平均值。<br>
设计一个支持以下两种操作的数据结构：
```
void addNum(int num) - 从数据流中添加一个整数到数据结构中。
double findMedian() - 返回目前所有元素的中位数。
```
---

标签: `堆` `排序`<br>
时间复杂度:`O(logN)` 空间复杂度:`O(N)`
```c++
class MedianFinder {
public:
    MedianFinder() {}
    
    void addNum(int num) {
        if (less.empty()) {
            less.push(num);
            return;
        }
        //🪁将新数据压入堆中(与大根堆的根元素比较),同时确保大根堆上元素个数等于或大于小根堆上元素个数一个
        num <= less.top() ?  less.push(num) : great.push(num);
        if (less.size() > great.size() + 1) {
            great.push(less.top());
            less.pop();
        } else if (less.size() < great.size()) {
            less.push(great.top());
            great.pop();
        }
    }
    
    double findMedian() {
        return less.size() == great.size() ? (less.top() + great.top()) / 2.0 : less.top();
    }
    
private:
    //🪁利用一个大根堆(存较小的数)和一个小根堆(存较大的数)来存储数据
    priority_queue<int, vector<int>, less<int>> less;
    priority_queue<int, vector<int>, greater<int>> great;
};
```
### 42.
### 43.
### 44.
### 45.
### 46.
### 47.
### 48.
### 49.
### 50.

### 51. 数组中的逆序对
🏅️在数组中的两个数字，如果前面一个数字大于后面的数字，则这两个数字组成一个逆序对。输入一个数组，求出这个数组中的逆序对的总数。
```
输入: [7,5,6,4] 输出: 5
```
---

标签: `归并算法` `逆序对`<br>
时间复杂度:`O(NlogN)` 空间复杂度:`O(N)`
```c++
class Solution {
public:
    int reversePairs(vector<int>& nums) {
        if (nums.size() <= 1) return 0;
        int pairs = 0;
        mergeSort(nums, 0, nums.size() - 1, pairs);
        return pairs;
    }
    
    void mergeSort(vector<int> &nums, int left, int right, int &pairs) {
        if (left == right) return;
        int mid = left + (right - left) / 2;
        mergeSort(nums, left, mid, pairs);
        mergeSort(nums, mid + 1, right, pairs);
        mergeSubsequence(nums, left, mid, right, pairs);
        
        
    }
    
    void mergeSubsequence(vector<int> &nums, int left, int mid, int right, int &pairs) {
        vector<int> temp;
        int i = left, j = mid + 1;
        //🪁同时遍历左右两侧的元素，当左侧元素大于右侧元素时形成逆序对
        while (i <= mid && j <= right) {
            if (nums[i] > nums[j]) {
                temp.push_back(nums[j++]);
                //🪁对左侧元素来说,一旦与右侧某元素形成逆序对，则其后面所有元素都形成逆序对
                pairs += mid - i + 1;
            } else {
                temp.push_back(nums[i++]);
            }
        }
        while (i <= mid) temp.push_back(nums[i++]);
        while (j <= right) temp.push_back(nums[j++]);
        for (int k = 0; k != temp.size(); ++k) nums[left + k] = temp[k];
    }  
};
```

### 52. 两个链表的第一个公共节点
🥉输入两个链表，找出它们的第一个公共节点。<br>
注意：如果两个链表没有交点，返回 null. 在返回结果后，两个链表仍须保持原有的结构。可假定整个链表结构中没有循环。程序尽量满足 O(n) 时间复杂度，且仅用 O(1) 内存。
```
输入：intersectVal = 8, listA = [4,1,8,4,5], listB = [5,0,1,8,4,5], skipA = 2, skipB = 3
输出：Reference of the node with value = 8
输入解释：相交节点的值为 8 （注意，如果两个链表相交则不能为 0）。从各自的表头开始算起，链表 A 为 [4,1,8,4,5]，链表 B 为 [5,0,1,8,4,5]。在 A 中，相交节点前有 2 个节点；在 B 中，相交节点前有 3 个节点。
```
---

标签: `链表`<br>
时间复杂度:`O(N)` 空间复杂度:`O(1)`
```c++
class Solution {
public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        ListNode *currA = headA, *currB = headB;
        int lenA = 0,lenB = 0;
        while (currA) {
            lenA++;
            currA = currA->next;
        }
        while (currB) {
            lenB++;
            currB = currB->next;
        }
        
        //🪁排除较长链表多出的部分后同时遍历两条链表,结点相同时即为相交节点
        currA = headA; currB = headB;
        while (lenA > lenB) {
            currA = currA->next;
            lenA--;
        } 
        while (lenA < lenB) {
            currB = currB->next;
            lenB--;
        }
        while (currA != currB) {
            currA = currA->next;
            currB = currB->next;
        }
        return currA;
    }
};
```

标签: `链表`<br>
时间复杂度:`O(N)` 空间复杂度:`O(1)`
```c++
class Solution {
public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        ListNode *currA = headA, *currB = headB;
        //🪁分别从两个链表的头节点遍历,当遇到空节点时,跳到另一个链表继续遍历
        while (currA != currB) {
            currA = currA ? currA->next : headB;
            currB = currB ? currB->next : headA;
        }
        return currA;
    }
};
```

### 53.
### 54.
### 55.
### 56.
### 57.
### 58.
### 59.
### 60.

### 61.
### 62.
### 63.
### 64.
### 65.
### 66.
### 67.
### 68.
### 69.
### 70.

### 71.
### 72.
### 73.
### 74.
### 75.
### 76.
### 77.
### 78.
### 79.
### 80.
