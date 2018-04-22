## Problem Description
Given an array of 2n integers, your task is to group these integers into n pairs of integer, say (a1, b1), (a2, b2), ..., (an, bn) which makes sum of min(ai, bi) for all i from 1 to n as large as possible.

### Examples

Input: [1,4,3,2]

Output: 4

Explanation: n is 2, and the maximum sum of pairs is 4 = min(1, 2) + min(3, 4).

## My Solution
问题要求2N长度的数组形成N个pair，其中每个pair的最小值和最小。因此考虑将数组进行升序排序，形成a1,a2,a3,...,a2N的数组，其中a1<=a2<=a3<=...<=a2N.这样做的好处在于，按顺序将数字两两形成pair。以长度为4的数组举例，例如已形成升序数组(a1,a2,a3,a4)，此时，a1作为最小值，无论与剩下的哪个数字形成pair，这个pair的最小值必定是pair，因此我们只需要考虑将另一个pair的最小值最大化，而剩下的三个数字中最小的是a2,如果将a2与a3或者a4形成pair，则另一个pair的最小值必定是a2，但如果将a2与a1形成pair，则a1所在pair的最小值仍然是a1，另一个pair的最小值则变成了a3，避免了a1与a2分别为两个pair的最小值的情况。同理，当数组长度为6时，通过将a1,a2形成pair，剩下的4个数字组合情况同上。因此，这个思路可以推广到2N长度的数组。
### code:
    class Solution {
        public int arrayPairSum(int[] nums) {
            Arrays.sort(nums);
            int sum=0;
            for(int i=0;i<nums.length;++i)
                sum+=nums[i]*((i%2+1)%2);
            return sum;
        }
    }

### rethink
代码写的还是不够简洁，特别是取奇数位的数字时，直接在循环中利用i+=2即可完成，直接减少循环次数，而不是利用((i%2+1)%2)这样的方法。