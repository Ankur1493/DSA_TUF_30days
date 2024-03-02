# Merge Two Sorted Array


1)  We initialize three pointers:
      1)  i pointing to the end of the first sorted array nums1.
      1)  j pointing to the end of the second sorted array nums2.
      1)  k pointing to the end of the combined array where we'll be merging elements.

2)    We start comparing elements from the end of both arrays (nums1 and nums2) and place the larger element at position k in nums1. We then decrement pointers accordingly.

3) After this loop, if there are any remaining elements in nums2, we simply copy them over to their correct positions in nums1.


**CODE** 
```cpp

class Solution {
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
        int i = m - 1;
        int j = n - 1;
        int k = m + n - 1;

        while (i >= 0 && j >= 0) {
            if (nums1[i] > nums2[j]) {
                nums1[k--] = nums1[i--];
            } else {
                nums1[k--] = nums2[j--];
            }
        }

        while (j >= 0) {
            nums1[k--] = nums2[j--];
        }
    }
};
```
**Time Complexity** O(m+n)
