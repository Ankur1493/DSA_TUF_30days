# Pascal Triangle

## Code

```cpp

class Solution {
public:
    vector<vector<int>> generate(int numRows) {
        vector<vector<int>> pascal(numRows);

        for (int i = 0; i < numRows; i++) {
            pascal[i].resize(i + 1);
            for (int j = 0; j <= i; j++) {
                int temp = 0;
                if (j == 0 || j == i) {
                    temp = 1;
                } else {
                    temp = pascal[i - 1][j - 1] + pascal[i - 1][j];
                }
                pascal[i][j] = temp;
            }
        }
        return pascal;
    }
};
```
