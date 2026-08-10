# Majority Element II
Given an integer array of size n, find all elements that appear more than ⌊n / 3⌋ times.

# code 
class Solution {
public:
    vector<int> majorityElement(vector<int>& nums) {

        unordered_map<int, int> mp;

        // Phase 1: Count frequency of every number
        for (int num : nums) {
            mp[num]++;
        }

        // Phase 2: Find numbers appearing more than n/3 times
        vector<int> ans;

        for (auto x : mp) {
            if (x.second > nums.size() / 3) {
                ans.push_back(x.first);
            }
        }

        return ans;
    }
};

