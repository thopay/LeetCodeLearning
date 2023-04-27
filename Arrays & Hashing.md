Created: 2023-04-24 23:27
Home: [[🏠 Coding Interviews]] 

### General Solution Methods
- **[[HashSet]]**: A set that doesn't allow duplicates
- **[[HashMap]]**: A collection that maps keys to values
- **[[Bucket Sort]]**: A sorting algorithm that divides an array's elements into several "buckets"

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
	return False
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
		if c not in countT or countS[c] != countT[c]:
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
- Compute prefix and postfix products
- $O(n)$ time and memory if creating an array for prefix and postfix

**Example**
Array = [1, 2, 3, 4]
|         | 1           | 2           | 3         | 4           |
| ------- | ----------- | ----------- | --------- | ----------- |
| Prefix  | 1           | 2           | 6         | 24          |
| Postfix | 24          | 24          | 12        | 4           |
| Output  | 24 (1 * 24) | 12 (1 * 12) | 8 (2 * 4) | 6 (6 * 1) |

- Can reduce memory if we use only output and track prefix/postfix within it
	- Every prefix is going to be stored in output + 1 index (index 0 stores 1)
	- Every postfix is going to be the product of whatever prefix is stored in the output - 1 index 
- $O(n)$ time and $O(1)$ memory

**Example**
|                | 1      | 2      | 3     | 4     |                     |
| -------------- | ------ | ------ | ----- | ----- | ------------------- |
| (start -> end) | **1**  |        |       |       | Pre = 1 * 1 = 1             |
|                | 1      | **1**  |       |       | Pre = 1 * 2 =2             |
|                | 1      | 1      | **2** |       | Pre = 2 * 3 = 6             |
|                | 1      | 1      | 2     | **6** | Pre = 6 * 4 = 24 (not used) |
| (end -> start) | 1      | 1      | 2     | **6** | Post = 1            |
|                | 1      | 1      | **8** | 6     | Post = 1 * 4 = 4            |
|                | 1      | **12** | 8     | 6     | Post = 4 * 3 = 12           |
| Output         | **24** | 12     | 8     | 6     | Post = 12 * 2 = 24           |

**Solution**
```Python
def productExceptSelf(nums):
	res = [1] * (len(nums))
	prefix = 1
	for i in range(len(nums)):
		res[i] = prefix
		prefix *= num[i]
	postfix = 1
	for i in range(len(nums) - 1, -1, -1):
		res[i] *= postfix
		postfix *= nums[i]
	return res
```

****

## Valid Sudoku
- Determine if a 9x9 Sudoku board is valid
- Requirements:
	- Each row must contain the digits 1-9 without repetition
	- Each column must contain the digits 1-9 without repetition
	- Each of the nine 3x3 sub-boxes of the grid must contain the digits 1-9 without repetition
	- Only the filled cells need to be validated according to the mentioned rules

### Method 1
- Iterate through each row using a [[HashSet]] (checks for duplicates)
- Iterate through each column using another [[HashSet]]
	- Adding an element and checking duplicates is $O(1)$
- For every 3x3 grid, we can use a [[HashSet]] and [[HashMap]]
	- Take the index of the row and column, then divide by 3 (floor result)
	- (4,4) = (1, 1) which is the index of the middle square
	- (8, 8) = (2, 2) which is the index of the bottom right square
	- Key for [[HashMap]] becomes ($\frac{row}{3}$,$\frac{col}{3}$)
	- Value for [[HashMap]] is a [[HashSet]] checking for duplicates
- Overall solution is $O(9^2)$ time and $O(9^2)$ memory

**Solution**
```Python
def isValidSudoku(board):
	cols = collections.defaultdict(set) # HashMap
	rows = collections.defaultdict(set)
	squares = collections.defaultdict(set) # key = (r/3, c/3)
	for r in range(9):
		for c in range(9):
			if board[r][c] == ".":
				continue
			if (board[r][c] in rows[r] or 
				board[r][c] in cols[c] or 
				board[r][c] in squares[(r // 3, c // 3)]): # Floor division
				return False
			cols[c].add(board[r][c])
			rows[r].add(board[r][c])
			squares[(r // 3, c // 3)].add(board[r][c])
	return True
```

****

## Encode and Decode Strings
- Design an algorithm to encode a list of strings to a string
- The encoded string is then sent over the network and is decoded back to the original list of strings
- Implement encode and decode
- Must be stateless, so you can't store an array of word lengths

### Method 1
- Put length of word and delimiter at the beginning of each string
	- "neat", "co#de" -> "4#neat5#co#de"
- $O(n)$ time for encode and decode where $n$ is the total number of characters

```Python
def encode(strs):
	res = ""
	for s in strs:
		res += str(len(s)) + "#" + s
	return res

def decode(s):
	res, i = [], 0
	while i < len(s):
		j = i
		while s[j] != "#":
			j += 1
		length = int(s[i:j]) # Tells how many following chars to read
		res.append(s[j + 1: j + 1 + length])
		i = j + 1 + length
	return res
```

****

## Longest Consecutive Sequence
- Given an unsorted array of integers, find the length of the longest consecutive sequence of integers
- Needs to run in $O(n)$ time
- `[100, 4, 200, 1, 3, 2]` -> `[1, 2, 3, 4]`

### Method 1
- Check for left neighbors on each number
- Convert array to a set
- Example: 100
	- Does array contain 99? No, let's get the length of the sequence
		- Count how many consecutive numbers come after our first number in the set (check if 101 exists)
	- Ok, so 4, not a start since 3 is in the set
	- 200? 199 not in set, so start sequence
		- 201? No, sequence is length 1
	- 1? No left neighbor, therefore start of sequence
		- 2? Yes
		- 3? Yes
		- 4? Yes
		- 5? No, sequence is length 4
- Time is $O(n)$ and memory is $O(n)$

**Solution**
```Python
def longestConsecutive(nums):
	numSet = set(nums)
	longest = 0
	for n in nums:
		# Check if its the start of a sequence
		if (n - 1) not in numSet:
			length = 0
			while (n + length) in numSet:
				length += 1
			longest = max(length, longest)
	return longest
```