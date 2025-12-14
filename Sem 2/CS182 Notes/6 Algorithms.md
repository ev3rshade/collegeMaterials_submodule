Opened 12-12-2025 18:49

Status:

Tags: cs182

# 6 Algorithms
### 3.1 Algorithms
finiteness  |  definiteness  |  correctness  |  effectiveness  |  Generality

>An algorithm has an input & output

##### Definition 1 - ==ALGORITHM==
>An *algorithm* is set of instructions for solving a problem or performing a computation. An algorithm is finite, ==add more here==

**trace** - a specific manner in which an algorithm runs given a specific input

#### Searching Algorithms
##### ==Linear Search==
(sequential search)
**Time complexity:**  O(n)
**Space complexity:**  O(1)
- go through the list 1 by 1 until a match is found for the given input

##### ==Binary Search==
**Time Complexity:**  $O(log (n))$
**Space Complexity:**  $O(1)$ (iterative) | $O(log (n))$ (recursive)
- assumes the list is sorted
- go to the list middle, if the element being searched is greater, search the upper half. If the element being searched is less, then move to the lower half
- repeat the step above until an element is found in a subset of the list

#### Sorting Algorithms

##### ==Bubble Sort==
**Time Complexity:**  $O(n^2)$
**Space Complexity:**  $O(1)$
- starts with elements 1 and 2 of a list
- exchange of adjacent elements if they are in the wrong order until they are all sorted in the right order
- number of comparisons in bubble sort is constant because *"it will always compare each value with each of the following values even if the array is already properly sorted"* - (stack exchange answer)

##### ==Insertion Sort==
**Time Complexity:**  $O(n^2)$
**Space Complexity:**  $O(1)$
- starts with second element of the list
- compares an element with the ones preceding it (starting with the first element in the list) until it is in the right order in the subset of elements up to its position


#### ==Greedy Algorithms==
- Algorithms that makes the "best" choice at a given step
##### The Optimization Problem
>solution to a problem that minimizes of maximizes the value of some parameter
###### Example: The cashier's algorithm
Algorithm make change for a given amount of cash
- choose big coins until you can't
- "BEST" CHOICE at a given moment is biggest coin that can be chosen

The optimization in this problem is handing a customer the least amount of coins possible

==prove that the cashier's algorithm always makes changes uses the fewest coins possible==

#### The Halting Problem
- Alan turing [[13 future note]]

### 3.2 The Growth of Functions

```Lec6
The time required to solve a problem is determined by
- Number o operations executed (input size)
- Speed of hardware and software (constant multiplier)
```

``` Lec6
Qualities to analyze the complexity of an algorithm
- Number of iterations in a loop
```
#### Big-$O$ Notation
``` Lec6
represents the number of operations executed (n)
operations like addition and division are assumed to take the same amount of time
```


##### Definition 1
>Let $f$ and $g$ be functions from the set of integers or the set of real numbers to the set of real numbers. We say that $f(x)$ is $O(g(x))$ if there are constants $C$ and $k$ such that
>	$|f(x) \leq C|g(x)|$
>whenever $x > k$. \[This is read as "$f(x)$ is big-oh of $g(x)$"]
- only need ONE PAIR of **witnesses** to the relationship (one pair of constants C and k)
	- Useful strat for finding a pair of witnesses
		1. first find k
		2. find a C
		3. ![[Screenshot 2025-02-16 135651.png]] Example: $x^2 + 2x + 1 \leq 4(x^2)$  when  $x > 1$
			$f(x) = x^2 + 2x + 1, g(x) = x^2, C = 4, k = 1$
	- HOW TO SHOW $n^2$ is not $O(n)$
		- Proof by contradiction (no C and k for all n)

###### Theorem 1
>Let $f(x) = a_nx^{n} + a_{n - 1}x^{n-1} + ... + a_1x^1 + a_0$, where $a_0, ... , a_{n}$ are real numbers. Then $f(x)$ is $O(x^n)$

##### Theorem 2
>Suppose that $f_1(x)$ is $O(g_1(x))$ and that $f_2(x)$ is $O(g_2(x))$. Then $( f_1 + f_2)(x)$ is $O(g(x))$, where $g(x) = (max(|g_1(x)|, |g_2(x)|)$ for all $x$.

##### Common Growth Functions
| Typle       | Big-O Notation | Notes             |
| ----------- | -------------- | ----------------- |
| constant    | $O(1)$         |                   |
| logarithmic | $O(log (n))$   |                   |
| linear      | $O(n)$         |                   |
| quadratic   | $O(n^2)$       |                   |
| polynomial  | $O(n^k)$       | $k$ is a constant |
| exponential | $O(c^n)$       | $c$ is a constant |
| factorial   | $O(n!)$        |                   |
##### Important big-O relationships
| Function                          | Relationship                               | Notes                   |
| --------------------------------- | ------------------------------------------ | ----------------------- |
| $log_2 (n)$ and $n$               | $log_2(n) = O(n)$                          | The reverse is not true |
| $log_2(n)$ and $\sqrt{n}$         | $log_2(n) = O(\sqrt{n})$                   | The reverse is not true |
| $log_2(n)$ and $log_b(n)$, $b> 1$ | $log_2(n)$ and $log_b(n)$ both $O(log(n))$ |                         |
| $log_2(n)$ and $n^{\frac{1}{8}}$  | $log_2(n) = O(n^{\frac{1}{8}})$            | The reverse is not true |
| $(log_2(n))^4$ and $\sqrt{n}$     | $(log_2(n))^4 = O(\sqrt{n})$               | The reverse is not true |
| $nlog(n)$ and $n^2$               | $nlog(n) = O(n^2)$                         | Reverse is not true     |
### 3.3 The complexity of functions
##### Time Complexity
- Time required to solve a problem of a particular size
- Use Big-O to analyze
##### Space Complexity
- Computer memory required to solve a given problem

###### Worst-Case Complexity
###### Average-Case Complexity

==PRACTICE OPPORTUNITY== - analysis of complexity for matrix tmultiplication