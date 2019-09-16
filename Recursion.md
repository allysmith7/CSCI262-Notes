# Recursion

- Defining something in terms of itself
- Needs a **base case, recursive call**

```c++
int factorial(int n) {
    if (n == 0) return 1;
    return n * factorial(n - 1);
}
```

- each function is added to "the stack", or the memory of the currently running program
- Make sure to include a base case and increment/decrement your recursive call