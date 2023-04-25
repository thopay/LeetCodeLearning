Created: 2023-04-25 09:50
Home: [[🏠 Coding Interviews]]

A HashSet is a data structure that represents a collection of distinct elements in an unordered manner. It is a part of the Java Collections Framework and is implemented by the `java.util.HashSet` class, which uses a hash table for storage.

Main characteristics of a HashSet are:

1. No duplicates: It does not allow duplicate elements, meaning that each element in the HashSet must be unique. If you try to insert a duplicate element, the HashSet will simply ignore the new insertion.

2. Unordered: The elements in a HashSet are not stored in any specific order, and the order may change over time as elements are added or removed.

3. Null values: HashSet allows a single null value as an element.

4. Time complexity: The primary operations (add, remove, and contains) have an average time complexity of O(1) due to the use of hashing. However, in the worst case (when there are hash collisions), the complexity can degrade to O(n).

5. Not synchronized: HashSet is not synchronized, meaning it is not thread-safe. If you need a synchronized version, you can use `Collections.synchronizedSet()` to wrap around it.

A HashSet is particularly useful when you need to store unique elements without caring about their order and want to perform quick insertion, deletion, and search operations. It is often used in problems where you need to eliminate duplicates or check if an element is already present in a collection.

Here's an example of using a HashSet in Java:

```java
import java.util.HashSet;

public class HashSetExample {
    public static void main(String[] args) {
        HashSet<String> set = new HashSet<>();

        // Adding elements
        set.add("Apple");
        set.add("Banana");
        set.add("Cherry");

        // Attempting to add a duplicate element
        set.add("Apple");

        // Checking if an element exists
        if (set.contains("Banana")) {
            System.out.println("Banana is in the set");
        } else {
            System.out.println("Banana is not in the set");
        }

        // Removing an element
        set.remove("Cherry");

        // Iterating through the elements
        for (String item : set) {
            System.out.println(item);
        }
    }
}
```

In this example, we create a HashSet of strings and perform various operations like adding elements, checking for duplicates, searching for an element, removing an element, and iterating through the set. Note that the output order of the elements may be different from the order in which they were inserted, as HashSet does not maintain any specific order.

Here's an example of using a HashSet in Python:

```python
# In Python, HashSet is called Set
my_set = set()

# Adding elements
my_set.add("Apple")
my_set.add("Banana")
my_set.add("Cherry")

# Attempting to add a duplicate element
my_set.add("Apple")

# Checking if an element exists
if "Banana" in my_set:
    print("Banana is in the set")
else:
    print("Banana is not in the set")

# Removing an element
my_set.remove("Cherry")

# Iterating through the elements
for item in my_set:
    print(item)
```

In this Python example, we use the built-in `set()` data structure, which has similar characteristics to Java's HashSet. We perform the same operations as in the Java example, and again, the output order of the elements may be different from the order in which they were inserted.