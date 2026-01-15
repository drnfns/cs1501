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
