Created: 2023-06-11 12:51
Home: [[🏠 Coding Interviews]]

This pattern reverses one node at a time starting with one variable (current) pointing to the head of the linked list, and one variable (previous) will point to the previous node that you have processed. In a lock-step manner, you will reverse the current node by pointing it to the previous before moving on to the next node. Also, you will update the variable "previous" to always point to the previous node that you have processed.

![inPlaceReversal](https://hackernoon.imgix.net/images/G9YRlqC9joZNTWsi1ul7tRkO6tv1-gekl3wfd.jpg)

### Identifying
- If you're asked to reverse a linked list without using extra memory

### Common Problems
- Reverse a sub-list (medium)
- Reverse every K-element sub-list (medium)