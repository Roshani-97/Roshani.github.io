# Day 1.1 — Two Sum
**Platform:** Leetcde 
**Difficulty:** Easy  
**Topic:** Array / HashMap

## Problem Statement
Given an array of integers 'nums' and an integer 'target', return indices of the two numbers that add up to 'target'.
## BRUTE FORCE APPROACH:

"First, we create an empty array to store the indices.
Then, we run a for loop within a while loop, checking the condition that the sum equals the target sum.
If it does, we store the index of that element in the ans vector. After completing the loop, we return ans."
"Since the time complexity of the code is (O(n*n)), which gives TLE. Hence, we look for an optimal approach."
```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        int n=nums.size();
        vector<int> ans;
        int i=0;
        while(i<n){
            for(int j=i+1;j<n;j++){
                if(nums[i]+nums[j]==target){
                    ans.push_back(i);
                    ans.push_back(j);
                }
            }
            i++;
        }
        return ans;
    }
};
```
## OPTIMAL APPROACH
Use hash HashMap to store previously seen numbers.
Time complexity = O(n)
Space complexity = O(n)
```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        vector<int> ans;
        int n=nums.size();
        unordered_map<int,int> m;
        for(int i=0;i<n;i++){
            int first=nums[i];
            int sec=target-first;
            if(m.find(sec)!=m.end()){
                ans.push_back(i);
                ans.push_back(m[sec]);
                break;
            }
            m[first]=i;
        }
        return ans;
    }
};
```
## WHAT I LEARNED
1. Importance of HashMap (since it reduces the time complexity by checking if its complement already exists)
2. It handles duplicates.
