# Recursion

- **Recursion** is defining something in terms of itself, usually problems that can be broken up into smaller problems
- Needs a **base case** and a **recursive call**

```c++
int factorial(int n) {
    if (n == 0) return 1;
    return n * factorial(n - 1);
}
```

- each function is added to "the stack", or the memory of the currently running program
- Make sure to include a base case and increment/decrement your recursive call
- Recursive functions can be *top-down* or *bottom-up*, different problems function in different ways based on which method you choose

######Towers of Hanoi example

```c++
/*
Setup:
1	|	|
2	|	|
3	|	|
4	|	|
5	|	|
---------
a	b	c
*/

void moveTower(int count, vector<int> a, vector<int> b, vector<int> c) {
    /*
    count is # to move
    a is 'from'
    b is 'to'
    c is spare
    */
    
    if (count == 1) {
        int size = a.end();
        a.pop_back(;
        b.push_back(size);
    } else {
        moveTower(count - 1, a, b, c);
        moveTower(1, a, b, c);
        moveTower(count - 1, c, b, from);
    }
}
```

