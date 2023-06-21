Created: 2023-06-11 12:43
Home: [[🏠 Coding Interviews]]

This pattern describes an interesting approach to deal with problems involving arrays containing numbers in a given range. The Cyclic Sort pattern iterates over the array one number at a time, and if the current number you are iterating is not at the correct index, you swap it with the number at its correct index. You could try placing the number in its correct index, but this will produce a complexity of $O(n^2)$ which is not optimal, hence the Cyclic Sort pattern.
![cyclicSort](https://hackernoon.imgix.net/images/G9YRlqC9joZNTWsi1ul7tRkO6tv1-t8i13wdp.jpg)

### Identifying
- They will be problems involving a sorted array with numbers in a given range
- If they problem asks you to find the missing/duplicate/smallest number in a sorted/rotated array

### Common Problems
- Find the missing number (easy)
- Find the smallest missing positive number (medium)