## Table of Contents
|序号|题目|难度|标签|
|:-:|:-|:-:|:-|
|41|[数据流中的中位数](#41-数据流中的中位数)|Hard|`堆` `排序`|
|51|[数组中的逆序对](#51-数组中的逆序对)|Hard|`归并算法` `逆序对`|


### 41. 数据流中的中位数
🏅️如何得到一个数据流中的中位数？如果从数据流中读出奇数个数值，那么中位数就是所有数值排序之后位于中间的数值。如果从数据流中读出偶数个数值，那么中位数就是所有数值排序之后中间两个数的平均值。<br>
设计一个支持以下两种操作的数据结构：
```
void addNum(int num) - 从数据流中添加一个整数到数据结构中。
double findMedian() - 返回目前所有元素的中位数。
```

标签: `堆` `排序`<br>
时间复杂度:`O(logN)` 空间复杂度:`O(N)`
```c++
class MedianFinder {
public:
    /** initialize your data structure here. */
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
