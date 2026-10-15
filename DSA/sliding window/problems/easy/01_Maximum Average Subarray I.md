# Maximum Average Subarray I
You are given an integer array nums consisting of n elements, and an integer k.

Find a contiguous subarray whose length is equal to k that has the maximum average value and return this value

<!-- example  -->
Example 1:

Input: nums = [1,12,-5,-6,50,3], k = 4
Output: 12.75000
Explanation: Maximum average is (12 - 5 - 6 + 50) / 4 = 51 / 4 = 12.75

# key points 



# code 
class Solution {
public:
    double findMaxAverage(vector<int>& nums, int k) {
    int current_sum = 0;
    int left = 0;
    int right = k - 1;

    for (int i = left; i <= right; i++) {
        current_sum += nums[i];
    }

    int max_sum = current_sum;

    while (right + 1 < nums.size()) {
        current_sum -= nums[left];
        left++;

        right++;
        current_sum += nums[right];

        max_sum = max(max_sum, current_sum);
    }

    return (double)max_sum / k;
    }
};

# algo 