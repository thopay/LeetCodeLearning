Created: 2024-01-31 20:30
Home: [[🏠 Coding Interviews]]

# Chapter 1 - Introduction to Algorithm Design

**Ideas**
- There is a fundamental difference between algorithms, procedures that always produce a correct result, and heuristics, which may usually do a good job but provide no guarantee of correctness
- Mathematical induction is usually the right way to verify the correctness of a recursive or incremental insertion algorithm

**Counterexample Properties**
- Verifiability -> must be able to (1) calculate what answer your algorithm will give and (2) display a better answer so as to prove the algorithm didn't find it
- Simplicity -> all unnecessary details are stripped away and make it clear why the proposed algorithm fails

**Counterexample Development Techniques**
- Think small
- Think exhaustively
- Hunt for the weakness
- Go for a tie
- Seek extremes

**Induction and Recursion**
- Recursion **is** mathematical induction in action

### Common structures

**Permutations**
- arrangements, or orderings, of items
- likely the object in question whenever your problem seeks an "arrangement," "tour," "ordering," or "sequence"

**Subsets**
- represent selections from a set of items
- order does not matter in subsets, the way it does with permutations
- likely the object in question whenever your problem seeks a "cluster," "collection," "committee," "group," "packaging," or "selection"

**Trees**
- represent hierarchical relationships between items
- likely the object in question whenever your problem seeks a "hierarchy," "dominance relationship," "ancestor/descendant relationship," or "taxonomy"

**Graphs**
- represent relationships between arbitrary pairs of objects
- likely the object in question whenever you seek a "network," "circuit," "web," or "relationship"

**Points**
- define locations in some geometric space
- likely the object in question whenever your problems work on "sites," "positions," "data records," or "locations"

**Polygons**
- define regions in some geometric space
- likely the object in question whenever you are working on "shapes," "regions," "configurations," or "boundaries"

**Strings**
- represent sequences of characters, or patterns
- likely the object in question whenever you are dealing with "text," "characters," "patterns," or "labels"

# Chapter 2 - Algorithm Analysis

![[Pasted image 20240131220125.png]]

• $f(n) = O(g(n))$ means $c · g(n)$ is an upper bound on $f(n)$. Thus, there exists some constant $c$ such that $f (n) ≤ c · g(n)$ for every large enough $n$ (that is, for all $n ≥ n_{0}$, for some constant $n_{0}$).

• $f(n) = Ω(g(n))$ means $c·g(n)$ is a lower bound on $f(n)$. Thus, there exists some constant $c$ such that $f(n) ≥ c · g(n)$ for all $n ≥ n_{0}$.

• $f(n) = Θ(g(n))$ means $c_{1} · g(n)$ is an upper bound on $f(n)$ and $c_{2} · g(n)$ is a lower bound on $f(n)$, for all $n ≥ n_{0}$. Thus, there exist constants $c_{1}$ and $c_{2}$ such that $f(n) ≤ c1 ·g(n)$ and $f(n) ≥ c2 ·g(n)$ for all $n ≥ n_{0}$. This means that g(n) provides a nice, tight bound on $f(n)$.

### Summations

$$
\sum_{i=1}^{n}f(i)=f(1)+f(2)+\dots+f(n)
$$
$$
\sum_{i=1}^{n}1=n
$$
$$
\sum_{i=1}^{n}i=\sum_{i=1}^{k}(i+(2k-i+1))=k(2k+1)=\frac{n(n+1)}{2}
$$
**Sum of a power of integers**
$$
S(n,p)=\sum_{i=1}^{n}i^{p}=\Theta(n^{p+1})
$$
**Sum of geometric progression**
$$
G(n,a)=\sum_{i=0}^{n}a^{i}=\frac{a^{n+1}-1}{a-1}
$$

### Logarithms

**Properties**
- $b^{x}=y \implies x=\log_{b }y$
- $b$ is the base of the logarithm
- $\exp(\ln x)=x$ and $\ln(\exp x)=x$
- $\log_{a}(xy)=\log_{a}(x)+\log_{a}(y)$
- Log conversion: $\log_{a}b=\frac{\log_{c}b}{\log_{c}a}$
- The base of the logarithm has no real impact on the growth rate
- Logarithms cut any function down to size since the logarithm of any polynomial function is $O(\lg n)$ because $\log_{a}n^{b}=b*\log_{a}n$

**Important Bases**
- Base $b=2$ is the **binary logarithm** and arises whenever repeated halving or doubling occurs
- Base $b=e$ is the **natural logarithm** and is usually denoted in $\ln x$
	- The inverse of $\ln x$ is the exponential function $\exp(x)=e^{x}$
- Base $b=10$ is the **common logarithm** and is usually denoted as $\log x$

### Esoteric Functions

**Inverse Ackermann's Function**
- $f(n)=\alpha(n)$
- The slowest growing complexity function besides constant
- $\alpha (n)$ eventually gets to infinity as $n\to \infty$ 
- The value of $\alpha(n)$ is smaller than 5 for any value of $n$ that can be written in this physical universe

**Log Log Function**
- $f(n)=\log \log n$
- Might arise when doing a binary search on a sorted array of only $\lg n$ items

**Epsilon Function**
- $f(n)=n^{1+\epsilon}$
- Epsilon ($\epsilon$) is a symbol to denote a constant that can be arbitrarily small but never quite goes away

### Limits and Dominance Relations

- We say that $f(n)$ dominates $g(n)$ if $\lim_{ n \to \infty } \frac{g(n)}{f(n)}=0$

$$
n \gg c^{n} \gg n^{3}\gg n^{2} \gg n^{1+\epsilon}\gg n\log n\gg n\gg \sqrt{ n }\gg \log^{2}n\gg \log n\gg \log n /\log \log n\gg \log \log n\gg \alpha (n)\gg 1
$$

# Chapter 3 - Data Structures

**Contiguous versus Linked**
- Contiguously allocated structures are composed of single slabs of memory and include:
	- arrays
	- matrices
	- heaps
	- hash tables
- Linked data structures are composed of distinct chunks of memory bound together by **pointers** and include:
	- lists
	- trees
	- graph adjacency lists

**Arrays**
- Structures of fixed-size data records such that each element can be efficiently located by its index or address
- Advantages:
	- **Constant-time access given the index** -> because the index of each element maps directly to a particular memory address, we can access arbitrary data items instantly provided we know the index
	- **Space efficiency** -> arrays consist purely of data, so no space is wasted with links or other formatting information
	- **Memory locality** -> physical continuity between successive data accesses helps exploit the high-speed **cache memory** on modern computer architectures
- Disadvantages:
	- Cannot adjust their size in the middle of a program's execution (unless using **dynamic arrays**)

**Dynamic Arrays**
- Suppose we start with an array of size 1, and double its size from $m$ to $2m$ whenever we run out of space
- This doubling process allocates a new contiguous array of size $2m$, copies the contents of the old array to the lower half of the new one, and then returns the space used by the old array to the storage allocation system
- The total work (amortized) of managing the dynamic array is the same $O(n)$ as a single array 
- Disadvantage:
	- Each insertion takes constant time **in the worst case**

**Pointers**
- Represent the address of a location in memory

**Canonicalization**
- Reducing complicated objects to a standard (i.e. canonical) form
- E.g. string transformations like sorting the string characters, converting to lower case, or stemming (removing word suffixes)

**Compaction (Fingerprinting)**
- Represent large objets by small hash codes
- E.g. when sorting books by content use the first 100 characters, sort them, and hash