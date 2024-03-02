# Merge Intervals

## Brute Force

1) Sort the Intervals
2) after that start = interval [i] [0] and end = interval [i] [1]
3) after that run another loop to check if there lies any interval

**Code**
```cpp
vector<vector<int>> mergeOverlappingIntervals(vector<vector<int>> &arr) {
    int n = arr.size(); // size of the array

    //sort the given intervals:
    sort(arr.begin(), arr.end());

    vector<vector<int>> ans;

    for (int i = 0; i < n; i++) { // select an interval:
        int start = arr[i][0];
        int end = arr[i][1];

        //Skip all the merged intervals:
        if (!ans.empty() && end <= ans.back()[1]) {
            continue;
        }

        //check the rest of the intervals:
        for (int j = i + 1; j < n; j++) {
            if (arr[j][0] <= end) {
                end = max(end, arr[j][1]);
            }
            else {
                break;
            }
        }
        ans.push_back({start, end});
    }
    return ans;
}
```

**Time Complexity** O(N* logN) for sorting and O(2N) for looping

## Optimal

1) Sort the array
2) create a seperate vector<vector<int>> ans
3) if ans is empty or the first element of i vector is > ans.back()[1] than push the i vector
4) else ans.back() [1] = max of ans.back()[1] or arr [i] [1]

**code**

```cpp
class Solution {
public:
    vector<vector<int>> merge(vector<vector<int>>& intervals) {

     int n = intervals.size();
     sort(intervals.begin(), intervals.end());

     vector<vector<int>> mergedIntervals;

     for(int i=0; i<n; i++){

         if(mergedIntervals.empty() || intervals[i][0] > mergedIntervals.back()[1]){
             mergedIntervals.push_back({intervals[i][0], intervals[i][1]});
         }else{

            mergedIntervals.back()[1] = max(mergedIntervals.back()[1], intervals[i][1]);
         }
     }
    return mergedIntervals;
    }
};
```

**Time Complexity** O(N) for single looping and O(N logN) for sorting

