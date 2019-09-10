# Stacks and Queues

These data structures are easily built using a LinkedList as the backing structure

------

## Stacks

Stacks are **LIFO**, or last in first out, which means the item that is added last is the first item to be removed from the list.

- `.top()` looks at the item at the top of the stack
- `.push()` adds an item to the top of the stack
- `.pop()` takes an item from the top of the stack
-  Most easily built using `add_to_front()` and `remove_from_front()` 
- Can be used practically for syntax analysis, traversing trees and mazes

## Queues

Queues are **FIFO**, or first in first out, so things are added to the end and takes thing from the front

- ` .enqueue()` or `.push()` will add to the back of the queue
- `.dequeue()` or `.pop()` will remove from the front
- `.front()` will show the item at the front, but leave it in the queue
- Most easily built using `.add_to_back()` and `.remove_from_front()`
- Can be used practically for print jobs, process scheduling, I/O request scheduling, event handling