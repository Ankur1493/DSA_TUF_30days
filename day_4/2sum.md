# TWO SUM

## Brute Force

**Approach**
Just run two loops and calculate sum for each value

**Time Complexity** O(n^2)

## Better using hashmap

**Approach**
Use a hash table and when you iterate over the element add nums [i]  and check if previously you have addded target-nums [i]

**code**

```cpp

#include <vector>
#include <unordered_map>

class Solution {
public:
    std::vector<int> twoSum(std::vector<int>& nums, int target) {
        std::unordered_map<int, int> hashTable;
        std::vector<int> ans;
        
        for (int i = 0; i < nums.size(); i++) {
            int complement = target - nums[i];
            if (hashTable.find(complement) != hashTable.end()) {
                ans.push_back(hashTable[complement]);
                ans.push_back(i);
                return ans;
            }
            hashTable[nums[i]] = i;
        }
        
        return ans;
    }
};
```


**Time Complexity** O(n) **Space Complexity** O(n)

## Optimal

**Approach**

1) Two pointers
2) left = 0 and right = n-1 
3) If arr[left] + arr[right] > sum, we will decrement the right pointer.
4) If arr[left] + arr[right] < sum, we will increment the left pointer.
5) If arr[left] + arr[right] == sum, we will return the result.

**Code**
```cpp 

class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
       vector<int> help;
        vector<int> ans;
        for(int i=0;i<nums.size();i++)
        {
            help.push_back(nums[i]);
        }
        sort(help.begin(),help.end());
        int start=0;
        int end=help.size()-1;

        while(start<end)
        {
            int sum = help[start]+help[end];
            if(sum==target){
                break;
            }
            else if(sum>target){
                end--;
            }
            else{
                start++;
}
        }
        for(int i=0;i<nums.size();i++)
        {
            if(help[start]==nums[i] || help[end]==nums[i]){
                ans.push_back(i);
            }
        }
        return ans;
    }
};

```
**Time Complexity** O(n) , **Space Complexity** O(1)

