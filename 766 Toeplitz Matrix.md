## Problem Description
A matrix is Toeplitz if every diagonal from top-left to bottom-right has the same element.

Now given an M x N matrix, return True if and only if the matrix is Toeplitz.

### Examples

Input: matrix = [[1,2,3,4],[5,1,2,3],[9,5,1,2]]
Output: True
Explanation:
1234
5123
9512

In the above grid, the diagonals are "[9]", "[5, 5]", "[1, 1, 1]", "[2, 2, 2]", "[3, 3]", "[4]", and in each diagonal all elements are the same, so the answer is True.

Explanation:
The row-traversing of nums is [1,2,3,4]. The new reshaped matrix is a 1 * 4 matrix, fill it row by row by using the previous list.

## My Solution
### code:
    class Solution {
        public boolean isToeplitzMatrix(int[][] matrix) {
            int rows=matrix.length;
            int cols=matrix[0].length;
            for(int j=0;j<cols;++j){
                int i=0,k=j;
                int pivot=matrix[i][k];
                while(i<rows&&k<cols){
                    if(matrix[i++][k++]!=pivot)
                        return false;
                }
            }
            for(int i=1;i<rows;++i){
                int j=0,k=i;
                int pivot=matrix[k][j];
                while(k<rows&&j<cols){
                    if(matrix[k++][j++]!=pivot)
                        return false;
                }
            }
            return true;
        }
    }
### rethink
#### 贴个最简洁的版本
    class Solution {
        public boolean isToeplitzMatrix(int[][] matrix) {
            for (int i = 0; i < matrix.length - 1; i++) {
                for (int j = 0; j < matrix[i].length - 1; j++) {
                    if (matrix[i][j] != matrix[i + 1][j + 1]) return false;
                }
            }
            return true;
        }
    }
事实上这个版本虽然简单，但是做了许多无意义的循环。