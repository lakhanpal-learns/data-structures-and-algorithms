# Move Zeroes













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

