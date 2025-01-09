# Polymorphism in C++

Polymorphism is an Object-Oriented Programming (OOP) concept that allows objects to behave differently based on their context. It is derived from the Greek words poly (many) and morph (forms), meaning "many forms."

In simpler terms, polymorphism enables the same function or operation to perform different tasks depending on the object it is acting upon.

## Types of Polymorphism in C++

### Compile-Time Polymorphism (Static Binding)

- Achieved using function overloading and operator overloading.
- The decision about which method to call is made at compile-time.

### Run-Time Polymorphism (Dynamic Binding)

- Achieved using function overriding and virtual functions.
- The decision about which method to call is made at runtime.

## 1. Compile-Time Polymorphism

### a. Function Overloading

Function overloading allows multiple functions to have the same name but different parameters (type or number).

```cpp
#include <iostream>
using namespace std;

class Calculator {
public:
    // Overloaded add function
    int add(int a, int b) {
        return a + b;
    }

    double add(double a, double b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }
};

int main() {
    Calculator calc;
    cout << calc.add(5, 10) << endl;         // Calls add(int, int)
    cout << calc.add(5.5, 4.5) << endl;     // Calls add(double, double)
    cout << calc.add(1, 2, 3) << endl;      // Calls add(int, int, int)
    return 0;
}
```

### b. Operator Overloading

Operator overloading allows custom implementation of operators for user-defined types.

```cpp
#include <iostream>
using namespace std;

class Complex {
private:
    double real, imag;

public:
    Complex(double r, double i) : real(r), imag(i) {}

    // Overload + operator
    Complex operator+(const Complex& other) {
        return Complex(real + other.real, imag + other.imag);
    }

    void display() {
        cout << real << " + " << imag << "i" << endl;
    }
};

int main() {
    Complex c1(2.3, 4.5), c2(1.2, 3.3);
    Complex c3 = c1 + c2;  // Calls operator+ function
    c3.display();
    return 0;
}
```

## 2. Run-Time Polymorphism

### a. Function Overriding

When a derived class provides a specific implementation of a method that is already defined in its base class. Achieved using virtual functions in C++.

```cpp
#include <iostream>
using namespace std;

// Base class
class Animal {
public:
    virtual void sound() {  // Virtual function
        cout << "Animal makes a sound." << endl;
    }
};

// Derived class 1
class Dog : public Animal {
public:
    void sound() override {
        cout << "Dog barks." << endl;
    }
};

// Derived class 2
class Cat : public Animal {
public:
    void sound() override {
        cout << "Cat meows." << endl;
    }
};

int main() {
    Animal* animal;
    Dog dog;
    Cat cat;

    animal = &dog;
    animal->sound();  // Calls Dog's sound()

    animal = &cat;
    animal->sound();  // Calls Cat's sound()
    return 0;
}
```

## Key Differences Between Compile-Time and Run-Time Polymorphism

| Feature | Compile-Time Polymorphism | Run-Time Polymorphism |
|---------|---------------------------|-----------------------|
| Binding | Static (determined at compile time) | Dynamic (determined at runtime) |
| Mechanism | Function/Operator overloading | Function overriding using virtual functions |
| Performance | Faster (no runtime overhead) | Slower (involves a vtable lookup) |
| Flexibility | Less flexible | More flexible |

## Real-World Example

### Compile-Time Polymorphism

ATM machines: The same `withdraw()` function handles different types of accounts, such as savings and checking, based on parameter types.

### Run-Time Polymorphism

An `Animal` base class can have derived classes like `Dog` and `Cat`. The `sound()` method behaves differently depending on the object type at runtime.

## Key Notes for Placements

- Understand function overloading, operator overloading, and function overriding.
- Focus on the difference between compile-time and run-time polymorphism.
- Practice writing virtual functions and understand the vtable mechanism in C++.
- Use polymorphism to make code extensible and maintainable.
- Relate polymorphism to real-world scenarios to explain it effectively during interviews.