# Analysis of Recursive Algorithms

- To find the Big O of a function, look at what is being decremented. ex:

    ```c++
    double power(int n, unsigned k) {
        if (k == 0) return n;
        return n * power(n, k - 1);
    }
    ```

    - in this example, the Big O is actually O(k), rather than O(n), as `k` is what is being decremented each call.

- Another formula for the power function:

    ```c++
    double power(int n, unsigned k) {
        if (k == 0) return 1;
        if (k == 1) return n;
        return power(n, k/2) * power(n, k/2);
    }
    ```

    - this has the same number of calls, so it probably is easier to implement the other way

- The "Smart Way":

    ```c++
    double power(int n, unsigned k) {
        if (k == 0) return 1;
        double m = power(n, k/2);
        if (m % 2 == 0) {
            return m * m;
        } else {
            return m * m * n;
        }
    }
    ```

    - because this divides `k` by two each time, this function has a Big O of O(log~2~k)



## Searching

###### Linear Search:

```c++
int search(string x, char k) {
    for (int i = 0; i < x.size(); i++) {
        if (x[i] == k) return i;
    }
    return -1;
}
```

- Has Big O complexity of O(n) where n is the size of x

###### Binary Search:

```c++
int binary_search(int[] x, int k) {
    if (x.size() == 0) return -1;
    
    int pivot = x.size() / 2;
    
    if (x[pivot] == k) {
        return pivot;
    } else if (x[pivot] > k) {
        return binary_search(x[pivot, end], k);
    } else {
        return binary_search(x[begin, pivot], k);
    }
}
```

- Has Big O complexity of O(logn)
    - in Big O notations, the base is dropped from logarithmic functions because they all end up being about the same in the end, so log~10~ *and* log~2~ are written just as log



## Sorting

###### Merge Sort

```c++
 // as a complexity of O(nlogn)
int[] merge_sort(int[] x) {
    int n = x.size();
    if (n == 1) return x;
    left = merge_sort(x[0, n/2]);
    right = merge_sort(x[n/2 + 1, end]);
    return left + right;
}
```

- In the STL, sorting works on *random access iterators*, so vectors, strings, and arrays

    ```c++
    #include <algorithm>
    
    void sort(iterator_begin, iterator_end);
    // can also add a third algorithm that is a sort function, similar to compareTo() in Java
    ```

    