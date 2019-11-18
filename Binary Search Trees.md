# Binary Search Trees

- Data structure for holding *comparable* elements
    - Efficient searching, insertion, and deletion
    - Underlying structure for sets, maps
    - Also used for database indexing
- Basic Structure:
    - Node holds *unique* elements and pointers to children nodes
    - Data acts as a partitioning element in the tree
        - Child nodes to the left are always of lesser value
        - Child nodes to the right are always of greater value

```c++
template <class T>
binary_tree_node<T>* search(binary_tree_node<T>* root, T val) {
	if (root == NULL) return NULL;
	if (val == root->data) return root;
	if (val < root->data) return search(root->left, val); 
    else return search(root->right, val);
}

template <class T>
void insert(binary_tree_node<T>*& root, T val) {
	if (root == NULL) root = new binary_tree_node<T>(val); 
    else if (val < tree->info) insert(tree->left, val); 
    else if (val > tree->info) insert(tree->right, val);
}

template <class T>
void remove(binary_tree_node<T>* root, T val) {
     if (root == NULL) return nullptr;
    
    if (val < root->data) remove(root->left, val);
	else if (val > root->data) remove(root->right, val);
    
    else { // item found!
		if (root->left == NULL || root->right == NULL) {
			binary_tree_node<T>* tmp;
			if (root->left == NULL) tmp = root->right; else tmp = root->left;
			delete root;
			root = tmp;
		} else {
            binary_tree_node<T>* tmp = root->left; 	// find rightmost node
            binary_tree_node<T>* parent = root; 	// in left subtree 
            while (tmp->right != NULL) {
                parent = tmp;
                tmp = tmp->right;
            }
            root->data = tmp->data;

            if (parent == root) root->left = tmp->left;
            else parent->right = tmp->left;

            delete tmp;
        }
    }
}
```

- BigO complexities: 
    - Best case: log(n)
    - Worst case: n
- Height-Balanced Tree (AVL):
    - the height of the left and right subtrees can only differ by 1 of every node
    - each subtree contains roughly half the nodes
- Self-balancing BSTs:
    - Red-black tree
        - Root node is black
        - no two adjacent nodes can be red
    - AVL tree
    - Splay tree
        - Attempts to decrease complexity to constant time for a second search by moving the searched-for node to the root and reorganizing

