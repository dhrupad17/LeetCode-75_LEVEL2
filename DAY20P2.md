# Permutations
---
- ## Question:
> Given an array nums of distinct integers, return all the possible permutations. You can return the answer in any order.
---
- ## Example:
> Input: nums = [1,2,3]
> 
> Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
---
- ## Solution:
**Code :**
```java
public class Solution {
   public List<List<Integer>> permute(int[] nums) {
		return permute(Arrays.stream(nums).boxed().collect(Collectors.toList()));
   }

	private List<List<Integer>> permute(List<Integer> nums) {
		List<List<Integer>> permutations = new ArrayList<>();
		if (nums.size() == 0) {
			return permutations;
		}
		if (nums.size() == 1) {
			List<Integer> permutation = new ArrayList<>();
			permutation.add(nums.get(0));
			permutations.add(permutation);
			return permutations;
		}
		
		List<List<Integer>> smallPermutations = permute(nums.subList(1, nums.size()));
		int first = nums.get(0);
		for(List<Integer> permutation : smallPermutations) {
			for (int i = 0; i <= permutation.size(); i++) {
				List<Integer> newPermutation = new ArrayList<>(permutation);
				newPermutation.add(i, first);
				permutations.add(newPermutation);
			}
		}
		return permutations;
	}
}
