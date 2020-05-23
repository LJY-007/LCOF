## Table of Contents
|序号|题目|难度|标签|LeetCode|
|:-:|:-|:-:|:-|:-:|
|1|[赋值运算符函数]()||||
|2|[]()||||
|3|[]()||||
|4|[二维数组中的查找](#4-二维数组中的查找)|Easy|`数组`|240|
|5|[]()||||
|6|[从尾到头打印链表](#6-从尾到头打印链表)|Easy|`链表` `数组` `栈` `递归`|～|
|7|[]()||||
|8|[二叉树的下一个结点](#8-二叉树的下一个结点)|Easy|`二叉树`|～|
|9|[用两个栈实现队列](#9-用两个栈实现队列)|Easy|`栈` `队列`|232|
|10|[]()||||
|11|[]()||||
|12|[]()||||
|13|[]()||||
|14|[]()||||
|15|[]()||||
|16|[]()||||
|17|[]()||||
|18|[删除链表的节点](#18-删除链表的节点)|Easy|`链表`|203|
|19|[]()||||
|20|[]()||||
|21|[]()||||
|22|[链表中倒数第k个节点](#22-链表中倒数第k个节点)|Easy|`链表` `双指针`|～|
|23|[链表中环的入口节点](#23-链表中环的入口节点)|Medium|`链表` `快慢指针`|142|
|24|[反转链表](#24-反转链表)|Easy|`链表`|206|
|25|[]()||||
|26|[]()||||
|27|[]()||||
|28|[]()||||
|29|[顺时针打印矩阵](#29-顺时针打印矩阵)|Easy|`数组`|54|
|30|[包含min函数的栈](#30-包含min函数的栈)|Easy|`栈`|155|
|31|[]()||||
|32-I|[从上到下打印二叉树 I](#32-I-从上到下打印二叉树-I)||||
|32-II|[从上到下打印二叉树 II](#32-II-从上到下打印二叉树-II)|Easy||102|
|33|[]()||||
|34|[]()||||
|35|[复杂链表的复制](#35-复杂链表的复制)|Medium|`链表` `哈希表`|138|
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

### 3. 数组中重复的数字
🥉找出数组中重复的数字。
在一个长度为 n 的数组 nums 里的所有数字都在 0～n-1 的范围内。数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次。请找出数组中任意一个重复的数字。
```
输入：[2, 3, 1, 0, 2, 5, 3] 输出：2 或 3 
```
---

标签: `数组` `哈希表`<br>
时间复杂度:`O(N)` 空间复杂度:`O(N)`
```c++
class Solution {
public:
    int findRepeatNumber(vector<int>& nums) {
        unordered_map<int, int> counter;
        for (int i : nums) {
            if (counter.find(i) != counter.end()) return i;
            counter[i]++;
        }
        return -1;
    }
};
```

标签: `数组`<br>
时间复杂度:`O(N)` 空间复杂度:`O(1)`
```c++
class Solution {
public:
    int findRepeatNumber(vector<int>& nums) {
        for (int i = 0; i != nums.size(); ++i) {
            //🪁将数组的下标和数据元素的值对应
            if (nums[i] != i) {
                if (nums[nums[i]] == nums[i]) return nums[i];
                swap(nums[i], nums[nums[i]]);
                i--;
            }
        }
        return -1;
    }
};
```


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

### 6. 从尾到头打印链表
🥉输入一个链表的头节点，从尾到头反过来返回每个节点的值（用数组返回）。
```
输入：head = [1,3,2] 输出：[2,3,1]
```
---

标签: `链表`<br>
时间复杂度:`O(N)` 空间复杂度:`O(N)`
```c++
class Solution {
public:
    vector<int> reversePrint(ListNode* head) {
        ListNode *new_head = NULL;
        //🪁反转链表后再次遍历并输出val(修改了链表结构)
        while (head) {
            ListNode *temp = head->next;
            head->next = new_head;
            new_head = head;
            head = temp;
        }
        vector<int> res;
        while (new_head) {
            res.push_back(new_head->val);
            new_head = new_head->next;
        }
        return res;
    }
};
```

标签: `链表` `数组`<br>
时间复杂度:`O(N)` 空间复杂度:`O(N)`
```c++
class Solution {
public:
    vector<int> reversePrint(ListNode* head) {
        ListNode *curr = head;
        int len = 0;
        //🪁遍历链表建立等长的数组,再次遍历输出对应(相反)位置的值
        while (curr) {
            len++;
            curr = curr->next;
        }
        vector<int> res(len);
        curr = head;
        while (curr) {
            res[--len] = curr->val;
            curr = curr->next;
        }
        return res;
    }
};
```

标签: `链表` `栈`<br>
时间复杂度:`O(N)` 空间复杂度:`O(N)`
```c++
class Solution {
public:
    vector<int> reversePrint(ListNode* head) {
        //🪁使用栈结构遍历压入链表结点后依次弹出并打印
        stack<ListNode*> nodes;
        while (head) {
            nodes.push(head);
            head = head->next;
        }
        vector<int> res;
        while (!nodes.empty()) {
            res.push_back(nodes.top()->val);
            nodes.pop();
        }
        return res;
    }
};
```

标签: `链表` `递归`<br>
时间复杂度:`O(N)` 空间复杂度:`O(N)`
```c++
class Solution {
public:
    vector<int> reversePrint(ListNode* head) {
        if (!head) return res;
        //🪁递归方法(本质与栈相同)实现链表的打印
        reversePrint(head->next);
        res.push_back(head->val);
        return res;
    }

private:
    vector<int> res;
};
```

### 7.

### 8. 二叉树的下一个结点
🥉给定一个二叉树和其中的一个结点，请找出中序遍历顺序的下一个结点并且返回。注意，树中的结点不仅包含左右子结点，同时包含指向父结点的指针。

---

标签: `二叉树` `中序遍历`<br>
时间复杂度:`O(\)` 空间复杂度:`O(1)`
```c++
class Solution {
public:
    TreeLinkNode* GetNext(TreeLinkNode* pNode) {
        if (!pNode) return NULL;
        //🪁若结点有右子树,那么它的右子树中的最左子结点即为下一个结点
        if (pNode->right) {
            pNode = pNode->right;
            while (pNode->left) pNode = pNode->left;
            return pNode;
        } else {
            /*🪁当前结点若为父结点的左子结点,则父结点即为下一个结点;
                若当前结点为父结点的右子结点,则不断往上迭代直到找到是其父结点的左子结点的结点(其父结点为下一个节点)*/
            while (pNode->parent && pNode->parent->right == pNode) pNode = pNode->parent;
            return pNode->parent;
        }
    }
};
```

### 9. 用两个栈实现队列
🥉用两个栈实现一个队列。队列的声明如下，请实现它的两个函数 appendTail 和 deleteHead ，分别完成在队列尾部插入整数和在队列头部删除整数的功能。(若队列中没有元素，deleteHead 操作返回 -1 )
```
输入：["CQueue","appendTail","deleteHead","deleteHead"] [[],[3],[],[]]
输出：[null,null,3,-1]
```
---

标签: `栈` `队列`<br>
时间复杂度:`O(N)` 空间复杂度:`O(N)`
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

### 18. 删除链表的节点
🥉给定单向链表的头指针和一个要删除的节点的值，定义一个函数删除该节点。返回删除后的链表的头节点。
```
输入: head = [4,5,1,9], val = 5 输出: [4,1,9]
```
---

标签: `链表`<br>
时间复杂度:`O(N)` 空间复杂度:`O(1)`
```c++
class Solution {
public:
    ListNode* deleteNode(ListNode* head, int val) {
        ListNode pre_node(0); //新建头结点便于对第一个结点的操作
        ListNode *curr = &pre_node;
        curr->next = head;
        while (curr->next) {
            if (curr->next->val == val) {
                curr->next = curr->next->next;
                break;
            }
            curr = curr->next;
        }
        return pre_node.next;
    }
};
```

### 19.
### 20.

### 21.

### 22. 链表中倒数第k个节点
🥉输入一个链表，输出该链表中倒数第k个节点。为了符合大多数人的习惯，本题从1开始计数，即链表的尾节点是倒数第1个节点。例如，一个链表有6个节点，从头节点开始，它们的值依次是1、2、3、4、5、6。这个链表的倒数第3个节点是值为4的节点。
```
给定一个链表: 1->2->3->4->5, 和 k = 2.
返回链表 4->5.
```
---

标签: `链表`<br>
时间复杂度:`O(N)` 空间复杂度:`O(1)`
```c++
class Solution {
public:
    ListNode* getKthFromEnd(ListNode* head, int k) {
        if (k <= 0) return NULL;
        //🪁遍历链表得到倒数第k个结点的顺序数
        ListNode *curr = head;
        int len = 0;
        while (curr) {
            len++;
            curr = curr->next;
        }
        if (len < k) return NULL;
        curr = head;
        for (int i = len - k; i != 0; i--) curr = curr->next;
        return curr;
    }
};
```

标签: `链表` `双指针`<br>
时间复杂度:`O(N)` 空间复杂度:`O(1)`
```c++
class Solution {
public:
    ListNode* getKthFromEnd(ListNode* head, int k) {
        ListNode *fast = head, *slow = head;
        if (k <= 0) return NULL;
        //🪁维持双指针跨度为k个结点并同时向后遍历,当快指针到达最后一个结点时返回慢指针
        while (--k) {
            fast = fast->next;
            if (!fast) return NULL;
        }
        while (fast->next) {
            slow = slow->next;
            fast = fast->next;
        }
        return slow;
    }
};
```

### 23. 链表中环的入口节点
🥈给定一个链表，返回链表开始入环的第一个节点。 如果链表无环，则返回 null。
为了表示给定链表中的环，我们使用整数 pos 来表示链表尾连接到链表中的位置（索引从 0 开始）。 如果 pos 是 -1，则在该链表中没有环。
说明：不允许修改给定的链表。
```
输入：head = [3,2,0,-4], pos = 1 输出：tail connects to node index 1
解释：链表中有一个环，其尾部连接到第二个节点。
输入：head = [1], pos = -1 输出：no cycle
解释：链表中没有环。
```
---

标签: `链表` `快慢指针`<br>
时间复杂度:`O(N)` 空间复杂度:`O(1)`
```c++
class Solution {
public:
    ListNode *detectCycle(ListNode *head) {
        ListNode *fast = head, *slow = head;
        //🪁判断是否有环并确定快慢指针相遇的位置
        while (fast && fast->next) {
            slow = slow->next;
            fast = fast->next->next;
            if (fast == slow) break;
        }
        if (!fast || !fast->next) return NULL;
        //🪁快慢指针第一次相遇的结点与入环结点的距离等于头结点与入环结点的距离
        fast = head;
        while (1) {
            if (fast == slow) return fast;
            fast = fast->next;
            slow = slow->next;
        }
    }
};
```

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

### 32-II. 从上到下打印二叉树 II
🥉从上到下按层打印二叉树，同一层的节点按从左到右的顺序打印，每一层打印到一行。
```
给定二叉树: [3,9,20,null,null,15,7] 
    3
   / \
  9  20
    /  \
   15   7
返回其层次遍历结果:
[
  [3],
  [9,20],
  [15,7]
]
```

---

标签: `二叉树` `BFS`<br>
时间复杂度:`O(N)` 空间复杂度:`O(N)`
```c++
class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) {
        vector<vector<int>> res;
        if (!root) return res;
        //🪁利用队列FIFO的特点对每一层进行迭代输出
        queue<TreeNode*> nodes;
        nodes.push(root);
        while (!nodes.empty()) {
            int len = nodes.size();
            vector<int> temp;
            while (len--) {
                temp.push_back(nodes.front()->val);
                if (nodes.front()->left) nodes.push(nodes.front()->left);
                if (nodes.front()->right) nodes.push(nodes.front()->right);
                nodes.pop();
            }
            res.push_back(temp);
        }
        return res;
    }
};
```

### 33.
### 34.
### 35. 复杂链表的复制
🥈请实现 copyRandomList 函数，复制一个复杂链表。在复杂链表中，每个节点除了有一个 next 指针指向下一个节点，还有一个 random 指针指向链表中的任意节点或者 null。
```
输入：head = [[7,null],[13,0],[11,4],[10,2],[1,0]]
输出：[[7,null],[13,0],[11,4],[10,2],[1,0]]
```
---

标签: `链表` `哈希表`<br>
时间复杂度:`O(N)` 空间复杂度:`O(N)`
```c++
class Solution {
public:
    Node* copyRandomList(Node* head) {
        //🪁利用哈希表建立复制链表与原链表的对应关系
        unordered_map<Node*, Node*> nodes;
        Node *new_head = head;
        while (head) {
            nodes[head] = new Node(head->val);
            head = head->next;
        }
        //🪁依次遍历将每个结点的next与random指针对应
        head = new_head;
        while (head) {
            nodes[head]->next = nodes[head->next];
            nodes[head]->random = nodes[head->random];
            head = head->next;
        }
        new_head = nodes[new_head];
        return new_head;
    }
};
```

标签: `链表`<br>
时间复杂度:`O(N)` 空间复杂度:`O(N)`
```c++
class Solution {
public:
    Node* copyRandomList(Node* head) {
        if (!head) return head;
        Node *new_head = head;
        //🪁遍历整个链表,在每个结点的后面新建对应的复制结点
        while (head) {
            Node *temp = head->next;
            head->next = new Node(head->val);
            head->next->next = temp;
            head = temp;
        }
        //🪁遍历链表完成内部指针关系的复制(每两个结点一组,next节点的random指向当前节点的random的next)
        head = new_head;
        while (head) {
            if (head->random) head->next->random = head->random->next; //注意random为空的情况
            head = head->next->next;
        }
        //🪁复制完成后要分离链表,不影响原链表结构
        head = new_head;
        new_head = new_head->next;
        while (head) {
            Node *temp = head->next->next;
            if (temp) head->next->next = temp->next; //注意最后一个两个结点的分离
            head->next = temp;
            head = temp;
        }
        return new_head;
    }
};
```

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
