# Finance-Tracker

<img width="526" height="351" alt="Screenshot 2026-02-24 090641" src="https://github.com/user-attachments/assets/caba73a5-772f-4233-9399-548d8e558c5a" />
<img width="752" height="392" alt="Screenshot 2026-02-24 091632" src="https://github.com/user-attachments/assets/88893401-7fc6-4092-86b5-947507bb63ba" />

A comprehensive personal finance management application built with Java Swing, designed for tracking income, expenses, and financial transfers with an intuitive GUI interface.

## Overview

Finance-Tracker is an Object-Oriented Programming (OOP) group assignment project that provides users with a secure, multi-user personal finance management system. The application allows users to track their financial transactions, categorize expenses and income, generate reports, and visualize financial data through interactive charts.

## Features

- **User Authentication**: Secure login and registration system with encrypted passwords
- **Income Tracking**: Record and manage income entries with categories and dates
- **Expense Management**: Track and categorize expenses with detailed notes
- **Transfers**: Monitor fund transfers between accounts or categories
- **Financial Reports**: Generate comprehensive financial reports in PDF and Excel formats
- **Data Visualization**: Interactive 3D pie charts for expense and income distribution analysis
- **Dynamic Dashboard**: Real-time balance updates and financial summaries
- **Multi-user Support**: Each user has isolated financial data
- **Category Management**: Flexible category creation and management for transactions
- **Data Persistence**: MySQL database integration for secure data storage

## Project Structure

```
Finance-Tracker/
├── group assignment/
│   ├── src/group/assignment/
│   │   ├── DBconnection.java          # Database connection management
│   │   ├── Encryption.java            # AES encryption for password security
│   │   ├── login.java                 # Login window GUI
│   │   ├── registration.java          # User registration window
│   │   ├── tracker.java               # Main dashboard/tracker window
│   │   ├── Income.java                # Income management window
│   │   ├── Expenses.java              # Expense management window
│   │   ├── Transfers.java             # Transfer management window
│   │   ├── Reports.java               # Report generation functionality
│   │   ├── UserThread.java            # Threading support
│   │   └── [.form files]              # NetBeans GUI form definitions
│   ├── build.xml                       # Ant build configuration
│   ├── manifest.mf                     # JAR manifest file
│   └── nbproject/                      # NetBeans project configuration
├── jar files/                          # Required library JAR files
│   ├── apache-log4j-2.17.1/           # Logging framework
│   └── poi-bin-5.2.2/                 # Apache POI for Excel generation
├── mysql-connector-java-8.0.17/       # MySQL JDBC driver
├── finance tracker.sql                 # Database schema initialization script
└── README.md                           # This file
```

## System Requirements

- **Java**: JDK 8 or higher
- **Database**: MySQL 5.7 or higher
- **Operating System**: Windows, macOS, or Linux with Java support
- **RAM**: 512 MB minimum
- **Disk Space**: 200 MB minimum

## Dependencies

The project uses the following external libraries:

1. **MySQL Connector/J 8.0.17** - Database connectivity
   - Used for JDBC connection to MySQL

2. **Apache POI 5.2.2** - Excel file generation
   - Create and export financial reports to .xlsx format

3. **Apache Log4j 2.17.1** - Logging framework
   - Application error and info logging

4. **iText** - PDF generation
   - Generate PDF financial reports

5. **JFreeChart** - Data visualization
   - Create 3D pie charts for financial analysis
   - Display expense and income distribution

6. **PDFBox** - PDF handling
   - PDF document manipulation

## Installation Instructions

### 1. Database Setup

```sql
-- Run the provided SQL script to create the database schema
mysql -u root -p < finance_tracker.sql
```

### 2. Project Configuration

1. Open the project in NetBeans IDE or your preferred Java IDE
2. Build the project using the build.xml file or IDE build tools
3. Ensure all JAR files in the `jar files/` directory are added to the project classpath

### 3. Configure Database Connection

Edit the database connection credentials in `DBconnection.java`:

```java
private static final String JDBC_URL = "jdbc:mysql://localhost:3306/finance_tracker?zeroDateTimeBehavior=convertToNull";
private static final String USERNAME = "root";
private static final String PASSWORD = "your_password_here";
```

