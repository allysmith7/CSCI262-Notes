# Binary Trees

- Trees are defined recursively, either it is empty or it has a root `node` with with children, each of which is also a tree
- The final node in a line is called a 'leaf' or an 'external node'
- The connection between nodes is called 'edges'
    - The number of connections between any node and the root is that node's 'depth'
    - The maximum depth of all nodes is the 'height' of the tree



## What makes it a Binary Tree?

- Binary trees have two child node pointers

- Given n nodes in the tree...

    - Maximum height of n
    - Minimum heigh of log~2~n

- A 'full' tree is where each node, excluding leaves, has two children

- Example templatized node class for a binary tree:

    ```c++
    template <class T>
    class binary_tree_node {
        public:
    		T data;
        	binary_tree_node<T>* left;
        	binary_tree_node<T>* right;
    }
    ```

## Traversals

###### Pre-Order

- Does action on the root, then the left sub-tree, then the right sub-tree

###### In-Order

- Does action on the left sub-tree, then the root, then the right sub-tree

###### Post Order

- Does action on the left sub-tree, then the right sub-tree, then the root



## Example Functions

```c++
template <class T>
void print_preorder(binary_tree_node<T>* root) {
    if (root != NULL) {
		cout << root->data << " ";
        print_preorder(root->left);
        print_preorder(root->right);
    }
}

template <class T>
int count(binary_tree_node<T>* root) {
	if (root == NULL) return 0;
	return 	1
        	+ count(root->left)
        	+ count(root->right);
}
```

## Possible Applications

- Decision trees
    - A kind of structure used in AI
    - See next project – Animal (20 Questions) 

- Sets/Maps
    - Using Binary *Search* Trees (next lecture) 

- Compression/encoding (Huffman encoding)
- Organizing high-dimensional spaces (k-d trees)
- Spelling dictionary (Tries)
- Many more... 