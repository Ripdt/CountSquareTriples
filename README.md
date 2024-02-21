
# Approach
For each value $a$ where $1 <= a <= n$, the algorithm has to square it up and sum with each value between $a + 1$ and $n$. When the sum results in a value that it's a perfect square less or equal $n$, the counter increments itself by $2$, because it found two new square triplets.

# Complexity
- Time complexity: $O(n²)$

# Code
```

class Solution {
public:
  int countTriples(int a, int top) {
    int triples = 0;
    for (int b = a + 1; b < top; b++) {
      const double product = a * a + b * b;
      const int c = static_cast<int>(sqrt(product));
      if (c <= top && c * c == product) {
        triples += 2;
      }
    }
    return triples;
  }

  int countTriples(int n) {
    int triples = 0;
    for (int i = 1; i < n; i++) {
      triples += countTriples(i, n);
    }
    return triples;
  }
};
```
