# Move Zeroes
Given an integer array nums, move all 0's to the end of it while maintaining the relative order of the non-zero elements.

Note that you must do this in-place without making a copy of the array.

# example 
Example 1:

Input: nums = [0,1,0,3,12]
Output: [1,3,12,0,0]
Example 2:

Input: nums = [0]
Output: [0]


# code 
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        int s=0;
        int f=0;

        while (f <= nums.size()-1)
        {
             if(nums[f]!=0)
             {
                swap(nums[s],nums[f]);
                f++;
                s++;
             }

             else{
                f++;
             }
        }
    }
};

