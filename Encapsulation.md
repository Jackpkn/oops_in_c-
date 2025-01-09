# Encapsulation in Object-Oriented Programming

Encapsulation is one of the core principles of Object-Oriented Programming (OOP). It refers to the bundling of data (variables) and methods (functions) that operate on the data within a single unit or class. It also involves restricting access to some of the object's components, which is often done using access modifiers like private, protected, and public.

## Why Encapsulation is Important

- **Data Hiding**: It protects the object's internal state from being modified directly, ensuring that only specific methods can modify it.
- **Maintainability**: If you need to change the implementation of an object, you can do so without affecting other parts of the code that interact with it.

## Access Modifiers

- **private**: Members are accessible only within the class.
- **protected**: Members are accessible within the class and its derived classes.
- **public**: Members are accessible from anywhere.

## Example of Encapsulation in C++

```cpp
#include <iostream>
using namespace std;

class Account {
private:
    double balance;  // Private data member

public:
    // Constructor to initialize balance
    Account(double initial_balance) {
        balance = initial_balance;
    }

    // Public getter method to access balance
    double getBalance() {
        return balance;
    }

    // Public setter method to modify balance with validation
    void deposit(double amount) {
        if(amount > 0) {
            balance += amount;
        } else {
            cout << "Invalid deposit amount!" << endl;
        }
    }

    void withdraw(double amount) {
        if(amount > 0 && amount <= balance) {
            balance -= amount;
        } else {
            cout << "Invalid withdrawal amount!" << endl;
        }
    }
};

int main() {
    Account myAccount(1000);  // Creating an Account object with an initial balance

    cout << "Initial balance: " << myAccount.getBalance() << endl;

    myAccount.deposit(500);  // Deposit
    cout << "Balance after deposit: " << myAccount.getBalance() << endl;

    myAccount.withdraw(200);  // Withdraw
    cout << "Balance after withdrawal: " << myAccount.getBalance() << endl;

    return 0;
}
```

### Explanation

- **Private Members**: `balance` is a private member, so it cannot be accessed directly from outside the class.
- **Public Methods**: The `deposit`, `withdraw`, and `getBalance` methods are public, allowing controlled access to the balance data. The setter methods ensure that the balance is modified only in a valid way.

### Benefits

- **Control**: You can control how the data is accessed and modified, adding validation or other logic in the setter methods.
- **Security**: It prevents direct manipulation of critical variables, which could lead to invalid or inconsistent states.