Created: 2024-01-05 21:20
Home: [[🏠 Coding Interviews]]

# Arrays

### Terms
- Subarray -> a range of **contiguous** values within an array
- Subsequence -> a sequence that can be derived from another sequence by deleting some or no elements (not changing the order)

### Time Complexity
| Operation             | Big-O     | Notes                                                                                                |
| --------------------- | --------- | ---------------------------------------------------------------------------------------------------- |
| Access                | O(1)      |                                                                                                      |
| Search                | O(n)      |                                                                                                      |
| Search (Sorted)       | O(log(n)) |                                                                                                      |
| Insert                | O(n)      | Insertion would require shifting all the subsequent elements to the right by one and that takes O(n) |
| Insert (at end)       | O(1)      |                                                                                                      |
| Remove                | O(n)      | See logic for insert                                                                                 |
| Remove (at end)       | O(1)      |                                                                                                      |
| Slicing/Concatenating | O(n)      |                                                                                                      |

### Edge Cases
- Empty array
- Array with 1 or 2 elements
- Array with repeated/duplicated elements


### Relevant Patterns/Techniques
- [[Sliding Window]]
- [[Two Pointers or Iterators]]
- Traversal from the right
- Sorting
- Pre-computation (e.g. product of array except self)
- Index as hash key
- Array traversal more than once

# Strings

### Time Complexity
| Operation                                      | Big-O    |
| ---------------------------------------------- | -------- |
| Access                                         | O(1)     |
| Search                                         | O(n)     |
| Insert                                         | O(n)     |
| Remove                                         | O(n)     |
| Find substring                                 | O(n.m)   |
| Concatenating                                  | O(n + m) |
| Slice                                          | O(m)     |
| Split (by token)                               | O(n + m) |
| Strip (remove leading and trailing whitespace) | O(n)     |

### Edge Cases
- Empty string
- String with 1 or 2 characters
- String with repeated characters
- Strings with only distinct characters

### Relevant Patterns/Techniques
- Counting characters
	- Note: the space required for a counter of a string of latin characters is O(1) not O(n) since the upper bound is a fixed constant of 26
- String of unique characters
- Anagram
	- Sorting strings takes O(n.log(n)) time and O(log(n)) space
	- Map each characters to a prime number and multiply together takes O(n) time and O(1) space
	- Frequency counting takes O(n) time and O(1) space
- Palindrome
	- Reverse the string
	- Two pointers at start and end