# RevPassword Manager - Quick Start Guide

## 🚀 Quick Setup (5 Minutes)

### 1️⃣ Import in IntelliJ IDEA
```
1. Open IntelliJ IDEA
2. Click "Open" 
3. Select the "revpassword-manager" folder
4. Click "OK"
5. Wait for Maven to import dependencies
```

### 2️⃣ Setup MySQL Database
```sql
-- In MySQL Workbench or command line:
mysql -u root -p < src/main/resources/schema.sql

-- Or copy-paste from schema.sql file
```

### 3️⃣ Configure Database Connection
```
Edit: src/main/resources/database.properties

db.url=jdbc:mysql://localhost:3306/revpassword_db
db.username=YOUR_USERNAME  # Change this
db.password=YOUR_PASSWORD  # Change this
```

### 4️⃣ Build the Project
```
In IntelliJ:
- Open Maven tool window (right sidebar)
- Click: Lifecycle → clean
- Click: Lifecycle → install
```

### 5️⃣ Run the Application
```
1. Navigate to: src/main/java/com/revature/revpassword/MainApplication.java
2. Right-click → Run 'MainApplication.main()'
3. Application starts in console!
```

## 📁 Project Structure Overview

```
revpassword-manager/
├── src/main/java/com/revature/revpassword/
│   ├── controller/      # UI Layer (Console interface)
│   ├── service/         # Business Logic Layer
│   ├── dao/             # Data Access Layer
│   ├── model/           # Entity Classes
│   ├── util/            # Utility Classes
│   └── MainApplication.java  # ⭐ START HERE
├── src/main/resources/
│   ├── database.properties   # 🔧 Configure this
│   ├── schema.sql           # 🗄️ Run this in MySQL
│   └── log4j2.xml
├── src/test/java/           # Unit Tests
├── docs/                    # Documentation
│   ├── ERD.md              # Database design
│   └── Architecture.md     # System architecture
└── pom.xml                 # Maven configuration
```

## 🎯 First Run - What to Do

### Create Your Account
```
1. Choose option 1 (Register)
2. Username: testuser
3. Email: test@example.com
4. Full Name: Test User
5. Master Password: Test@1234 (or create stronger one)
6. Set up 2 security questions
```

### Add Your First Password
```
1. Login with your account
2. Choose option 3 (Add New Password)
3. Account Name: Gmail
4. Username: yourname@gmail.com
5. Password: (press Enter to generate or type your own)
6. Website: https://gmail.com
7. Notes: My email account
```

### Generate a Strong Password
```
1. Choose option 7 (Generate Random Password)
2. Length: 16
3. Include uppercase: y
4. Include lowercase: y
5. Include digits: y
6. Include special chars: y
7. Copy the generated password
```

## 🔑 Key Features to Try

1. **List Passwords** - See all your stored accounts
2. **View Details** - See decrypted password (requires master password)
3. **Search** - Find passwords by account name
4. **Security Questions** - Set up for account recovery
5. **Update Profile** - Change email or name
6. **Change Master Password** - Update your master key

## 🛠️ Common Commands

### Build Project
```bash
mvn clean install
```

### Run Tests
```bash
mvn test
```

### Run Application
```bash
mvn exec:java -Dexec.mainClass="com.revature.revpassword.MainApplication"
```

### Package JAR
```bash
mvn clean package
java -jar target/revpassword-manager-1.0.0.jar
```

## ⚠️ Important Security Notes

1. **Master Password**: Never forget it! It cannot be recovered (only reset with security questions)
2. **Strong Passwords**: Use 8+ characters with uppercase, lowercase, digits, and special chars
3. **Security Questions**: Set up at least 2 for account recovery
4. **Database Access**: Keep your MySQL credentials secure

## 🐛 Troubleshooting

### "Database connection failed"
- ✅ Is MySQL running?
- ✅ Check credentials in database.properties
- ✅ Did you run schema.sql?

### "Maven dependencies not found"
- ✅ Check internet connection
- ✅ Click Maven refresh icon
- ✅ Run: mvn clean install -U

### "Cannot find main class"
- ✅ Build the project first
- ✅ Rebuild: mvn clean install
- ✅ Invalidate caches in IntelliJ

## 📚 Documentation Files

- **README.md** - Complete documentation
- **INTELLIJ_SETUP.md** - Detailed setup guide
- **docs/ERD.md** - Database schema
- **docs/Architecture.md** - System design

## 🎓 Learning Path

1. **Start**: MainApplication.java
2. **Follow**: MainController.java (see how UI works)
3. **Explore**: UserService.java (business logic)
4. **Understand**: UserDAO.java (database operations)
5. **Review**: Tests in src/test/java

## 💡 Tips

- Use IntelliJ's debugger to step through code
- Check logs/revpassword.log for detailed information
- Run tests to see how utilities work
- Experiment with the password generator
- Try adding new features!

## 🎉 You're Ready!

The application is now ready to use. Start exploring the code and enjoy learning!

For detailed documentation, see README.md and INTELLIJ_SETUP.md

---

**Happy Coding!** 🚀
