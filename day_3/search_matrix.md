# Search in a sorted Matrix

## Brute Force

1) just run a simple loop Search
2) return true if found

**Time Complexity** O(m*n)

## Optimal

1) Simple Binary Search
2) start = 0, end = row*columns-1, mid = start+end/2 
3) in loop elem = matrix [mid/col] [mid%col]
4) same procedure as Binary Search

**CODE**
```cpp
class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
        int row = matrix.size();
        int col = matrix[0].size();

        int s = 0;
        int e = row*col -1; 
        int mid = s+ (e-s)/2;

        while(s<=e){
            int element = matrix[mid/col][mid%col];
            if(element == target){
                return true;
            }else if(element > target){
                e = mid-1;
            }else{
                s = mid+1;
            }
            mid = s + (e-s)/2;
        }
        return false;
    }
};

```

**Time Complexity** O(log(m*n))
