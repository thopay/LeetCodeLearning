Created: 2023-04-24 23:27
Home: [[🏠 Coding Interviews]] 

### General Solution Methods
- **[[HashSet]]**: A set that doesn't allow duplicates
- **[[HashMap]]**: A collection that maps keys to values

****

## Contains Duplicate
- Given an integer array, return true if any value appears **at least twice** in the array, and return false if every element is distinct

### Method 1
- Checking every number against every other number would be $O(n^{2})$ -> Bad
	- Space is $O(1)$

### Method 2
- Sorting would allow us to be able to check adjacent elements $O(n\log(n))$ (since sorting takes time)
	- Space is still $O(1)$

### Method 3 (Best)
- **[[HashSet]]** -> Insert elements in $O(1)$ time and checks if in array when inserting
	- Time $O(n)$ / Space $O(n)$ since we create a HashSet

**Solution**
```Python
def containsDuplicate(nums):
	hashset = set()
	for n in nums:
		if n in hashset:
			return True
		hashset.add(n)
```

****

## Valid Anagram
- Given two strings, s and t, return true if t is an anagram of s, and false otherwise
	- Anagram is a string using the same letters to form a different string (dog and god are anagrams)

### Method 1
- Count occurrences of each character in both strings
- Can use an array or a [[HashMap]]
- Key value will be the character and value will be the count
- Then reiterate through keys of each [[HashMap]] and make sure the values match up
	- Time $O(s+t)$ / Space $O(s+t)$ since we have to build [[HashMap|HashMaps]] up to size of $s+t$

**Solution**
```Python
def isAnagram(s, t):
	# return Counter(s) == Counter(t) # Uses HashMaps in Python

	if len(s) != len(t):
		return False
	countS, countT = {}, {}
	for i in range(len(s)):
		countS[s[i]] = 1 + countS.get(s[i], 0) # 0 is default value
		countT[t[i]] = 1 + countT.get(t[i], 0)
	for c in countS:
		if countS[c] != countT[c]:
			return False
	return True
```

### Method 2
- Can we do a solution with $O(1)$ memory?
	- Sorted order should make them become the exact string!
	- Some sort algos take $n^2$ or $n\log n$ time (sometimes use $O(n)$ extra memory)

**Solution**
```Python
def isAnagram(s, t):
	return sorted(s) == sorted(t)
```

****

## Two Sum
- Given an array of integers and a target, return indices of two values that sum to the target, return the indices
- There *should* be exactly one solution

### Method 1
- Iterate through every integer and check with every other integer
- Worst case time is $O(n^{2})$

### Method 2
- Use a [[HashMap]] to check if the complimentary value exists
- Map each value to the index of each value
- Can't reuse the same value twice
	- Resolve this by only adding the element only after visiting it
- Only need to iterate through the array once, so time is $O(n)$ and space is $O(n)$

**Solution**
```Python
def twoSum(nums, target):
	prevMap = {} # Value : Index
	for i, n in enumerate(nums):
		diff = target - n
		if diff in prevMap:
			return [prevMap[diff], i]
		prevMap[n] = i
	return
```

****

## Group Anagrams
- Given an array of strings, group the anagrams together, and return the answer in any order (return is an array of arrays)
- 26 unique chars since the letters are a-z

### Method 1
- Two strings are anagrams if we can sort them and they are equal
- Iterate through each string and sort them
	- Time is $O(m*n\log n)$ where $m$ is the length of input strings

### Method 2
- For each string, count characters from a-z
- Use a [[HashMap]] with keys as the count of a-z (e.g. [1e, 1a, 1t] for "eat" and "tea")
- Time is $O(m*n*26)$ where $m$ is total number of input strings and $n$ is the average length of a string and $26$ since that's the length of the count array
	- Simplifies to $O(m*n)$

**Solution**
```Python
def groupAnagrams(strs):
	res = defaultdict(list) # Mapping charCount to list of anagrams
	for s in strs:
		count = [0] * 26 # a ... z
		for c in s:
			count[ord(c) - ord("a")] += 1
		res[tuple(count)].append(s) # arr can't be keys so use tuple (since non-mutable)
	return res.values()
```

****

## Top K Frequent Elements
- Given an integer array and an integer k, return the k most frequent elements (in any order)

### Method 1
- Create a [[HashMap]] with the keys as the integer and values as the count
- Then add the map to a **[[MaxHeap]]**, then we can pop off the heap k times (each pop takes $\log n$ time)
	- The total time is $k\log n$

### Method 2
- Takes $O(n)$ time and space
- Use **[[Bucket Sort]]**
	- For index, map the counts of each value
	- For values, have a list of which values have a particular count
- First, create a [[HashMap]] of keys as integers and values as count then put into [[Bucket Sort]]
- Start at the size of the input array since the number of indexes of the [[Bucket Sort]] is bounded by the size of the input array (if there are 6 elements, the maximum number of particular occurrences is 6)
- Memory complexity is $O(n)$ since we have a [[HashMap]] and [[Bucket Sort]]

**Solution**
```Python
def topKFrequent(nums, k):
	count = {}
	freq = [[] for i in range(len(nums) + 1)]
	for n in nums:
		count[n] = 1 + count.get(n, 0)
	for n, c in count.items(): # returns key value pair in dict
		freq[c].append(n)
	res = []
	for i in range(len(freq) - 1, 0, -1):
		for n in freq[i]:
			res.append(n)
			if len(res) == k:
				return res
```

****

### Product of Array Except Self
- Given an integer array, return an array such that array[i] is equal to the product of all elements in the original array **except** array[i]

### Method 1

****

### Valid Sudoku

### Encode and Decode Strings

### Longest Consecutive Sequence