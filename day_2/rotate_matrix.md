# Rotate Matrix
**Note the problem suggest to do the rotation in-place, that's why need better approach than brute force**


## Brute Force

1) Create a empty matrix with initial values 0
2) rotated matrix [j] [n-1-i] = matrix [i] [j ]
3) matrix = rotatedmatrix

**code**
```cpp
class Solution {
public:
    void rotate(vector<vector<int>>& matrix) {
        int n = matrix.size();
        vector<vector<int>> rotatedMatrix(n, vector<int>(n, 0)); 

        for(int i = 0; i < n; i++){
            for(int j = 0; j < n; j++){
                rotatedMatrix[j][n - 1 - i] = matrix[i][j]; 
            }
        }

        matrix = rotatedMatrix;
    }
};
```
## Optimal

1) Calculate the transpose of the matrix
2) swap the columns

**code**
```cpp

class Solution {
public:
    void rotate(vector<vector<int>>& matrix) {
        int n = matrix.size();

        for(int i = 0; i<n; i++){
            for(int j=i+1; j<n; j++){
                swap(matrix[j][i], matrix[i][j]);
            }
        }

        for(int i=0; i<n; i++){
            for(int j=0; j<n/2; j++){
                swap(matrix[i][j], matrix[i][n-j-1]);
            }
        }

    }
};
```
