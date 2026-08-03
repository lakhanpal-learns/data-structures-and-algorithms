# Merge Sorted Array

# problem 
Your Task

Merge both arrays into one sorted array.

Store the result inside nums1.

Do not create a new array.

# Example
Input
nums1 = [1,2,3,0,0,0]
m = 3

nums2 = [2,5,6]
n = 3
Valid values
nums1 → [1,2,3]

nums2 → [2,5,6]
After merging
nums1 = [1,2,2,3,5,6]

# code 
class Solution {
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
       int  i = m - 1;
       int  j = n - 1;
       int   k = m + n - 1;

       while ( j>= 0)
       {
        if (i >= 0 && nums1[i]>nums2[j])
        {
            nums1[k]=nums1[i];
            i--;
            k--;
        }
        else 
        {
            nums1[k]=nums2[j];
            j--;
            k--;
        }
       }

    }
};

# code breakddown 
| Step | Question to Ask                | Answer / Action                                            |
| ---- | ------------------------------ | ---------------------------------------------------------- |
| 1    | What is given?                 | Two sorted arrays `nums1` and `nums2`.                     |
| 2    | What is the goal?              | Merge them into `nums1` in sorted order.                   |
| 3    | Can I create a new array?      | ❌ No. Use only `nums1`.                                    |
| 4    | Where is the empty space?      | At the **end** of `nums1`.                                 |
| 5    | Should I start from the front? | ❌ No, it will overwrite useful values.                     |
| 6    | Where should I start?          | ✅ From the **back**.                                       |
| 7    | Which elements do I compare?   | Last valid element of `nums1` and last element of `nums2`. |
| 8    | How many pointers?             | **3 pointers:** `i`, `j`, `k`.                             |
| 9    | Initialize pointers            | `i = m-1`, `j = n-1`, `k = m+n-1`                          |
| 10   | Which value do I place?        | Place the **larger** value at `nums1[k]`.                  |
| 11   | If `nums1[i]` is larger        | `nums1[k] = nums1[i]`, then `i--`, `k--`                   |
| 12   | Otherwise                      | `nums1[k] = nums2[j]`, then `j--`, `k--`                   |
| 13   | What is the loop condition?    | `while (j >= 0)`                                           |
| 14   | What is the edge case?         | Check `i >= 0` before using `nums1[i]`.                    |
| 15   | Time Complexity                | **O(m + n)**                                               |
| 16   | Space Complexity               | **O(1)**                                                   |



