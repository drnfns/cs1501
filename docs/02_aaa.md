# asymptotic algorithm analysis

consider the 3-sum problem. given a set of arbitrary integers, we need
to find out how many _distinct_ triples `(a, b, c)` that sums to zero.
for example, given: `[5, -1, 2, -3, -2, 1, 0]`, the output should be 4
triples.

## brute-force solution

consider this solution; it works by enumerating all the distinct triples
and checking their sums. if it equal to zero, we increase the answer
counter by 1.

```java
public static int count(int[] a) {
  int n = a.length;
  int cnt = 0;
  for (int i = 0; i < n; i++) {
    for (int j = i+1; j < n; j++) {
      for (int k = j+1; k < n; k++) {
        if (a[i] + a[j] + a[k] == 0) cnt++;
      }
    }
  }
  return cnt;
}
```

however, we would miss some triple by doing so.

- Would we miss a triple if we do so?
- Is it correct to start the j loop from 0? Why?
- note: distinct based on position, not on value
- Would that solution be correct if the input integers are not unique?

### analysis
the brute-force algorithm contains 3 `for` loops. for each loop, we assign them a cost and a frequency.

for the ambient program, we assign the cost as $t_0$ and the frequency as $f_0 := 1$.

for the outer-most loop, the cost would be $t_1$, and the frequency would be $f_1 := n$, since this loop would be ran $n$ times by its parent.

for the next nested loop, we say the cost is $t_2$, and the frequency would be $f_2 := (n-1) + (n-2) + (n-3) + ... + 1 = \frac{n^2}{2}-\frac{n}{2}$, since it would be starting based on the position of its parent loop.

for the final nested loop, we assign the cost as $t_3$, and the frequency would be the combination $f_3 := \frac{n!}{(n-3)! \cdot 3!}$.

for the inner-most code, the cost would be $t_4$ and its frequency would be $f_4 := x$ where x is the number of triples that sum to 0 in the input array. $0 \le x \le C(n, 3)$ where the $C$ is the combination function.

to calculate the grand total, we find the sum of all the products of the frequency with its cost: (rewrite this so it doesnt sound awkward)

$$
  \sum_{i=0}^{4} f_i \cdot t_i = 
$$

if $x = 0$, then it is the best case runtime.

if $x = C(n, 3)$, then it is the worst case runtime.
