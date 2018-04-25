## Problem Description
Given a binary array, find the maximum number of consecutive 1s in this array.

### Examples

Input: [1,1,0,1,1,1]

Output: 3

Explanation: The first two digits or the last three digits are consecutive 1s.
    The maximum number of consecutive 1s is 3.

## My Solution
### code:
    class Solution {
        public int findMaxConsecutiveOnes(int[] nums) {
            int ans=0,rec=0;
            if(nums.length==0 || (nums.length==1 && nums[0]==0))
                return 0;
            if(nums.length==1)
                return 1;
            for(int i=0;i<nums.length;++i){
                if(nums[i]==1)
                    rec++;
                else {
                    ans = Math.max(rec,ans);
                    rec=0;
                }
            }
            ans = Math.max(rec,ans);
            return ans;
        }
    }
### rethink
#### 贴个最简洁的版本
    public int findMaxConsecutiveOnes(int[] nums) {
        int maxHere = 0, max = 0;
        for (int n : nums)
            max = Math.max(max, maxHere = n == 0 ? 0 : maxHere + 1);
        return max; 
    } 