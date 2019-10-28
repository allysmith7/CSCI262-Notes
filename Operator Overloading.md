# Operator Overloading

- Classes have member variables and functions[^1] within them, and they can also overwrite default behavior of operators such as `+, [], >, <, *, -, /,` etc.

    - If you do, be consistent with the function of the operators, and be complete by overwriting at least the matching pair of operators

- Helper Function:

- ```c++
    complex complex::operator +(const complex &a, const complex &b) {
        return complex(a.real + b.real, 
                       a.imaginary + b.imaginary);
    }
    ```

- Member Function: because you are calling it *on* an object, you only need 1 argument

    ```c++
    complex complex::operator+(const complex &b) {
        return complex(real + b.real,
                imaginary + b.imaginary);
    }
    ```

- some operators (e.g. assignment) **must** be member functions

- some operators (e.g. <<, >>) **must** be helper functions

- Non-member operator functions may have to be declared as *friend* functions for private access 

- Most binary operators can be either

    - Which you use partly a matter of style
    - For now, recommend using non-member functions 

- You can write a function with a different set of parameters that behave differently

- Example:

    ```c++
    complex complex::operator +(const double &b) {
        return complex(real + b, 
                       imaginary);
    }
    ```

- To tell the program how to print an object, you must overwrite the function as follows:

    ```c++
    ostream& operator<<(ostream &out, const complex &c) {
        out << c.real << " + " << c.imaginary << "i";
        return out;
    }
    ```

    

[^1]: By default, member variables and functions are private

