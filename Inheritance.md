# Inheritance in Object-Oriented Programming (OOP)

Inheritance is an important feature of Object-Oriented Programming (OOP) that allows a class (called the child or derived class) to inherit properties and behaviors (fields and methods) from another class (called the parent or base class). It promotes code reusability and establishes a hierarchical relationship between classes.

## Key Features of Inheritance

- **Code Reusability**: You can reuse the code of the parent class in the child class, reducing duplication.
- **Extensibility**: Child classes can add new features or modify existing ones without changing the parent class.
- **Hierarchy**: Models relationships like "is-a". For example, a Dog is-a Animal.
- **Overriding**: The child class can override methods of the parent class to provide its own implementation.
- **Access Control**: The access modifiers (public, protected, private) determine what can be inherited.

## Types of Inheritance in C++

- **Single Inheritance**: A child class inherits from a single parent class.
- **Multiple Inheritance**: A child class inherits from more than one parent class.
- **Multilevel Inheritance**: A class inherits from another class, which in turn inherits from another class.
- **Hierarchical Inheritance**: Multiple child classes inherit from the same parent class.
- **Hybrid Inheritance**: A combination of the above types.

## Example of Inheritance in C++

### 1. Single Inheritance

```cpp
#include <iostream>
using namespace std;

// Base class
class Animal {
public:
    void eat() {
        cout << "This animal eats food." << endl;
    }
};

// Derived class
class Dog : public Animal {
public:
    void bark() {
        cout << "The dog barks." << endl;
    }
};

int main() {
    Dog myDog;
    myDog.eat();  // Inherited from Animal
    myDog.bark(); // Defined in Dog
    return 0;
}
```

### 2. Multilevel Inheritance

```cpp
#include <iostream>
using namespace std;

// Base class
class Animal {
public:
    void eat() {
        cout << "This animal eats food." << endl;
    }
};

// Intermediate class
class Mammal : public Animal {
public:
    void walk() {
        cout << "This mammal walks." << endl;
    }
};

// Derived class
class Dog : public Mammal {
public:
    void bark() {
        cout << "The dog barks." << endl;
    }
};

int main() {
    Dog myDog;
    myDog.eat();  // Inherited from Animal
    myDog.walk(); // Inherited from Mammal
    myDog.bark(); // Defined in Dog
    return 0;
}
```

### 3. Multiple Inheritance

```cpp
#include <iostream>
using namespace std;

// Base class 1
class Teacher {
public:
    void teach() {
        cout << "Teaching students." << endl;
    }
};

// Base class 2
class Researcher {
public:
    void research() {
        cout << "Conducting research." << endl;
    }
};

// Derived class
class Professor : public Teacher, public Researcher {
public:
    void publish() {
        cout << "Publishing papers." << endl;
    }
};

int main() {
    Professor myProfessor;
    myProfessor.teach();    // From Teacher
    myProfessor.research(); // From Researcher
    myProfessor.publish();  // From Professor
    return 0;
}
```

## Access Modifiers and Inheritance

The access level of inherited members depends on the access specifier used during inheritance:

- **Public Inheritance**:
  - public members of the parent become public in the child.
  - protected members of the parent become protected in the child.
  - private members of the parent are not accessible in the child.
- **Protected Inheritance**:
  - public and protected members of the parent become protected in the child.
- **Private Inheritance**:
  - public and protected members of the parent become private in the child.

### Example with Access Modifiers

```cpp
#include <iostream>
using namespace std;

class Parent {
public:
    int publicVar = 10;

protected:
    int protectedVar = 20;

private:
    int privateVar = 30;
};

class Child : public Parent {
public:
    void display() {
        cout << "Public Variable: " << publicVar << endl;       // Accessible
        cout << "Protected Variable: " << protectedVar << endl; // Accessible
        // cout << "Private Variable: " << privateVar << endl;  // Not Accessible
    }
};

int main() {
    Child obj;
    obj.display();
    cout << "Accessing publicVar directly: " << obj.publicVar << endl; // Accessible
    // cout << obj.protectedVar; // Not Accessible
    return 0;
}
```

## Key Notes for Placements

- Understand the types of inheritance and their use cases.
- Be familiar with method overriding (polymorphism).
- Know the role of access specifiers in inheritance.
- Be cautious about multiple inheritance to avoid ambiguity (use virtual inheritance if needed).
- Understand real-world examples to relate: e.g., Vehicle -> Car -> ElectricCar.