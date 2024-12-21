# 🏧 ATM Project 🏧

**ATM Project** This project simulates a basic ATM system with the following features:

> This project demonstrates the use of Python programming concepts like loops, conditionals, functions, and list operations.💡


---

## 🎮 Project Features
- **PIN Verification**: Users need to enter the correct PIN to access the system. After 3 incorrect attempts, the system locks.
- **Main Menu**: Provides options to:
## 1.Display current balance.
## 2.Withdraw funds (multiple of 10).
## 3.Deposit funds.
## 4.View the last 10 transactions.
## 5.Exit the system.
- **Transaction History**: Tracks and displays the last 10 transactions.
- **Input Validation**: Handles invalid inputs gracefully.

---


#👨‍💻Code
# Initial setup
    import time
    import sys


    user_balance = 100
    transactions = ["NA"] * 10
    attempts = 3

# Welcome message
    print('''The PIN code is 1122.
    Don't use caps.
    You can see the previous 10 transactions.''')
    time.sleep(1)
    print("Welcome to Kingdom Trust Banking\n")

# PIN verification
    while attempts > 0:
    pin = input("Enter Your PIN: ")
    if pin == "1122":
        print("Correct PIN\n")
        break
    else:
        attempts -= 1
        print(f"Incorrect PIN. You have {attempts} attempts left.")
        time.sleep(0.75)
        if attempts == 0:
            print("Too many incorrect attempts. Please try again later.")
            sys.exit()

 # Main menu
    def display_menu():
    return int(input('''Please Select an Option:
    1 - Display Balance
    2 - Withdraw Funds
    3 - Deposit Funds
    4 - Print List of Transactions
    5 - Return Card
    ---> '''))

    while True:
    time.sleep(0.75)
    menu = display_menu()

    if menu == 1:  # Display Balance
        print(f"Your Balance: ${user_balance}\n")

    elif menu == 2:  # Withdraw Funds
        while True:
            time.sleep(0.75)
            print("Withdraw Options: 10, 20, 50, 100, or Other (multiple of 10)")
            wf = int(input("Enter amount to withdraw or 0 to return to menu: "))
            if wf == 0:
                break
            if wf % 10 != 0 or wf <= 0:
                print("Invalid amount. Please enter a valid option.")
            elif wf > user_balance:
                time.sleep(0.75)
                print("Insufficient balance!")
            else:
                user_balance -= wf
                transactions.pop(0)
                transactions.append(f"Withdrew ${wf}")
                print(f"Successfully withdrew ${wf}. Remaining balance: ${user_balance}")
                break

    elif menu == 3:  # Deposit Funds
        time.sleep(0.75)

    dp = int(input("Enter amount to deposit: "))
        if dp > 0:
            time.sleep(0.75)
            user_balance += dp
            transactions.pop(0)
            transactions.append(f"Deposited ${dp}")
            print(f"Successfully deposited ${dp}. New balance: ${user_balance}")
        else:
            print("Invalid amount. Deposit must be positive.")

    elif menu == 4:  # Print Transactions
        time.sleep(0.75)

    print("Last 10 Transactions:")
        for idx, transaction in enumerate(transactions, 1):
            print(f"{idx}: {transaction}")

    elif menu == 5:  # Return Card
        time.sleep(0.75)

        print("Thank you for banking with Kingdom Trust!")
        sys.exit()

    else:
        print("Invalid option. Please choose again.")

---
📜 License
This project is licensed under the MIT License.

GitHub:KAMENOVGEORGI
Email:g.kamenovkanchev@gmail.com

