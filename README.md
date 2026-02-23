# RevPassword Manager

A secure, console-based password management application built with Java, JDBC, MySQL, Log4j, and JUnit.

## Overview

RevPassword Manager is a comprehensive password vault application that allows users to securely store, manage, and retrieve passwords for their various online accounts. The application emphasizes security through password encryption, master password protection, and security question-based recovery.

## Features

### User Management
- ✅ User registration with strong password requirements
- ✅ Secure login with master password
- ✅ Profile management (update email, full name)
- ✅ Master password change functionality
- ✅ Password recovery through security questions

### Password Vault
- ✅ Add new password entries with encryption
- ✅ List all stored passwords
- ✅ View password details (requires master password re-entry)
- ✅ Update existing passwords
- ✅ Delete password entries
- ✅ Search passwords by account name

### Security Features
- ✅ Strong password generation with customizable parameters
- ✅ BCrypt password hashing for master passwords
- ✅ AES encryption for stored passwords
- ✅ Security questions for account recovery
- ✅ Verification codes for sensitive operations (with expiration)
- ✅ Master password re-verification for viewing passwords

### Additional Features
- ✅ Comprehensive logging with Log4j 2
- ✅ Input validation
- ✅ User-friendly console interface
- ✅ Audit trail capability

## Technologies Used

- **Java 11**: Core programming language
- **Maven**: Build and dependency management
- **MySQL 8.0**: Database for persistent storage
- **JDBC**: Database connectivity
- **Log4j 2**: Logging framework
- **JUnit 5**: Unit testing framework
- **BCrypt**: Password hashing
- **AES**: Symmetric encryption for passwords

## Project Structure

```
revpassword-manager/
├── src/
│   ├── main/
│   │   ├── java/com/revature/revpassword/
│   │   │   ├── controller/
│   │   │   │   └── MainController.java
│   │   │   ├── dao/
│   │   │   │   ├── UserDAO.java
│   │   │   │   ├── PasswordVaultDAO.java
│   │   │   │   ├── SecurityQuestionDAO.java
│   │   │   │   └── VerificationCodeDAO.java
│   │   │   ├── model/
│   │   │   │   ├── User.java
│   │   │   │   ├── PasswordEntry.java
│   │   │   │   ├── SecurityQuestion.java
│   │   │   │   └── VerificationCode.java
│   │   │   ├── service/
│   │   │   │   ├── UserService.java
│   │   │   │   ├── PasswordVaultService.java
│   │   │   │   └── SecurityService.java
│   │   │   ├── util/
│   │   │   │   ├── DatabaseConnection.java
│   │   │   │   ├── EncryptionUtil.java
│   │   │   │   ├── PasswordHashUtil.java
│   │   │   │   ├── PasswordGenerator.java
│   │   │   │   └── ValidationUtil.java
│   │   │   └── MainApplication.java
│   │   └── resources/
│   │       ├── database.properties
│   │       ├── log4j2.xml
│   │       └── schema.sql
│   └── test/
│       └── java/com/revature/revpassword/
│           └── util/
│               ├── PasswordGeneratorTest.java
│               ├── PasswordHashUtilTest.java
│               ├── EncryptionUtilTest.java
│               └── ValidationUtilTest.java
├── docs/
│   ├── ERD.md
│   └── Architecture.md
├── pom.xml
└── README.md
```

## Prerequisites

- Java JDK 11 or higher
- Maven 3.6 or higher
- MySQL 8.0 or higher
- IntelliJ IDEA (recommended) or any Java IDE

## Database Setup

1. Install MySQL and start the MySQL service

2. Create the database and tables:
```bash
mysql -u root -p < src/main/resources/schema.sql
```

3. Update database credentials in `src/main/resources/database.properties`:
```properties
db.url=jdbc:mysql://localhost:3306/revpassword_db
db.username=your_username
db.password=your_password
```

## Installation & Setup

### Method 1: Using IntelliJ IDEA

1. **Download/Clone the project**
   - Download the project as a ZIP file and extract it
   - Or clone from repository

2. **Import Project in IntelliJ**
   - Open IntelliJ IDEA
   - Click `File` → `Open`
   - Navigate to the `revpassword-manager` folder
   - Select the folder and click `OK`
   - IntelliJ will automatically detect it as a Maven project

3. **Configure Maven**
   - IntelliJ will automatically start downloading dependencies
   - Wait for the Maven import to complete
   - You should see "Maven projects need to be imported" notification
   - Click `Import Changes` or enable `Auto-Import`

4. **Verify Project Structure**
   - Ensure the JDK is set to Java 11 or higher
   - Go to `File` → `Project Structure` → `Project`
   - Set Project SDK to Java 11+
   - Set Project language level to 11

5. **Setup Database**
   - Make sure MySQL is running
   - Execute the schema.sql file to create the database
   - Update database.properties with your MySQL credentials

