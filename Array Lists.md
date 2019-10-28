# Array Lists

- **Array lists** are a list structure built on dynamically allocated arrays

- Very similar to a vector, not like a linked list

- Array lists *resize* when they fill up (usually double in size)

    - **Capacity** is how many slots in the list, while **size** is the number of elements stored in the list

    ```c++
    // array_list.h
    class array_list {
        public:
    		array_list();
    		int size();							{ return _size; }
    		int get(int index);					{ return _arr[index]; }
    		void set(int index, int val); 		{ _arr[index] = val; }
        	void add(int val);
    		void insert(int index, int val);
        	void erase(int index);
    		int& operator[](int index);			{ return _arr[index]; }	// operator overload
        
        private:
    		int* _arr;
        	int  _size;
        	int  _capacity;
        	void _resize();
      };
    
    // array_list.cpp
    // missing error checking
    // isn't templatized, only stores ints
    // no iterators
    // the "big 3": copying, assigning, and destroying: are we getting all the memory back?
    array_list::array_list() {
        _capacity = 1; // can be any value
        _size = 0;
        _arr = new arr[_capacity];
    }
    
    array_list::_resize() {
        if (_size == _capacity) {
            _capacity *= 2;
            
            int* temp = new int[_capacity];
            for (int i = 0; i < _size; i++) {
                temp[i] = _arr[i];
            }
            
            delete[] _arr;
            _arr = temp; 
    	}
    }
    
    array_list::add(int val) {
        // O(1) best case, when you don't expand
        // O(n) worst case, when you expand
        _resize();
        
        arr[_size] = val;
        _size++;
    }
    
    array_list::insert(int index, int val) {
        // O(1) when the list is empty or insert at end
        // O(n) in worst or average case
        _resize();
        
        for (int j = _size; j > index; j--) {
            _arr[j] = _arr[j - 1];
        } 
        
        _arr[index] = val;
        _size++;
    }
    
    array_list::erase(int index) {
        // O(1) when the list is empty or insert at end
        // O(n) in worst or average case
        for (int j = index; j < _size - 1; j++) {
    		_arr[j] = _arr[j + 1]; 
        }
        _size--;
    }
    ```

    