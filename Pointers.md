# Pointers

## Bases

- 0x is hexadecimal (base 16) 0-f
- binary is 0-1

## Bits and Bytes

- a byte is 8 bits
- `char` uses 1 byte, `int` and `float` use 4, `double` uses 8
    - sizeof() returns how many bytes something is

## Memory

- computer memory is organized as an indexed array of bytes, stacked from the bottom to the top

- to print address of a variable, do `cout << &x << endl;`

- a *pointer* is a variable that stores an address

    - the type of pointer for any type `T` is type `T*`

- you can *dereference* a pointer by using `*`  ex:

    ```c++
    int x = 19851225;
    int* p = &x;
    cout << *p << endl; // prints out 19851225
    ```

- when changing the value of `x`, the value of `p` doesn't change

- `nullptr` is used now instead of `null`, can't be dereferenced