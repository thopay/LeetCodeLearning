Created: 2023-10-22 13:19
Home: [[🏠 Coding Interviews]]

### Overview
- Worst case runtime is $O(n^2)$
- Often the best practical choice for sorting because it's very efficient on average
- Expected running time is $O(n\log(n))$

### Divide
- $A[p:r]$ is partitioned into $A[p:q-1]$ (**low side**) and $A[q+1:r]$ (**high side**) such that each element in the low side of the partition is less than or equal to the **pivot** $A[q]$
- Index $q$ is computed as part of the partitioning procedure

### Conquer
- Call QuickSort on each of the subarrays $A[p:q-1]$ and $A[q+1:r]$

### Combine
- Combine by doing nothing since the two subarrays are already sorted
- All elements in $A[p:q-1]$ are sorted and less than or equal to $A[q]$, and all elements in $A[q+1:r]$ are sorted and greater than or equal to $A[q]$

### Partitioning
- Pick a pivot and iterate through
![[IMG_8656.jpeg]]
