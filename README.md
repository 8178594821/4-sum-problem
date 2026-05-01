# 4-sum-problem

Given an array nums of n integers, return an array of all the unique quadruplets [nums[a], nums[b], nums[c], nums[d]] such that:

0 <= a, b, c, d < n
a, b, c, and d are distinct.
nums[a] + nums[b] + nums[c] + nums[d] == target

Approach:
First I sort the array. Then I fix two elements using nested loops.
For the remaining two elements, I use the two-pointer approach to find pairs that match the remaining target.
I also skip duplicates at every step to ensure unique quadruplets

Time Complexity
Sorting → O(n log n)
Loops + two pointer → O(n^3)

👉 Final: O(n³)

code:
class Solution {
    public List<List<Integer>> fourSum(int[] nums, int target) {
        List<List<Integer>> ans = new ArrayList<>();
        int n = nums.length;
        Arrays.sort(nums);
        for(int i=0; i<n; i++){
            for(int j = i+1; j<n; j++){
                long target2 = (long)target-(long)nums[i]-nums[j];
                int left=j+1;
                int right=n-1;
                while(left<right){
                    int s=nums[left]+nums[right];
                    if(s<target2){
                        left++;
                    }else if(s>target2){
                        right--;
                    }else {
                        List<Integer> list=Arrays.asList(nums[i],nums[j],nums[left],nums[right]);
                        ans.add(list);
                        while(left<right && nums[left]==list.get(2)){
                            left++;
                        }
                        while(left<right && nums[right]==list.get(3)){
                            right--;
                        }
                    }
                }
                while(j+1<n && nums[j]==nums[j+1]){
                    j++;
                }
            }
            while(i+1<n && nums[i]==nums[i+1]){
                i++;
            }
        }
        return ans;
    }
}

Dry Run code:
Har step pe:

i fix → first number
j fix → second number
left + right → remaining 2 numbers

✔️ Duplicate handling:

j skip
i skip
left/right skip

✔️ Isliye unique quadruplets

If you found this solution helpful, please give this repository a ⭐ and follow for more DSA solutions 🚀


