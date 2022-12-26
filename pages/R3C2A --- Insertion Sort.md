- #+BEGIN_PINNED
  Cormen, T. H., Leiserson, C. E., Rivest, R. L., & Stein, C. (2022). Introduction to algorithms (4th ed.). The MIT Press. c2.1
  #+END_PINNED
- keywords: ==Insertion Sort== ==Loop Invariant==
-
- ## Problem
	- **Input**: A sequence of $n$ numbsers $\langle a_1,a_2,\ldots,a_n \rangle$
	- **Output**: A permutaion $\langle a'_1,a'_2,\ldots,a'_n \rangle$ of the input sequence such that $$a'_1 < a'_2 < \ldots < a'_n$$
- ## Algorithm
	- `INSERTION-SORT(A, n)`
		- ```text
		    for i = 2 to n:
		    	key = A[i]
		      // Insert A[i] into the sorted subarray A[1:i-1]
		      j = i-1
		      while j > 0 and a[j] > key:
		      	a[j+1] = a[j]
		          j = j - 1
		      a[j+1] = key
		  ```
- ## Loop Invariant
	- The property of **_loop invariant_**:
		- At the start of each iteration of the `for` loop of lines 1-8, the subarray $A[1: i-1]$ consists of the elements originally in $A[1:i-1]$, but in sorted order.
	- Things need to show when using *loop invariant*:
		- **Initialization**: It is true prior to the first iteration of the loop.
		- **Maintenance**: If it is true before an iteration of the loop, it remains true before the next iteration.
		- **Termination**: The loop terminates, and when it terminates, the invariant gives us a useful propery that helps show that the algorithm is correct.
	- Thses three properties in insertion-sort:
		- ==*Initialization*==: Before the first loop, when $i = 2$. The subarray $A[1:i-1]$ consist of only one element, so it is sorted.
		- ==*Maintenance*==: The body of the `for` loop, move the values in  $A[i-1]$, $A[i-2]$, $A[i-3]$ and so on by one position to the right until it find the proper position for $A[i]$, at which point it insert the value of $A[i]$, but in sorted order.
		- ==*Termination*==: The loop variable $i$ starts at 2 and increases by 1 in each iteration. Once $i$'s value exceeds $n$, the loop terminates. At this moment, $i = n+1$. Substituting $n+1$ for $i$ in $A[1:i-1]$ yields that the subarray $A[1:n]$ consist of the elements originally in $A[1:n]$, but in sorted order. Hence, the algorithm is correct.
- [[RE3C2A1 --- 练习2]]
- [[RE3C2A2 --- 练习3]]
- [[RE3C2A3 --- 练习4]]
- [[RE3C2A4 --- 练习5]]
-