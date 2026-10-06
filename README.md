# Employee Payroll System

An Employee Payroll System is a software application designed to automate the management of salary generation, tracking employee work hours, and calculating deductions (like taxes or insurance). It is typically built using Object-Oriented Programming (OOP) to structure data for different employee types (e.g., salaried, hourly) and uses file handling or databases to securely store financial records that saves employee data in a CSV file and payslips in a text file.

## What the project does

This project helps manage the salaries of employees. A user can add Full-Time and Part-Time employees, calculate their salary, generate payslips, and search for employees by name or ID. All data is saved in files, so nothing is lost when the program is closed.

## How the project works

1. When the program starts, it loads the saved employees from `employees.csv`. If the file does not exist, it starts with an empty list.
2. A menu is shown and the user selects an option (1 to 6).
3. Each employee has a unique ID (starting from 101), a name, an employee type, and a pay amount.
4. The salary is calculated using these rules:
   - **Full-Time employee:** Gross salary = Basic + HRA (20% of basic) + DA (10% of basic). PF (12% of basic) is deducted. Net salary = Gross - PF.
   - **Part-Time employee:** Salary = Pay per hour x Hours worked. There are no deductions. The program asks for the hours worked when calculating the salary or generating a payslip.
5. When a payslip is generated, it is shown on the screen and also saved in `payslips.txt`.
6. After every change, the employee data is saved to `employees.csv` automatically.
7. Invalid input (wrong employee ID, empty name, negative pay, file errors) is handled with exception handling, so the program does not crash.

**Example:** For a Full-Time employee with a basic salary of 25000: HRA = 5000, DA = 2500, Gross = 32500, PF = 3000, Net = 29500.

## How to run the project

**Requirements:** Python 3.8 or above. No extra libraries are needed.

**On your computer:**

```
python employee_payroll_system.py
```

**On Google Colab:**

1. Paste the code into a cell and run it.
2. Use the menu by typing a number and pressing Enter.
3. Choose option 6 to exit and save. The `employees.csv` and `payslips.txt` files will be created in the Colab files panel.

## Classes used

| Class | Type | Purpose |
|---|---|---|
| `PayrollError` | Custom exception | Raised when an action cannot be completed (employee not found, invalid type, etc.) |
| `Employee` | Abstract base class (`abc`) | Defines the common structure and salary calculation, with private attributes and abstract methods `employee_type()`, `earnings()` and `deductions()` |
| `FullTimeEmployee` | Derived class | Inherits from `Employee`. Monthly salary with HRA, DA, and PF deduction |
| `PartTimeEmployee` | Derived class | Inherits from `Employee`. Pay per hour multiplied by hours worked |
| `Payroll` | Manager class | Stores all employees and handles adding, searching, generating payslips, and saving data |

## Main features implemented

- **Add employees:** adds a Full-Time or Part-Time employee with an automatic ID
- **Calculate salary:** shows the gross salary, deductions, and net salary of an employee
- **Generate payslips:** creates a detailed payslip and saves it in `payslips.txt`
- **Search employees:** finds employees by name (not case-sensitive) or by ID
- **Display all employees:** lists every employee in the system
- **Save payroll data:** reads and writes data using `employees.csv` and `payslips.txt`

## OOP concepts demonstrated

| Concept | Where it is used |
|---|---|
| Classes & Objects | `Employee`, `FullTimeEmployee`, `PartTimeEmployee`, `Payroll` |
| Encapsulation | Private attributes (`__name`, `__base_pay`, `__hours_worked`) with getters and setters using `@property` |
| Inheritance | `FullTimeEmployee` and `PartTimeEmployee` inherit from `Employee` |
| Abstraction | `Employee` is an abstract class using the `abc` module |
| File Handling | Data is read from and written to `employees.csv` (CSV) and `payslips.txt` (text) |
| Exception Handling | `PayrollError`, `FileNotFoundError`, `ValueError`, and `OSError` are handled |

## Program output (Screenshots)

### 1. Main menu
The program shows the menu and asks the user to enter a choice.

![Main Menu](https://github.com/Nadeem7361/EMPLOYEE-PAYROLL-SYSTEM/blob/ba5d9c8d09753542addc3207205b19e054363856/ENTER_YOUR_CHOICE.png
)

### 2. Add employee (Choice 1)
The user enters the name, employee type, and pay. An employee ID is generated.

![Add Employee](https://github.com/Nadeem7361/EMPLOYEE-PAYROLL-SYSTEM/blob/ba5d9c8d09753542addc3207205b19e054363856/ADD_EMPLOYEE.png
)

### 3. Calculate salary (Choice 2)
The gross salary, deductions, and net salary of the employee are displayed.

![Calculate Salary](https://github.com/Nadeem7361/EMPLOYEE-PAYROLL-SYSTEM/blob/ba5d9c8d09753542addc3207205b19e054363856/CALCULATE_SALARY.png
)

### 4. Generate payslip (Choice 3)
A detailed payslip is displayed and saved in `payslips.txt`.

![Generate Payslip](https://github.com/Nadeem7361/EMPLOYEE-PAYROLL-SYSTEM/blob/ba5d9c8d09753542addc3207205b19e054363856/PAYSLIP_GENERATED.png
)

### 5. Search employees (Choice 4)
The user searches by name or ID, and the matching employees are displayed.

![Search Employees](https://github.com/Nadeem7361/EMPLOYEE-PAYROLL-SYSTEM/blob/ba5d9c8d09753542addc3207205b19e054363856/SEARCH_EMPLOYEES.png
)

### 6. Display all employees (Choice 5)
All employees in the system are listed.

![Display All Employees](https://github.com/Nadeem7361/EMPLOYEE-PAYROLL-SYSTEM/blob/ba5d9c8d09753542addc3207205b19e054363856/DISPLAY_EMPLOYEES.png
)

### 7. Exit and save data (Choice 6)
The data is saved and the program closes.

![Exit and Save](https://github.com/Nadeem7361/EMPLOYEE-PAYROLL-SYSTEM/blob/ba5d9c8d09753542addc3207205b19e054363856/EXIT_PROGRAM.png
)

## Project files

```
employee_payroll_system/
├── employee_payroll_system.py   # main program
├── employees.csv                # saved employee records
├── payslips.txt                 # generated payslips
├── screenshots/                 # output screenshots
└── README.md                    # project documentation
```
