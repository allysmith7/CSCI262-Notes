# Inheritance

- Classes can *inherit* from other classes

    - Properties (variables)
    - Behaviors (methods)

- Inheritance serves various functions

    - Modeling class relationships
    - Code reuse
    - Subtyping/polymorphism

    ```c++
    class animal {
        public:
        	string name;
        	void print();
    };
    
    class dog : public animal { 						// public just means that all members have the
        public:											// same visibility as the superclass
        	string breed;
    };
    
    class cat : public animal {
    };
    
    void animal::print() {
        cout << "My name is " << name;
        cout << endl;
    }
    
    void dog::print() {									// can be rewritten as below
        cout << "My name is " << name << "." << endl;
        cout << "I am a " << breed << "." << endl;
    }
    
    void dog::print() {
        animal::print();
        cout << "I am a " << breed << "." << endl;
    }
    
    void print_animal(animal &a) {						// polymorphism
        a.print();										// will use the animal generic print function
    }													// fixed below with virtual
    
    class animal {
        public:
        	string name;
        	virtual void print();						// tells the program to use the print function
    };													// from the child class if it exists
    
    animal* A[2];										// outputs properly due to the virtual function
    A[0] = &c;
    A[1] = &d;
    for (int j = 0; j < 2; j++) A[j]->print();
    
    animal a = d;										// will use the animal print function,
    a.print();											// not the dog print
    ```

    

## Abstract Classes

- contains at least one "pure virtual" method

- cannot be instantiated

- can only be used via inheritance

- denoted by `= 0;` at the end of the function definition

    ```c++
    class animal {
    	public:
            string name;
            void print();
            virtual void speak() = 0; 					// makes it abstract, or pure virtual
    };
    
    void animal::print() {
        cout << "My name is " << name << ".";
        speak();										// can reference pure virtual methods,
        cout << endl;									// as they will be overwritten on compile
    }
    
    animal::animal(string nm) { name = nm;}
    
    dog::dog(string nm, string br) : animal(n) { 		// uses the animal default constructor from animal
        breed = br;										// as well as setting the breed
    }
    ```

    