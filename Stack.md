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
- An important **invariant** of a stack is that when a new number `x` is placed on the stack, the numbers below it will not change for as long as number `x` remains on the stack
- Whenever number `x` is at the top of the stack, the minimum will always be the same, as it's simply the minimum out of `x` and all the numbers below it
- Whenever we add a new number to the stack, we need to decide whether the minimum at that point is the new number itself, or whether it's the minimum before

```ad-tip
An **invariant** is something that is always true or consistent.
```

```Python
class MinStack:
	stack = []

	def __init__(self):
		self.stack = []

	def push(self, val: int) -> None:
		if len(self.stack) == 0:
			self.stack.append([val, val])
		else:
			self.stack.append([val, min(val, self.getMin())])

	def pop(self) -> None:
		self.stack.pop()

	def top(self) -> int:
		return self.stack[-1][0]

	def getMin(self) -> int:
		return self.stack[-1][1]
```

****

## Evaluate Reverse Polish Notation (Post-Fix)
- You are given an array of strings `tokens` that represents an arithmetic expression in post-fix
- Evaluate the expression and return an integer that represents the value of the expression

### Method 1
- Create a stack
- For each token in tokens, if the token is a number append it to the stack, when an expression is detected, pop twice from the stack and perform the operation, pushing the result back onto the stack

```Python
def evalRPN(tokens):
	stack = []
	for token in tokens:
		if token not in "+-*/":
			stack.append(int(token))
		else:
			b, a = stack.pop(), stack.pop()
			if token == '+':
				stack.append(a+b)
			elif token == '-':
				stack.append(a-b)
			elif token == '*':
				stack.append(a*b)
			elif token == '/':
				stack.append(int(a/b))
	return stack[0]
```

****
