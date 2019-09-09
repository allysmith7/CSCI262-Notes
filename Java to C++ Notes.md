# Java to C++ Notes
## Similarities
- primitive types
- arithmetic operators
- logic operators
	- except ==
- if/else

## Functions/Methods
* C++ is built on C, a structured language
	- C code runs in C++
- C++ allows **free** functions, like a global function that can be called from anywhere
	- always public
- non-static method are invoked using a dot operator
- methods have access to other members of object
- Methods can reference bound object using `this` keyword
	- `this` is a pointer in C++, not a reference


## Classes
* in C++, classes are all public
* There are visibility sections, like below:
```c++
class Dog {
	private:
		int age;
		string name;
	public:
		string owner;
		int getAge();
		int setAge();
		...
};
```

## Objects
- In C++, Objects are created when the class type is declared. ex:
```c++
Java:
Dog quinn = new Dog();

C++:
Dog quinn;
```
* To call parameter constructor, do the following:
`Dog quinn(42);`
* In Java, objects hold the reference to the data, in C++, the object holds the value
	* When passed as an argument, Objects are passed by value, unless an `&` is put in front of it

## Testing Equality
- In Java, == tests if two objects have the same memory address
- In C++, == is not defined for a class, so you do it manually
	- == should function like .equals() in Java

## Object Destruction
- In C++, objects are destroyed when the function they are declared in returns
	- If you return an object from a function, a copy is returned

## Arrays
- Java:
	- Are objects
	- Have `.length` property
	- Are bound-checked (throws an exception for out of bounds)
- C++:
	- Arrays are primitives
	- No properties or methods
	- No bound-checking (out of bounds can cause segmentation fault or can lead to errors later on)
	- Must keep check of length on your own

## File I/O
- Same idea as Java, but *very* different syntax
- Will be covered in lab 2

## Miscellaneous
- Symbols (names of things) must be declared before use
	- Use *header (.h)* files to share decelerations (not definitions) among all users of the declared entities
	- `#include` lets us incorporate the declarations from header files into the current compilation unit
	- Must use "include guards" or `#pragma once` to prevent multiple declarations of same symbol
		- include guards are as follows
```c++
// file foo.h
#ifndef _FOO_H
#define _FOO_H

// file foo.cpp
#define _FOO_H
```
- C++ doesn't allow for multiple definitions of the same thing
	- Dependencies are resolved at link time, not compile time
	- If not careful, you can compile the same thing twice
- No restrictions on file naming (doesn't need to match class name)

## C++ File Conventions
- Header files contain class declarations and function prototypes only
	- use `#pragma once`
- Source (.cpp) files contain function or method definitions only
- For class named `X`, create `X.cpp` and `X.h`
	- `X.h` has single class declaration for `X`. maybe helper classes if only used by `X`
	- `X.cpp` has `X` method definitions
- Put `main()` and helper functions in its own file named `main.cpp` or `project_name.cpp`

