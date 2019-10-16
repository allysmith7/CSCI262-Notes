# Hashtables

- Used in *unordered* sets and maps to determine the location on an item within the structure

- Allows for basic operations to be **constant time**

- Good for holding **unique** keys

- Issue of **Collisions**, aka when values have the same hash value

    - **Collision Detection**
        - Chaining: Linked List for each hash, can make it to where operations are not contant time any more
            - Uses linked list to take advantage of dynamic allocation
        - Open Addressing: When a second value matches to a hash, you start at the beginning and look for an open spot
            - Makes look-up more complicated
        - Double Hashing: Inner hash function to ensure that values that match original hashes don't overlap again

    

    ###### Creating a Hashtable

    - Create an array of some size
    - For each value you want to store...
        - Convert to an integer or *hash key * (see below)
        - Index = hash key % array size
        - Store key at the resulting index



###### Hash Functions

- A good hash function is the first defense against collisions
- Example: Hashing strings
    - Can add first four bytes
    - Can add ASCII codes
    - Java: $\sum_{i=0}^{n}{\text{s[i]} \times 31^{n-i-1}}$