Created: 2023-04-25 23:20
Home: [[🏠 Coding Interviews]]

Bucket Sort is a non-comparison based sorting algorithm that works by distributing the elements of an array into a number of "buckets". Each bucket is then sorted individually, either using a different sorting algorithm or by recursively applying the bucket sorting algorithm. Finally, the sorted values from the buckets are combined back into the original array to produce the sorted output.

Bucket Sort is mainly useful when the input elements are uniformly distributed over a range. It has an average time complexity of $O(n+k)$, where $n$ is the number of elements in the input array, and $k$ is the number of buckets.

Here's a high-level explanation of how Bucket Sort works:

1. Determine the range of the input elements and calculate the number of buckets needed.
2. Create an empty array of buckets.
3. Iterate through the input array and place each element into the appropriate bucket.
4. Sort the elements in each bucket using a suitable sorting algorithm (for example, insertion sort) or apply bucket sort recursively.
5. Concatenate the sorted elements from each bucket to form the sorted output.

Here's an example of Bucket Sort in Python:

```python
def insertion_sort(arr):
    for i in range(1, len(arr)):
        key = arr[i]
        j = i - 1
		while j >= 0 and key < arr[j]:
            arr[j + 1] = arr[j]
            j -= 1
        arr[j + 1] = key
    return arr

def bucket_sort(arr):
    # Determine the range and create buckets
    max_val = max(arr)
    min_val = min(arr)
    bucket_range = (max_val - min_val) / len(arr)
    temp = []

    for _ in range(len(arr)):
        temp.append([])
    
    # Place array elements into buckets
    for i in range(len(arr)):
        index = int((arr[i] - min_val) // bucket_range)
        if index != len(arr):
            temp[index].append(arr[i])
        else:
            temp[-1].append(arr[i])

    # Sort each bucket and concatenate
    sorted_arr = []
    for i in range(len(temp)):
        if temp[i]:
            insertion_sort(temp[i])
            sorted_arr.extend(temp[i])

    return sorted_arr

arr = [30, 40, 10, 80, 5, 12, 70, 50]
print("Original Array:", arr)
sorted_arr = bucket_sort(arr)
print("Sorted Array:", sorted_arr)
```

In this example, we use insertion sort as the sorting algorithm for each bucket. The input array is first divided into buckets based on the range of the input elements. Then, each bucket is individually sorted, and finally, the sorted elements from all buckets are combined to produce the sorted output.

Keep in mind that the performance of Bucket Sort depends on the distribution of the input elements and the sorting algorithm used for the individual buckets. If the elements are uniformly distributed, Bucket Sort can be very efficient, but if the distribution is skewed, it may perform poorly.