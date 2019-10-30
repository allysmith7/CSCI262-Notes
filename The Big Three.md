# The Big Three

###### Copy constructor, assignment operator, and destructor



## Assignment

- The default behavior of the `=` is move pointers around so you can have two objects pointing to the same memory address

    ```c++
    foo x, y;
    y = x; // assignment constructor is used because both x and y have already been declared
    
    number& number::operator=(const number& num) {
        if (this == num) return *this; // self assignment
        
        // no need to allocate/deallocate because they are the same size
        *ptr = *(num.ptr);
        return *this;
    }
    ```

## Copy Constructor

- The copy constructor is used when you have one object that you want two copies of stored in different memory addresses

    - Called *shallow copy*

    ```c++
    foo x;
    foo y(x); // y is created as a copy of x
    	or
    foo y = x;
    ```
    - when using the copy operator and shallow copy, pointers point to the memory addresses that x holds

- When writing a copy constructor, you must use pass by reference because otherwise it will create *another* copy

    ```c++
    number::number(const number& num) {
        ptr = new int; 		// allocates memory
        *ptr = *(num.ptr); 	// sets the value at the pointers equal
    }
    ```

- Example arraylist copy constructor:

    ```c++
    class array_list { 
        public:
    		array_list();
        	array_list(const array_list& lst); 
        	~array_list();
        
    		array_list& operator=(const array_list& lst);
        
    		int size();
    		int get(int index);
    		void set(int index, int val); ...
    	private:
    	    int* _arr;
    		int _size; int _capacity; void _resize();
    };
    
    // copy constructor
    array_list::array_list(const array_list& src) {
        _capacity = src._capacity;
        _size = src._size;
        _arr = new int[_capacity];
        for (int j = 0; j < _size; j++) {
        	_arr[j] = src._arr[j];
        }
    }
    
    // assignment operator
    array_list& array_list::operator=(const array_list& src) {
        if (this == &src) return *this; // self-assign chk
        delete[] _arr;
        
        _capacity = src._capacity;			// same as deep copy, can be refactored
        _size = src._size;
        _arr = new int[_capacity];
        for (int j = 0; j < _size; j++) {
        _arr[j] = src._arr[j];
            
        return *this; // return *this
        }
    }
    
    // destructor
    array_list::~array_list() { 
        delete[] _arr;
    }
    ```

    

## Destructor

- Called when an object goes out of scope or when the `delete` keyword is used

- Responsible for returning memory to the stack when an object is no longer needed

- If you use dynamic memory allocation in a class, you need to write a destructor to clean up this memory

    - primitives do not need to be included in your destructor as they are handled automatically
        - same thing with classes like `vector` or `string` that come from STL, those destructors are written for us

    ```c++
    number::~number() { 
        delete ptr;
    }
    ```

    