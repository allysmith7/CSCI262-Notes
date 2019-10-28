# Dynamic Allocation

- When dynamically allocating memory, the program gets memory from the _heap_ to store the object
- **Arrays** are just sequential blocks of memory, so you can do *pointer arithmetic* with them



###### Pointer Arithmetic

```c++
char s[5] = {'H', 'e', 'l', 'l', 'o'};
char* p = s;

for (int i = 0; i < 5; i++) {
    p[j] == *(p+j);
}

// Each time you ++, you move by sizeof(T) bytes, so 1 byte for char, 4 for int, etc.
```



###### Pointer Notes

- **C-style strings** are actually char-arrays so, `char *s = "Hello!" // valid in C, in C++ you need to add const`

- **Reference Parameters** are *not* pointers



###### Dynamic Array Allocation

```c++
int size;
cin >> size;
int arr[size]; // doesn't work because size is modifiable
int* arr = new int[size]; // works with dynamic allocation        note: new gives us a pointer to the memory
```

###### Stack vs. Heap

- In the stack, memory lasts within the scope, so if it is declared in a function, the memory is returned to the stack when the function returns
- In the heap, memory is allocated when you use the `new` keyword and stays until you `delete` whatever variable it is
    - use `delete[]` to delete a whole array rather than just the pointer to the first index
    - given `class* p = new class;`, access member variables and functions by doing either `p->var` or `(*p).var`

###### Destructors

- Destructors are defined in the class as a function as follows: `~[class name]();`
- Destructors never take a parameter and never return anything

###### Don'ts of Dynamic Allocation

- Dereference a pointer which has not been set to valid memory (using `new` or `&`) 
- Dereference a pointer to memory which has already been deallocated (a *dangling pointer*) 
- Change or lose a pointer which is pointing to dynamically allocated memory (or you won’t be able to deallocate – this causes a *memory leak*) 
- Use delete on a pointer which isn’t pointing to dynamically allocated memory (e.g., a dangling or null pointer) 