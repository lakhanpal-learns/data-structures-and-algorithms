# Group Anagrams

Given an array of strings strs, group the anagrams together. You can return the answer in any order.

# example 
Example 1:

Input: strs = ["eat","tea","tan","ate","nat","bat"]

Output: [["bat"],["nat","tan"],["ate","eat","tea"]]

Explanation:

There is no string in strs that can be rearranged to form "bat".
The strings "nat" and "tan" are anagrams as they can be rearranged to form each other.
The strings "ate", "eat", and "tea" are anagrams as they can be rearranged to form each other.

# doubt 

# understadning 

## Brute Force

Suppose

["eat","tea","tan","ate","nat","bat"]

Compare every string with every other string.

eat vs tea

eat vs tan

eat vs ate

eat vs nat

...

If there are n strings, this leads to about O(n²) comparisons, and each comparison also takes work.

This is too slow for large inputs.

## think differently 

So after sorting

Original	Sorted
eat	aet
tea	aet
ate	aet
tan	ant
nat	ant
bat	abt

Notice something?

Every anagram has the same sorted string.

That sorted string can be our key.

## data strucuture 
Step 4: Which Data Structure?

We need

Key

↓

List of Strings

Example

"aet"

↓

eat
tea
ate

That is exactly

unordered_map<string, vector<string>>

Key

↓

Value

"aet"

↓

vector<string>

## Dry Run
First string
eat

Sort

aet

Store

mp["aet"].push_back("eat");

Map

aet

↓

eat
Second string
tea

Sort

aet

Already exists.

Push

mp["aet"].push_back("tea");

Now

aet

↓

eat

tea

# code 

class Solution {
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {

        unordered_map<string, vector<string>> mp;

        for (string str : strs)
        {
            string key = str;

            sort(key.begin(), key.end());

            mp[key].push_back(str);
        }

        vector<vector<string>> ans;

        for (auto it : mp)
        {
            ans.push_back(it.second);
        }

        return ans;
    }
};














