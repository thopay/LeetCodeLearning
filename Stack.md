Created: 2023-07-26 15:14
Home: [[🏠 Coding Interviews]]

****

## Valid Parentheses
- Given a string containing just the characters `(){}[]`, determine if the input string is valid

**Solution**
```Python
def isValid(s):
	stack = []
	for c in s:
		if c == '(':
			stack.append('(')
		elif c == '[':
			stack.append('[')
		elif c == '{':
			stack.append('{')
		elif c == ')':
			if len(stack) == 0 or stack.pop() != '(':
				return False
		elif c == ']':
			if len(stack) == 0 or stack.pop() != '[':
				return False
		elif c == '}':
			if len(stack) == 0 or stack.pop() != '{':
				return False
	if len(stack) != 0:
		return False
	return True
```

****

## Min Stack
- Design a stack that supports push, pop, top, and retrieving the minimum element in constant time
- Each function must have a time complexity of `O(1)`

### Method 1 - Stack of Value / Minimum Pairs
- An important **invariant** of a stack is that when a new number `x` is placed on the stack, the numbers b