# Abstraction in Object-Oriented Programming (OOP)

Abstraction is another core principle of Object-Oriented Programming (OOP) that focuses on hiding the complex implementation details and exposing only the essential features of an object or system. This allows the user to interact with the object at a higher level without needing to understand its internal workings.

## Key Points of Abstraction

- **Simplifies Interaction**: It provides a simplified view of the object by hiding unnecessary details.
- **Reduces Complexity**: Only essential functionalities are exposed, making the system easier to interact with and understand.
- **Promotes Reusability**: Abstract classes and interfaces can be reused across different parts of the system, making code more modular and maintainable.

## Types of Abstraction

- **Data Abstraction**: Hiding the internal data and showing only relevant data.
- **Control Abstraction**: Hiding the implementation of control flow (like functions, loops, etc.).

## Achieving Abstraction in C++

- **Abstract Classes**: A class that contains at least one pure virtual function (a function declared with `= 0`).
- **Interfaces**: C++ doesn't have formal interfaces like Java, but an abstract class with only pure virtual functions serves the same purpose.

## Example of Abstraction in C++

```cpp
#include <iostream>
using namespace std;

// Abstract class
class Shape {
public:
    // Pure virtual function (abstract)
    virtual void draw() = 0;  // No implementation here, must be overridden

    // A regular function
    void move(int x, int y) {
        cout << "Moving shape to (" << x << ", " << y << ")" << endl;
    }
};

// Derived class
class Circle : public Shape {
public:
    void draw() override {  // Implementation of the pure virtual function
        cout << "Drawing a Circle!" << endl;
    }
};

// Derived class
class Square : public Shape {
public:
    void draw() override {  // Implementation of the pure virtual function
        cout << "Drawing a Square!" << endl;
    }
};

int main() {
    Shape* shape1 = new Circle();  // Create a Circle object
    shape1->draw();  // Call the overridden function in Circle
    shape1->move(10, 20);  // Call the non-virtual function in Shape

    Shape* shape2 = new Square();  // Create a Square object
    shape2->draw();  // Call the overridden function in Square
    shape2->move(30, 40);  // Call the non-virtual function in Shape

    delete shape1;
    delete shape2;

    return 0;
}
```

## Explanation

- **Abstract Class Shape**: Contains a pure virtual function `draw()`, making it an abstract class. This forces derived classes like `Circle` and `Square` to implement their own version of `draw()`.
- **Derived Classes**: Both `Circle` and `Square` inherit from `Shape` and provide their own implementation of the `draw()` function.
- **Abstraction in Action**: The user interacts with the `Shape` class through the `draw()` method without needing to know the specific details of how each shape is drawn.

## Benefits of Abstraction

- **Improves Code Maintainability**: Changes in the implementation of a class do not affect code that uses the abstract class.
- **Code Flexibility**: Allows you to work with different objects (like `Circle` and `Square`) through a common interface without knowing their specific types.
- **Cleaner Code**: Helps in organizing code and focusing only on the essential features.