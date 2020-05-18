## Table of Contents
|序号|题目|难度|标签|
|:-:|:-|:-:|:-|
|51|[数组中的逆序对](#51-数组中的逆序对)|Hard|`归并算法` `逆序对`|

### 51. 数组中的逆序对
🥉在数组中的两个数字，如果前面一个数字大于后面的数字，则这两个数字组成一个逆序对。输入一个数组，求出这个数组中的逆序对的总数。
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
