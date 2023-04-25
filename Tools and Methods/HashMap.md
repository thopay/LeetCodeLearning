Created: 2023-04-25 09:53
Home: [[🏠 Coding Interviews]]

A HashMap is a data structure that allows you to store and retrieve values based on a corresponding key. It is a part of the Java Collections Framework and implements the Map interface. HashMap uses a technique called hashing, which allows it to achieve constant-time complexity for most of its operations, such as inserting, retrieving, and deleting key-value pairs.

In Python, the equivalent of a HashMap is a Dictionary. Dictionaries are built-in data structures that use key-value pairs to store and retrieve data efficiently.

Here's a brief example of how to use HashMap in Java:

```java
import java.util.HashMap;

public class HashMapExample {
    public static void main(String[] args) {
        // Create a HashMap object
        HashMap<String, Integer> map = new HashMap<>();

        // Add key-value pairs
        map.put("Alice", 30);
        map.put("Bob", 25);
        map.put("Charlie", 35);

        // Retrieve the value for a specific key
        int aliceAge = map.get("Alice");
        System.out.println("Alice's age: " + aliceAge);

        // Remove a key-value pair
        map.remove("Bob");

        // Check if the HashMap contains a key
        boolean hasCharlie = map.containsKey("Charlie");
        System.out.println("Is Charlie in the map? " + hasCharlie);
    }
}
```

And here's an example of how to use a Dictionary in Python:

```python
# Create a dictionary object
map = {}

# Add key-value pairs
map["Alice"] = 30
map["Bob"] = 25
map["Charlie"] = 35

# Retrieve the value for a specific key
alice_age = map["Alice"]
print("Alice's age:", alice_age)

# Remove a key-value pair
del map["Bob"]

# Check if the dictionary contains a key
has_charlie = "Charlie" in map
print("Is Charlie in the map?", has_charlie)
```