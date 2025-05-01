#include <stdio.h>

#include <stdlib.h>

void checkBalance(int balance) {
    printf("Current Balance: ₹%d\n", balance);
}

void deposit(int *balance) {
    int amount;
    printf("Enter amount to deposit: ₹");
    scanf("%d", &amount);

    *balance += amount;  // Add deposit to balance
    printf("Deposit successful! New Balance: ₹%d\n", *balance);
}

void withdraw(int *balance) {
    int amount;
    printf("Enter amount to withdraw: ₹");
    scanf("%d", &amount);

    if (amount > *balance) {
        printf("Insufficient balance!\n");
    } else {
        *balance -= amount;  // Deduct withdrawal
        printf("Withdrawal successful! Remaining Balance: ₹%d\n", *balance);
    }
}

int main() {
    int enteredPin, savedPin, balance = 10000, choice;

    // Step 1: Handle PIN creation or reading
    printf("No PIN found. Please create a new 4-digit PIN: ");
    scanf("%d", &savedPin);
    printf("PIN created successfully!\n");

    // Ask for PIN
    printf("Enter your PIN: ");
    scanf("%d", &enteredPin);

    if (enteredPin != savedPin) {
        printf("Incorrect PIN. Access Denied.\n");
        return 0;
    }

    // Step 2: ATM Menu
    do {
        printf("\nATM Menu:\n");
        printf("1. Check Balance\n");
        printf("2. Deposit Money\n");
        printf("3. Withdraw Money\n");
        printf("4. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                checkBalance(balance);
                break;
            case 2:
                deposit(&balance);
                break;
            case 3:
                withdraw(&balance);
                break;
            case 4:
                printf("Thank you for using the ATM!\n");
                break;
            default:
                printf("Invalid choice. Please try again.\n");
        }
    } while (choice != 4);

    return 0;
}
