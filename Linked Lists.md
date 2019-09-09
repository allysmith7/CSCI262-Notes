# Linked Lists

## Nodes

Linked lists are made up of individual nodes that contain a value and a pointer to the next node iwthin the list. Ex:

```c++
class node {
    public:
    int data;
    node* next;
}
```

To create a linked list, you create a `head` node, then use `head->next = new node` to create sequential nodes, etc.

To access data within a node, you can either use `(*head).data` or `head->data` both of these dereference the pointer and access `data`

##Looping

To loop through a linked list using a for loop, use the following code:

```c++
for (node* p = head; p != nullptr; p = p->next) {
	...
}
```

##Linked Lists vs. Arrays

- For linked lists...
    - Growing and shrinking is trivial
    - Insertion and removal is inexpensive-ish
    - Traversal is expensive
    - No random access because no indexes
- For arrays
    - Growing and shrinking is not possible
    - Traversal is inexpensive
    - Random access is possible

## Insertion

To insert a node within a linked list, you need to traverse the array to the node before your insertion point, create a new `node`, set `data` to your value, then set `next` to the node after it and set the current node's next to the new node... easier done than said

```c++
node *current = head;

while (current->data != search) {
	current = current->next;
}

// creates new node
node new_node = new node;
new_node->data = VALUE;
// sets new nodes next to node after insertion
new_node->next = current->next;

// sets node before insertion to the new node
current->next = new_node;
```

## Adding

```c++
void add(node* head, int val) {
	// start at head, travel until you find the tail
	node* ptr = head;
	while (ptr->next != nullptr) {
	ptr = ptr->next;
	}
	
	ptr->next = new node;
    ptr->next->data = val;
    ptr->next->next = nullptr;
}
```

## Linked List Class Declaration

```c++
class LinkedList {
    public:
    	void add(int val);
    	void print();
    
    private:
    	class node {
            public:
            	int _data;
            	node* _next;
        };
    	node* _head = nullptr;
    	node* _tail = nullptr;
    	int _size = 0;
};
```

## Add to front
```c++
void add_to_front(int val) {
	// make new node
    node* p = new node;
    p->_data = val;
    p->_next = nullptr;

	// checks for empty list
    if (_head == nullptr) {
        _head = _tail = p;
    }
    
    node* currNode = _head;
    while (currNode->_next != nullptr) {
        currNode = currNode -> _next;
    }
```

## Destroying a node

For every node that is created, you must delete it in order to prevent a memory leak.

```c++
void remove_from_front() {
	if (_head == nullptr) {
        return;
    }   
    
    // save pointer to head
    node* p = _head;
    
    // move head down a node
    _head = _head -> _next;
    
    // destroy old head
    delete p;
    
    _size--;
}

void remove_from_end() {
    if (_head == nullptr) {
        return;
    }
    
    if (_head == _tail) {
        delete _head;
        _head = _tail = nullptr;
    } else {
        node* p = _head;
        while (p->_next != _tail) {
            p = p -> _next;
        }
        p -> _next = nullptr;
        delete _tail;
        _tail = p;
    }
    
    _size--;
}
```

