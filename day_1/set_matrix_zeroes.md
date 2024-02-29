# SET Matrix Zeroes

## BRUTE FORCE 

1) we will iterate over the matrix and turn every row and column to -1 which contains 0, except the cells with 0
2) Then we will iterate over the matrix again and turn -1to 0

**Time Complexity** - O(n*m)(n+m) nearly O(n^3)

**CODE**
class Solution {
public:

    void markRow(vector<vector<int>> &matrix, int n, int m, int i) {
    for (int j = 0; j < m; j++) {
        if (matrix[i][j] != 0) {
            matrix[i][j] = -1;
        }
    }
}


void markCol(vector<vector<int>> &matrix, int n, int m, int j) {
    for (int i = 0; i < n; i++) {
        if (matrix[i][j] != 0) {
            matrix[i][j] = -1;
        }
    }
}


    void setZeroes(vector<vector<int>>& matrix) {
        
        int rows = matrix.size();
        int columns = matrix[0].size();
        
        for(int i = 0; i<rows; i++){
            for(int j = 0; j< columns; j++){
                if(matrix[i][j] == 0){
                    markRow(matrix, rows, columns, i);
                    markCol(matrix, rows, columns, j);
                }
            }
        }

        for(int k = 0; k<rows; k++){
            for(int l = 0; l<columns; l++){
                if(matrix[k][l] == -1)
                    matrix[k][l] = 0;
            }
        }
    }
};

## Better

1) create two arrays of length no of row and col
2) We will iterate over the matrix and when a cell value is zero turn row[i] can col[j] = 0
3) In our final iteration we will use these vectors to turn values to zero

**Time Complexity** - O(n*m) nearly O(n^2)


**CODE**

class Solution {
public:
    void setZeroes(vector<vector<int>>& matrix) {
        int rows = matrix.size();
        int columns = matrix[0].size();

        vector<int> zeroRow(rows, 0);
        vector<int> zeroCol(columns, 0);

        for(int i = 0; i < rows; i++){
            for(int j = 0; j < columns; j++){
                if(matrix[i][j] == 0){
                    zeroRow[i] = 1;
                    zeroCol[j] = 1;
                }
            }
        }

        for(int i = 0; i < rows; i++){
            for(int j = 0; j < columns; j++){
                if(zeroRow[i] == 1 || zeroCol[j] == 1){
                    matrix[i][j] = 0;
                }
            }
        }
    }
};

