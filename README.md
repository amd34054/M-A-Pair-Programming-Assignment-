# M-A-Pair-Programming-Assignment-
class income
 def__init__(self, source, amount, frequency):
  self.source = source
  self.amount = amount
  self.frequency = frequency

# EXPENSE TRACKER

# Create Expense class
class Expense:

    def __init__(self, description, amount, category, date):
        self.description = description
        self.amount = amount
        self.category = category
        self.date = date

    # Display expense information
    def show_expense(self):
        print("Description:", self.description)
        print("Amount: $", self.amount)
        print("Category:", self.category)
        print("Date:", self.date)


# Create a list to store expenses
expenses = []


# Function to add a new expense
def add_expense():

    description = input("Enter expense description: ")
    amount = float(input("Enter expense amount: $"))
    category = input("Enter expense category: ")
    date = input("Enter expense date: ")

    if amount > 0:
        expense = Expense(description, amount, category, date)
        expenses.append(expense)
        print("Expense added successfully!")

    else:
        print("Expense amount must be greater than zero.")


# Function to display all expenses
def view_expenses():

    if len(expenses) == 0:
        print("No expenses have been recorded.")

    else:
        for expense in expenses:
            expense.show_expense()
            print("--------------------")


# Function to calculate total expenses
def calculate_total_expenses():

    total = 0

    for expense in expenses:
        total = total + expense.amount

    return total


# Function to calculate spending by category
def calculate_category_spending():

    category_totals = {}

    for expense in expenses:

        if expense.category in category_totals:
            category_totals[expense.category] = (
                category_totals[expense.category] + expense.amount
            )

        else:
            category_totals[expense.category] = expense.amount

    print("\nSpending by Category:")

    for category in category_totals:
        print(category, ": $", category_totals[category])


# EXPENSE TRACKER MENU

while True:

    print("\n===== EXPENSE TRACKER =====")
    print("1. Add Expense")
    print("2. View Expenses")
    print("3. Calculate Total Expenses")
    print("4. View Spending by Category")
    print("5. Exit")

    choice = input("Select a number: ")

    if choice == "1":
        add_expense()

    elif choice == "2":
        view_expenses()

    elif choice == "3":
        print("Total Expenses: $", calculate_total_expenses())

    elif choice == "4":
        calculate_category_spending()

    elif choice == "5":
        print("Exiting Expense Tracker.")
        break

    else:
        print("Invalid selection. Please try again.")
