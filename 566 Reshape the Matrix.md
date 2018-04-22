## Problem Description
In MATLAB, there is a very useful function called 'reshape', which can reshape a matrix into a new one with different size but keep its original data.

You're given a matrix represented by a two-dimensional array, and two positive integers r and c representing the row number and column number of the wanted reshaped matrix, respectively.

The reshaped matrix need to be filled with all the elements of the original matrix in the same row-traversing order as they were.

If the 'reshape' operation with given parameters is possible and legal, output the new reshaped matrix; Otherwise, output the original matrix.

### Examples

Input: 
nums = 
[[1,2],
 [3,4]]
r = 1, c = 4

Output: 
[[1,2,3,4]]

Explanation:
The row-traversing of nums is [1,2,3,4]. The new reshaped matrix is a 1 * 4 matrix, fill it row by row by using the previous list.

## My Solution
### code:
    class Solution {
        public int[][] matrixReshape(int[][] nums, int r, int c) {
            int rows=nums.length;
            int cols=nums[0].length;
            if(rows*cols!=r*c)
                return nums;
            int[][] ans = new int[r][c];
            for(int i=0;i<r;i++)
                for(int j=0;j<c;j++){
                    int index = i*c+j;
                    int origin_row_index = index/cols;
                    int origin_col_index = index%cols;
                    ans[i][j] = nums[origin_row_index][origin_col_index];
                }
            return ans;
        }
    }
### rethink
刚学着使用Java，犯了一个错，在建立二维数组时，Java与C++还是不同的，谨记，int[][] mat=new int[m][n];