**Important**: Update the `PASSWORD` field with your actual MySQL password.

### 4. Compile and Run

Option A - Using NetBeans:
- Open project → Right-click → Build and Run

Option B - Using Command Line:
```bash
ant clean
ant build
ant run
```

## Usage Guide

### Starting the Application

1. Launch the application
2. The login window will appear
3. New users should click "Register" to create an account
4. Existing users enter username and password to log in

### Main Dashboard (Tracker)

- Displays current balance and financial overview
- Quick access to Income, Expenses, Transfers, and Reports modules
- Real-time balance updates

### Income Management

- Add new income entries with amount, category, and date
- Create custom income categories
- View all income transactions in a table
- Edit or delete existing income records

### Expense Management

- Record expenses with category classification
- Add detailed notes for each expense
- Track spending patterns by category
- Modify or remove expense entries

### Transfers

- Manage fund transfers between different categories or accounts
- Track transfer history
- Monitor transfer destinations

### Reports

- Generate comprehensive financial reports
- Export data to PDF format
- Export data to Excel (.xlsx) format
- Options for filtering by date range and categories

### Data Visualization

- View 3D pie charts showing expense distribution
- Analyze income breakdown by category
- Interactive chart interface for deeper insights

## Security Features

### Password Encryption

The application uses **AES (Advanced Encryption Standard)** encryption for password security:

```java
// AES Encryption with 16-byte key
private static String keyString = "ThisIsAKeyForDem"; // 16 characters
```

**Note**: Passwords are encrypted before storage in the database using PKCS5Padding.

### Multi-User Data Isolation

Each user's financial data is completely isolated using username-based queries:

```sql
SELECT * FROM [table_name] WHERE user_name = ?
```

## Database Schema

The application uses the following main tables:

- `user_table` - User account information (username, encrypted password)
- `income` - Income transaction records
- `expenses` - Expense transaction records
- `transfers` - Transfer records
- `income_categories` - Predefined and custom income categories
- `expense_categories` - Predefined and custom expense categories

## Class Overview

| Class | Purpose |
|-------|---------|
| `DBconnection` | Manages MySQL database connections using JDBC |
| `Encryption` | Handles AES encryption/decryption for sensitive data |
| `login` | Login authentication GUI window |
| `registration` | New user registration GUI window |
| `tracker` | Main dashboard GUI with navigation |
| `Income` | Income transaction management GUI |
| `Expenses` | Expense transaction management GUI |
| `Transfers` | Fund transfer management GUI |
| `Reports` | Report generation (PDF/Excel export) |
| `UserThread` | Threading utilities for async operations |

## Troubleshooting

### Database Connection Issues
- Verify MySQL service is running
- Check credentials in `DBconnection.java`
- Ensure `finance_tracker` database exists
- Verify firewall allows localhost:3306

### Missing JAR Files
- Ensure all JAR files are in the `jar files/` directory
- Add JAR files to project classpath
- Rebuild the project

### Icon Not Loading
- Verify `./src/pics/pic17.png` exists in the correct location
- The application continues to work if image is not found

### Password Encryption Issues
- Ensure encryption key is exactly 16 characters
- Verify AES algorithm is available in your Java installation

## Building from Source

```bash
# Clean previous builds
ant clean

# Compile the project
ant build

# Create JAR file
ant jar

# Run the application
ant run
```

## Development Notes

- Project developed using NetBeans IDE
- GUI forms built with Swing and NetBeans Form Editor (.form files)
- Supports concurrent user sessions
- Transaction data is user-specific and role-independent

## Future Enhancement Possibilities

- Budget planning and alerts
- Recurring transaction automation
- Data import/export functionality
- Mobile application version
- Dashboard export to image files
- Transaction search and filter enhancements
- Cloud database synchronization

## License

Please refer to the LICENSE file in the project root.

## Team Members

- P H D B Nayanakantha
- R M J Jayashan 
- N T P G B Upethra 
- H D S J Dharmasiri 
- L B Alles 

This is a collaborative group repository where all team members contribute to the development of the Finance-Tracker application.




