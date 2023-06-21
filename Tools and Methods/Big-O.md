*Date: 2023-06-13 20:12*
*Type:* #lecture
*Class:* [[📌cs 311 MOC]]

*Categorizing algorithms*

## Classifying Algorithms

From [[Algorithm Analysis & Big-O]] we know the general basics of how Big-O works to classify the speed of algorithms. We learned that *only* the polynomial has any effect on the big-O, and that we can assign them groups like $$O(n), O(n^2), O(\log n), O(n\log n)$$
but how are we able to make this distinction? We can see it with our eyes, but we need **verifiable proof** that we are able to say that the function $2n+5$ is the same big-O as $n+1$. 

> [!def] 
> Let $f,g$ be functions over the natural numbers. We say that $f(n)\epsilon O(g(n))$ if there exists $c >0$ and $N$ such that whenever $n>N$, $f(n) \leq c*g(n)$

This is the basis definiton that allows us to make these group distinctions. 

$f(n)$ is the class function we are trying to put our algorithms function ($g(n)$) into

What this definition tells us is that if there are 2 functions ($f(n)$ and $g(n)$), then if the constant in front of $g(n)$ is greater than 0, then they can *at minimum* be equal to each other or $g(n)$ is greater. This basically says that because $g(n)$ has a constant in front of it that is non-zero, then it can be greater than *or equal to* the function $f(n)$, which means we can categorize them in the same bracket.

The second thing this definition is doing is letting us *normalize* our functions. If we take a function, say $2n^2+5\log n$, then the beginning of the function at the beginning of the numberline $(1,2,3,4,5,\dots)$ could have wild behaviors(log start out with negative numbers) compared to the numbers when it is closer to infinity. We can cut out those wild behaviors by having $N$ be the cutoff for when the function starts looking like **how its supposed to look like (curves of log/n^2)**, and comparing the functions on the basis that $n > N$.


> [!faq] Example
> Prove that $2n+1 \epsilon O(N)$

$f(n) = 2n+1$
$f(n) \leq 2n + n$
$f(n) \leq 3n$
$3n$ is in the form of $c*g(n)$ where $c=3$ and $N=1$, therefore $2n+1 \epsilon O(N)$

### Bigger O and little O

so we know that the big-O notation classifys an algorithm into a bracket, where the class function is *less than or equal to* the algorithms function.

There are more ways we can narrow down the time complexity of an algorithm, based off how much bigger (or smaller) the algorithms function is in comparison to the class function. 

> [!def]  Big-$\Omega$ 
> Big-$\Omega$: $f \epsilon \Omega(g)$ means $f$ is bounded *below* by $g$ 
> i.e. $\exists c>0, N s.t. \forall n \geq N$: $c * g(n) \leq f$

put in english: There *exists* some constant `c` and `N`, such that *for all* values of `n`, `n` must be greater than or equal to `N`. It means that algorithms function is **bounded** by the class function, meaning that the ***class function*** is greater than *or equal to* to the algorithms function. ($f(n)$ and $g(n)$ swap sides of inequality)

This is semi confusing until you understand why it exists: 
From our definition, we can capture a broad range of algorithms into a single class function, for example: $n\epsilon O(n^3)$, but we know that $n^3$ is much bigger than $n$ which is where Big-$\Omega$ comes in: $n \cancel \epsilon \Omega(n^3)$.

> [!def] Big-$\theta$
> Big-$\theta$: $f \epsilon \theta(g(n))$ if $f \epsilon O(g(n))$ & $f \epsilon \Omega(g(n))$
> Big-$\theta$ is used to say something is **tightly bound**

so for the above example with $n \epsilon O(n^3)$, thats how we fix the problem of having our original definition catch some of the wrong classes. 

> [!tip] Intuition
> Think about it like `if statements`:
> if you have the biggest term at the beginning of your catch, then you will never hit the lower conditions that refine your program. our first definition is the most general condition, so it will miss out on refining things to what they truly are ($n$ is not in the $n^3$ class but fits the condition), which is where Big-$\Omega$ and Little-O comes in, and Big-$\theta$ is the most refined version (what it actually is)

---

You can also switch the signs from $\leq$ to a $<$ to get the *little-O* of the function, or if you are switching for big-$\Omega$, the terminology is *little-$\omega$*. 

This is used to compare if the function is **a lot bigger than the class** -> big-O is checking if the function is greater than *or equal to the class*, little-O is checking if it is *strictly greater than the class function*.

Little-O:
$$
f(n) < c*g(n)
$$
Little-$\omega$:
$$
c*g(n) < f(n)
$$
---

> [!faq] Example
> Prove: for $a \geq 1, \log n \epsilon O(n^a)$

So, when we are solving problems based on the Big-O and such, these algorithms we are assuming that they *go to infinity*, meaning that we need to use calculus and limits to prove our definitions above (this is how calculus ties into computer science -> large numbers and indiscriminates over time)

> [!fact] Limits
> Fact: if $\lim_{ n \to \infty }{\frac{f(n)}{g(n)}} = 0$
> Then $f\epsilon o(g) \to f\epsilon O(g)$ 
> **Also**: if $\lim_{ n \to \infty }{\frac{f(n)}{g(n)}} = c>0$
> then $f \epsilon \theta(g) \to f\epsilon O(g) , f\epsilon \Omega(g)$

back to the example:

$\lim_{ n \to \infty }{\frac{\log n}{n^a}} = ?$

We can apply L'Hopital's rule (compare derivatives):

$\lim_{ n \to \infty }{\frac{\frac{1}{\ln(2)n}}{an^a-1}} = \lim_{ n \to \infty }{\frac{1}{an^a-1 \ln 2 n}}$

$n^a$ blows up the function as $n \to \infty$, therefore:
$= \lim_{ n \to \infty }{\frac{1}{an^a \ln 2}} = 0$

so $f$ is $O(g)$.

> [!faq] Example
> Prove: $3^n \cancel \epsilon O(n^5)$

This is an example where we can utilize the [[CS230 MOC|Proof skills]] we learned in cs230 to further aid in proving these example. *Just because the problem says to prove, that doesn't mean it has to be true*, as it could be asking us to disprove. Basically, just don't go with a direction because the problem tells you to, think about it yourself then make the judgement on which way you should go. With this, we can obviously tell that $n$ in the exponent will grow much faster than $n^5$, so we can head in the direction of proving it. 

We can do a proof by contradiction:

Assume that $3^n \epsilon O(n^5)$. Then there is some $N$ such that when $n \geq N, 3^n \leq cn^5$.

We can take the log of both sides:
$$
\log_{3}3^n \leq \log_{3}c*n^5
$$
then simplify:
$$
n \leq \log c + 5\log n
$$
we can rewrite to make it more obvious:
$$
n-5\log n \leq \log c
$$
$\log c$ is a constant, meanwhile the lefthand side goes to $\infty$, meaning that this statement is a contradiction, therefore our assumption is incorrect, and thus the original statement is true.