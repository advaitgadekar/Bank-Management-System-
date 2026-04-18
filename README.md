# Bank Management System

A Java-based desktop application that simulates ATM and core banking operations. Built with Java Swing for the GUI, JDBC for database connectivity, and MySQL as the backend.

---

## What it does

The system lets users create an account, log in with a PIN, and perform standard banking operations through a clean desktop interface. It's designed to mirror the kind of functionality you'd find on a real ATM, without the hardware.

**Features:**
- User registration and account creation
- Secure PIN-based login and authentication
- Cash deposits and withdrawals
- Fast cash (quick withdrawal options)
- Balance inquiry
- Mini-statement (recent transaction history)
- PIN change

---

## Tech Stack

| Layer | Tool |
|---|---|
| Language | Java |
| GUI | Java Swing (AWT) |
| Database | MySQL |
| DB Connectivity | JDBC |
| IDE | IntelliJ IDEA |

---

## Project Structure

```
Bank Management System/
├── src/
│   ├── Login.java               # Entry point, PIN authentication
│   ├── Signup.java              # New user registration (personal details)
│   ├── Signup2.java             # Registration continued (additional info)
│   ├── Signup3.java             # Account setup and confirmation
│   ├── Transactions.java        # Main transaction menu
│   ├── Deposit.java             # Deposit functionality
│   ├── Withdrawal.java          # Cash withdrawal
│   ├── FastCash.java            # Quick withdrawal options
│   ├── BalanceEnquiry.java      # Balance check
│   ├── MiniStatement.java       # Recent transaction history
│   ├── PinChange.java           # PIN update
│   └── Conn.java                # MySQL database connection class
├── out/production/
└── Bank Management System.iml
```

---

## Getting Started

### Prerequisites

- JDK 8 or higher
- MySQL Server
- IntelliJ IDEA (or any Java IDE)
- MySQL Connector/J (JDBC driver)

### Setup

1. Clone the repository

```bash
git clone https://github.com/advaitgadekar/Bank-Management-System-.git
cd Bank-Management-System-
```

2. Set up the MySQL database. Open MySQL and create a database:

```sql
CREATE DATABASE bankmanagement;
```

Then create the required tables:

```sql
USE bankmanagement;

CREATE TABLE signup (
    formno VARCHAR(20),
    name VARCHAR(30),
    fname VARCHAR(30),
    dob VARCHAR(20),
    gender VARCHAR(10),
    email VARCHAR(30),
    marital VARCHAR(20),
    address VARCHAR(40),
    city VARCHAR(20),
    pincode VARCHAR(20),
    state VARCHAR(20)
);

CREATE TABLE signuptwo (
    formno VARCHAR(20),
    religion VARCHAR(20),
    category VARCHAR(20),
    income VARCHAR(20),
    education VARCHAR(20),
    occupation VARCHAR(20),
    pan VARCHAR(20),
    aadhar VARCHAR(20),
    seniorcitizen VARCHAR(20),
    existingaccount VARCHAR(20)
);

CREATE TABLE signupthree (
    formno VARCHAR(20),
    cardnumber VARCHAR(30),
    pin VARCHAR(10),
    facility VARCHAR(100)
);

CREATE TABLE bank (
    pin VARCHAR(10),
    date VARCHAR(30),
    type VARCHAR(30),
    amount VARCHAR(20)
);
```

3. Update database credentials in `Conn.java`:

```java
Connection c = DriverManager.getConnection(
    "jdbc:mysql://localhost/bankmanagement", "root", "your_password"
);
```

4. Add the MySQL Connector/J JAR to your project's classpath in your IDE.

5. Run `Login.java` to launch the application.

---

## How it works

When a new user signs up, their details are collected across three registration screens and stored across the `signup`, `signuptwo`, and `signupthree` tables. A card number and PIN are auto-generated and assigned to their account.

On login, the card number and PIN are verified against the database. Once authenticated, the user lands on the transactions menu where they can perform any of the supported operations. Every deposit or withdrawal is logged in the `bank` table with a timestamp and transaction type, which is what powers the mini-statement view.

---

## Notes

- Make sure your MySQL server is running before launching the application
- The `Conn.java` file holds your database credentials — do not commit it with real passwords if you fork this
- Default database name used is `bankmanagement` — update `Conn.java` if you use a different name
