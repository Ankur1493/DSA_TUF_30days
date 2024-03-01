# Next Permutation

## Brute Force

1) Find all the possible Permutations, using recursion
2) Sort them
3) Linear search and return next index

**Time Complexity**  O(N!*N)

## Optimal 

1) Find break Index (from right side find the first element which is less than i+1)
2) Swap breakIndex value from the number which isgreater than breakindex value but most close to it 
3) Reverse from break index to n 
4) if breakIndex = -1 that means we are at last Permutation than we just have to return 1st Permutation, so reverse whole array

**CODE**
```cpp
class Solution {
public:
    void reverseArr(vector<int>& nums, int start, int end){
        while(start < end){
            swap(nums[start], nums[end]);
            start++;
            end--;
        }
    }

    void nextPermutation(vector<int>& nums) {
        int n = nums.size();
        int breakIndex = -1;
        
        // Finding break index
        for(int i = n-2; i >= 0; i--){
            if(nums[i] < nums[i+1]){
                breakIndex = i;
                break;
            }
        }

        if(breakIndex != -1){
            // Finding the next big integer than nums[breakIndex]
            for(int i = n-1; i > breakIndex; i--){
                if(nums[i] > nums[breakIndex]){
                    swap(nums[i], nums[breakIndex]);
                    break;
                }
            }
            reverseArr(nums, breakIndex+1, n-1);
        } else {
            // If no break index found, reverse the entire array
            reverseArr(nums, 0, n-1);
        }
    }
};
```

**Time Complexity** O(3*N)

