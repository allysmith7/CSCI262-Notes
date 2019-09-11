# Sorting Methods

## Selection Sort

- input of a list of elements (usually integers)
- returns the list in sorted order
- algorithm is O(n^2^), actually has  $\sum_{i=0}^n\frac{n(n+1)}{2}$ operations
    - find the minimum element in the list
    - swap it with the first value in the list (needs a  `temp` variable)
    - Sort the sublist following the first element

**Big O notation only matters to the highest degree** e.g. $O(o^3+n \cdot log(n)) \rightarrow O(n^3)$

