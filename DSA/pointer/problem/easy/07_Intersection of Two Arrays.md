# Intersection of Two Arrays

Given two integer arrays nums1 and nums2, return an array of their intersection. Each element in the result must be unique and you may return the result in any order.

 

Example 1:

Input: nums1 = [1,2,2,1], nums2 = [2,2]
Output: [2]
Example 2:

Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
Output: [9,4]
Explanation: [4,9] is also accepted.


# key point 
1. run both side pointer 
2. hash map for unique value 

# code 
class Solution {
public:
    vector<int> intersection(vector<int>& nums1, vector<int>& nums2) {

        unordered_set<int> inter;
        vector<int> answer;

        for (int num : nums1) {

            for (int x : nums2) {

                if (num == x) {
                    inter.insert(num);
                    break;
                }

            }
        }

        for (int x : inter) {
            answer.push_back(x);
        }

        return answer;
    }
};