6. **Build the Project**
   - Open Maven tool window (View → Tool Windows → Maven)
   - Click `Lifecycle` → `clean`
   - Click `Lifecycle` → `install`
   - This will compile the code and run tests

7. **Run the Application**
   - Navigate to `src/main/java/com/revature/revpassword/MainApplication.java`
   - Right-click on the file
   - Select `Run 'MainApplication.main()'`

### Method 2: Using Command Line

1. **Extract and navigate to project**
```bash
cd revpassword-manager
```

2. **Build the project**
```bash
mvn clean install
```

3. **Run the application**
```bash
mvn exec:java -Dexec.mainClass="com.revature.revpassword.MainApplication"
```

Or compile and run directly:
```bash
mvn clean package
java -jar target/revpassword-manager-1.0.0.jar
```

## Running Tests

### In IntelliJ IDEA:
- Right-click on `src/test/java` folder
- Select `Run 'All Tests'`

### Using Maven:
```bash
mvn test
```

## Usage Guide

### 1. Registration
```
1. Choose option 1 (Register) from main menu
2. Enter username (3-20 alphanumeric characters)
3. Enter email address
4. Enter full name
5. Create a strong master password (min 8 chars, with uppercase, lowercase, digit, special char)
6. Confirm master password
7. Optionally set up security questions
```

### 2. Login
```
1. Choose option 2 (Login) from main menu
2. Enter your username
3. Enter your master password
```

### 3. Managing Passwords
```
After login, you can:
- List all passwords: View all stored account names
- View password details: See encrypted password (requires master password)
- Add new password: Store a new account password
- Update password: Modify existing entry
- Delete password: Remove an entry
- Search passwords: Find passwords by account name
```

### 4. Generate Strong Password
```
1. Select option 7 from user menu
2. Specify password length (8-32 characters)
3. Choose character types to include:
   - Uppercase letters
   - Lowercase letters
   - Digits
   - Special characters
4. Use the generated password or create your own
```

### 5. Security Questions
```
1. Select option 8 (Manage Security Questions)
2. Add at least 2 security questions
3. These will be used for password recovery
```

## Security Features

### Password Strength Requirements
- Minimum 8 characters
- At least one uppercase letter
- At least one lowercase letter
- At least one digit
- At least one special character

### Encryption
- Master passwords: BCrypt hashing (cost factor 12)
- Stored passwords: AES-256 encryption
- Security question answers: BCrypt hashing

### Additional Security
- Master password re-verification for viewing passwords
- Verification codes with expiration
- Security questions for account recovery
- Comprehensive audit logging

## Troubleshooting

### Database Connection Issues
```
Error: Unable to connect to database
Solution: 
1. Ensure MySQL service is running
2. Verify database credentials in database.properties
3. Check if database 'revpassword_db' exists
4. Verify MySQL is listening on port 3306
```

### Maven Build Failures
```
Error: Dependencies cannot be resolved
Solution:
1. Check internet connection
2. Run: mvn clean install -U
3. Delete .m2/repository folder and rebuild
```

### Class Not Found Error
```
Error: ClassNotFoundException
Solution:
1. Rebuild the project: mvn clean install
2. In IntelliJ: File → Invalidate Caches → Invalidate and Restart
```

## Testing

The project includes comprehensive unit tests for:
- Password generation functionality
- Password hashing and verification
- Encryption and decryption
- Input validation

Run all tests:
```bash
mvn test
```

View test coverage:
```bash
mvn clean test jacoco:report
```

## Architecture

The application follows a layered architecture:

1. **Presentation Layer**: Console-based UI (MainController)
2. **Service Layer**: Business logic (UserService, PasswordVaultService, SecurityService)
3. **Data Access Layer**: Database operations (DAOs)
4. **Utility Layer**: Helper classes for encryption, validation, etc.
5. **Model Layer**: Entity classes (User, PasswordEntry, etc.)

See [docs/Architecture.md](docs/Architecture.md) for detailed architecture diagram.

## Database Schema

See [docs/ERD.md](docs/ERD.md) for Entity-Relationship Diagram.

## Logging

Logs are stored in `logs/revpassword.log`

Log levels:
- **INFO**: General application flow
- **DEBUG**: Detailed debugging information
- **WARN**: Warning messages
- **ERROR**: Error messages

## Contributing

This is a training project for Revature associates. For contributions:
1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## License

This project is created for educational purposes as part of Revature training.

## Contact

For questions or issues, please contact your Revature trainer.

## Future Enhancements

- [ ] Password strength analyzer
- [ ] Password expiration reminders
- [ ] Multi-factor authentication
- [ ] Password sharing functionality
- [ ] Browser extension integration
- [ ] Mobile application
- [ ] Cloud backup and sync
- [ ] Biometric authentication

---

**Note**: This is a console-based application designed for learning purposes. For production use, additional security measures and features would be required.
