# Sets & Maps

- Can be unordered or ordered

- Templetted, like vectors, queues, and stacks

    - `set<type T> s;`

- Does not contain duplicate values

- Does not have indexes, instead it uses iterators

    - easiest to loop through using a ranged loop e.g. `for (T var : set)`
    - alternatively, use `for (auto iter = set.begin(); iter != set.end(); iter++)`

- Member functions include...

    ```c++
    iterator<T> find(T &val); 		// returns an iterator to an item
    void insert(T &val);			// inserts an element, preserving uniqueness
    void remove(T &val);			// removes an element
    int count(T &val);				// returns 1 or 0, useful for testing if a value is in a set
    											// rather than finding its location with find()
    int size();						// returns # of unique items in the set
    bool empty();					// returns size == 0
    ```

###### Ordered Sets

- Items must be comparable
- Items are in sorted order
- Typically implemented using a binary tree

###### Unordered Set

- Typically faster
- Items are iterated in no particular order
- Implemented using hashtables

###### Iterators

- Object that *points to* an element in a container
- Abstractly, it works like a pointer
    - Use the `*` operator to dereference an iterator and get its value

## Maps

- Similar to a set, but it contains a **key** and a **value**

    - can be ordered or unordered
    - does not contain duplicate values
    - uses iterators, including range-based for loops
        - loops point to pair objects

- `map<type T1, type T2>` T1 and T2 don't have to be the same type, and they can be any type, even classes

    - the key type should likely *not* be a class, as it will be harder to access

- in the STL, the following methods are to be used: 

- `.at(key)`

    - returns a reference to the value associated with the key, unless the key is in the map, then it throws an exception

- `.find(key)`

    - returns an iterator to the pair of the key and value
    - if the key is not in the map, it returns `.end()`

- `[key]`

    - **always** returns a reference to a value
    - if the key is not in the map, it creates a pair with the default value and returns that reference
    - **should not** be used to test for containment

- `.insert({key, val})`

    - takes a pair as a parameter
    - **will not** overwrite/update existing entries

- `.emplace(key, val)` or `.emplace({key, val})`

    - takes pair or key, val
    - **will not** overwrite/update existing entry

- `[key] = val`

    - **will** overwrite/update existing entry

    

## Pair

- `pair` is an STL template class designed for one purpose: to hold two object
- `auto p = make_pair(obj1, obj2);` is easier than creating a pair and manually specifying what obj1 and obj2 are
    - can also use `{obj1, obj2}` to pass a pair, without instantiation, into a function that is expecting a pair
- use `.first` and `.second` to access the values

