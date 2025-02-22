# sijad-khan
#include <iostream>
#include <string>
using namespace std;

// BankAccount class declaration
class BankAccount {
private:
    string accountHolderName;
    int accountNumber;
    double balance;

public:
    // Constructor to initialize the account
    BankAccount(string name, int number) {
        accountHolderName = name;
        accountNumber = number;
        balance = 0.0;
    }

    // Function to deposit money into the account
    void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            cout << "Deposited: " << amount << "\n";
        } else {
            cout << "Invalid amount!\n";
        }
    }

    // Function to withdraw money from the account
    void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            cout << "Withdrew: " << amount << "\n";
        } else if (amount > balance) {
            cout << "Insufficient funds!\n";
        } else {
            cout << "Invalid amount!\n";
        }
    }

    // Function to display the account details
    void displayAccountDetails() {
        cout << "Account Holder: " << accountHolderName << "\n";
        cout << "Account Number: " << accountNumber << "\n";
        cout << "Balance: " << balance << "\n";
    }

    // Function to check the balance
    double checkBalance() {
        return balance;
    }
};

// Main function to drive the program
int main() {
    string name;
    int accountNumber;
    double amount;
    int choice;

    cout << "Enter account holder's name: ";
    getline(cin, name);
    cout << "Enter account number: ";
    cin >> accountNumber;

    // Create a BankAccount object
    BankAccount account(name, accountNumber);

    do {
        // Display menu options
        cout << "\nBank Management System\n";
        cout << "1. Deposit\n";
        cout << "2. Withdraw\n";
        cout << "3. Display Account Details\n";
        cout << "4. Check Balance\n";
        cout << "5. Exit\n";
        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
            case 1:
                cout << "Enter amount to deposit: ";
                cin >> amount;
                account.deposit(amount);
                break;
            case 2:
                cout << "Enter amount to withdraw: ";
                cin >> amount;
                account.withdraw(amount);
                break;
            case 3:
                account.displayAccountDetails();
                break;
            case 4:
                cout << "Current Balance: " << account.checkBalance() << "\n";
                break;
            case 5:
                cout << "Exiting the system...\n";
                break;
            default:
                cout << "Invalid choice! Please try again.\n";
        }
    } while (choice != 5);

    return 0;
}
