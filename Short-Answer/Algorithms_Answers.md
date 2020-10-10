#### Please add your answers to the ***Analysis of  Algorithms*** exercises here.

## Exercise I

a)  a = 0 // O(1)
    while (a < n * n * n): 
      a = a + n * n // 0, (0 + n^2), (0 + 2*n^2), (0 + 3*n^2)... (0 + n*n^2) => n times => O(n)

O(1) + O(n) = O(1 + n) => O(n) (linear)

b)  sum = 0 // O(1)
    for i in range(n): 
      j = 1 // O(n)
      while j < n:
        j *= 2 // 1, 2, 4, 8, 16 => log2 n  = log n/log 2 => O(log n)
        sum += 1 // O(log n)
      // O(log n) + O(log n) = O(2 * log n) => O(log n)

O(1) + O(n)*O(log n) => O(n log n) (linearithmic) 

c)  def bunnyEars(bunnies):
      if bunnies == 0:
        return 0 // O(1)

      return 2 + bunnyEars(bunnies-1) // 2 + n-1, 2 + n-2, 2 + n-3 ... 2 + n - n => n times => O(n)

O(1) + O(n) => O(n) linear

## Exercise II

### Problems

- E is number of dropped + broken eggs to test.
- E is unlimited (plenty of eggs) but E should be minimized in the solution.
- N is number of floors in a n-story building.
- N = 1 is the base case.
- * F is the floor that any egg at this floor or the above floors will be broken if it is dropped.
- Value F is determined with E is minimized.

### Solution Analysis

1. N = 1:

F is 1 and the minimum number of attempt (number of dropped + broken eggs) or E = 1. O(1)

2. N > 1:

Linear Search:

Start dropping an egg from 1th Floor and one floor at a time until the egg is broken. The worse case scenario is the broken egg at the top floor which number of dropping attempt is N times (E = N). Regarding time complexity, the number of operation is O(n).

According to the problems to solve this solution is not suitable because the requirement is to minimized dropped + broken eggs.

Binary Search:

We start doing an egg drop from the middle floor called (M) in range of N (M = N//2). If the egg is broken at the middle floor of the range (M) then F should be in the below floors with range of the bottom to (M - 1). If the egg is not broken at the middle floor then F should be the above floors with range of M + 1 to the top. We can continue this process repeatly by using recursion or iterative function. The number of attempts (E) in the worse case senario of this solution is now equal to log2 N. Regarding time complexity, the number of operation is O(log2 n) => O(log n)
