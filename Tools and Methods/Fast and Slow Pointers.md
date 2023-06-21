Created: 2023-06-11 12:01
Home: [[🏠 Coding Interviews]]

The Fast and Slow pointer approach, also known as the **Hare & Tortoise algorithm**, is a pointer algorithm that uses two pointers which move through the array (or sequence/linked list) at different speeds. This approach is quite useful when dealing with cyclic linked lists or arrays. By moving at different speeds (say, in a cyclic linked list), the algorithm proves that the two pointers are bound to meet. The fast pointer should catch the slow pointer once both the pointers are in a cyclic loop.

![fastandslow](https://hackernoon.imgix.net/images/G9YRlqC9joZNTWsi1ul7tRkO6tv1-suft3wtu.jpg)

### Identifying
- The problem will deal with a loop in a linked list or array
- When you need to know the position of a certain element or the overall length of the linked list

### When to use this over Two Pointer?
- There are some cases where you shouldn't use the Two Pointer approach such as
	- In a singly linked list where you can't move in a backwards direction
	- When you're trying to determine if a linked list is a palindrome

### Common Problems
- Linked list cycle (easy)
- Palindrome linked list (medium)
- Cycle in a circular array (hard)