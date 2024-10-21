 Bank Management System - Mini Project
Overview
This project implements a **Bank Management System** using Python for database interaction and MySQL for backend data storage. The system enables users to create accounts, log in, deposit/withdraw money, transfer funds, check balances, and update account numbers. It automates many key banking operations and addresses several inefficiencies found in traditional banking systems.

Problem Statement
The current banking system has several inefficiencies such as:
- Extended transaction times
- High error rates
- Lack of centralized data storage
- Vulnerability to security threats

The Bank Management System aims to solve these issues by providing an integrated, secure, and efficient platform for bank operations.

Features
1. Create a bank account
2. User login with account number and password
3. Deposit and withdraw money
4. Transfer funds between accounts
5. Check balance
6. Update account details

Technologies Used
- **Python** for coding the application logic.
- **MySQL** for the backend database.
- **mysql.connector** module for connecting Python to the MySQL database.

Table Creation (MySQL)
The system stores data in a MySQL database. Below is the SQL table structure used:

sql
CREATE TABLE RECORDS(
  ACCONT_NO INT(4) PRIMARY KEY,
  PASSWORD INT(3),
  NAME VARCHAR(20),
  CR_AMT INT DEFAULT 0,
  WITHDRAWAL INT DEFAULT 0,
  BALANCE INT DEFAULT 0
);
```

Python Code
The Python code has two main phases:
1. **MySQL Connectivity**: Connects to the database and creates the required table.
2. **Bank Management Operations**: Manages account creation, login, transactions (deposit/withdrawal/transfer), and balance checks.

### Example: MySQL Connectivity
```python
import mysql.connector as sql

conn = sql.connect(host='localhost', user='root', password='1234', database='ATM_MACHINE')

if conn.is_connected():
    print("Successfully connected")

c1 = conn.cursor()
mn = """
    CREATE TABLE RECORDS(
        ACCONT_NO INT(4) PRIMARY KEY,
        PASSWORD INT(3),
        NAME VARCHAR(20),
        CR_AMT INT DEFAULT 0,
        WITHDRAWAL INT DEFAULT 0,
        BALANCE INT DEFAULT 0
    )
"""
c1.execute(mn)
print("Successfully created")
```

Example: Account Creation in Python
```python
op = int(input("Enter your choice:"))

if op == 1:
    m = int(input("Enter a 4-digit number as account number:"))
    cb = "SELECT * FROM records WHERE ACCONT_NO={}".format(m)
    c1.execute(cb)
    d = c1.fetchall()

    if len(d) == 0:
        name = input("Enter your name:")
        passw = int(input("Enter your password (4 digits):"))
        ab = "INSERT INTO records(ACCONT_NO, PASSWORD, NAME) VALUES({}, {}, '{}')".format(m, passw, name)
        c1.execute(ab)
        conn.commit()
        print("Account successfully created")
    else:
        print("Account number already exists")
```

Results
The system performs various banking operations like creating accounts, managing funds, and checking balances. Screenshots are included in the project report to demonstrate each operation.

Conclusion
This project provides a user-friendly, efficient, and secure solution for managing banking operations, ensuring data security and smooth customer experience.

References
1. Ayush Kumar, Tushar Sharma, Sagar Kumar, Dr Parveen Kumar, To study of bank management system, Journal of emerging technologies and innovative research (JETIR) May 2023, Volume 10, Issue 5.
2. Wang, L. and Wang, Y., 2022. Supply chain financial service management system based on block chain IoT data sharing and edge computing. Alexandria Engineering Journal, 61(1), pp.147-158.
3. MD.Faizan, MD.Aquil Amwar, Masrurul Haque, (2021), bank management system, International Journal of Engineering Research in Computer Science and Engineering (IJERCSE).

