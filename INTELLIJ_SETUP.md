# IntelliJ IDEA Import and Setup Guide

## Prerequisites

Before importing the project, ensure you have:

1. ✅ IntelliJ IDEA (Community or Ultimate Edition)
2. ✅ Java JDK 11 or higher installed
3. ✅ MySQL 8.0 or higher installed and running
4. ✅ Maven 3.6 or higher (usually bundled with IntelliJ)

## Step-by-Step Import Instructions

### Step 1: Download and Extract Project

1. Download the `revpassword-manager.zip` file
2. Extract it to a location of your choice (e.g., `C:\Projects\` or `~/Projects/`)
3. Remember the extraction path

### Step 2: Open IntelliJ IDEA

1. Launch IntelliJ IDEA
2. If you see the Welcome screen:
   - Click **"Open"**
3. If you have a project already open:
   - Click **File → Open**

### Step 3: Open the Project

1. Navigate to the extracted `revpassword-manager` folder
2. **Important**: Select the `revpassword-manager` folder itself (not files inside it)
3. Click **"OK"**

### Step 4: Import as Maven Project

IntelliJ should automatically detect it as a Maven project:

1. You'll see a notification: **"Maven projects need to be imported"**
2. Click **"Import Changes"** or **"Enable Auto-Import"**
3. Wait for Maven to download all dependencies (this may take a few minutes)
4. You'll see progress in the bottom right corner

**Alternative if auto-import doesn't work:**
1. Right-click on `pom.xml` in the Project view
2. Select **"Add as Maven Project"**

### Step 5: Configure Project SDK

1. Go to **File → Project Structure** (or press `Ctrl+Alt+Shift+S` / `Cmd+;` on Mac)
2. Under **"Project"** section:
   - **Project SDK**: Select Java 11 or higher
     - If not available, click **"Add SDK" → "Download JDK"**
     - Choose version 11 or higher
   - **Project language level**: Set to "11 - Local variable syntax for lambda parameters"
3. Click **"Apply"** and **"OK"**

### Step 6: Verify Maven Configuration

1. Open the Maven tool window:
   - **View → Tool Windows → Maven** (or click the "M" icon on the right side)
2. You should see the project structure with:
   - Dependencies
   - Lifecycle
   - Plugins
3. Click the refresh icon (circular arrows) to reload Maven project

### Step 7: Set up MySQL Database

1. Open MySQL Workbench or MySQL command line
2. Run the schema file:
   ```sql
   source /path/to/revpassword-manager/src/main/resources/schema.sql
   ```
   Or copy and paste the contents directly into MySQL Workbench

3. Verify the database was created:
   ```sql
   SHOW DATABASES;
   USE revpassword_db;
   SHOW TABLES;
   ```

### Step 8: Configure Database Connection

1. Navigate to `src/main/resources/database.properties`
2. Update with your MySQL credentials:
   ```properties
   db.url=jdbc:mysql://localhost:3306/revpassword_db
   db.username=YOUR_MYSQL_USERNAME
   db.password=YOUR_MYSQL_PASSWORD
   db.driver=com.mysql.cj.jdbc.Driver
   ```
3. Save the file

### Step 9: Build the Project

**Option A: Using Maven Tool Window**
1. Open Maven tool window
2. Expand **Lifecycle**
3. Double-click **clean**
4. Double-click **install**
5. Check the **Run** tab at the bottom for build output
6. You should see **"BUILD SUCCESS"**

**Option B: Using Terminal**
1. Open Terminal in IntelliJ (**View → Tool Windows → Terminal**)
2. Run:
   ```bash
   mvn clean install
   ```
3. Wait for build to complete

**Option C: Using Run Menu**
1. Click **Build → Rebuild Project**

### Step 10: Run Tests

1. In Project view, navigate to `src/test/java`
2. Right-click on `com.revature.revpassword` package
3. Select **"Run 'Tests in 'com.revature.revpassword''"**
4. Test results will appear in the Run window
5. All tests should pass ✅

### Step 11: Run the Application

**Method 1: Using Main Class**
1. Navigate to `src/main/java/com/revature/revpassword/MainApplication.java`
2. Right-click on the file
3. Select **"Run 'MainApplication.main()'"**
4. The console will appear at the bottom
5. Follow the on-screen prompts

**Method 2: Using Maven**
1. Open Terminal in IntelliJ
2. Run:
   ```bash
   mvn exec:java -Dexec.mainClass="com.revature.revpassword.MainApplication"
   ```

**Method 3: Create Run Configuration**
1. Click **Run → Edit Configurations**
2. Click the **"+"** button and select **"Application"**
3. Name it: "RevPassword Manager"
4. Main class: `com.revature.revpassword.MainApplication`
5. Click **"Apply"** and **"OK"**
6. Now you can run using the green play button in the toolbar

## Troubleshooting

### Problem 1: "Cannot resolve symbol" errors

**Solution:**
1. **File → Invalidate Caches / Restart**
2. Select **"Invalidate and Restart"**
3. Wait for IntelliJ to reindex the project

### Problem 2: Maven dependencies not downloading

**Solution:**
1. Check internet connection
2. Open Maven tool window
3. Click refresh icon (circular arrows)
4. Or run in terminal:
   ```bash
   mvn clean install -U
   ```

### Problem 3: Database connection failed

**Solution:**
1. Verify MySQL is running:
   ```bash
   # Windows
   net start MySQL80
   
   # Mac/Linux
   sudo systemctl start mysql
   ```
2. Check credentials in `database.properties`
3. Test connection in MySQL Workbench
4. Verify database `revpassword_db` exists

### Problem 4: "java: package does not exist" errors

**Solution:**
1. Right-click on project root
2. Select **"Maven → Reload Project"**
3. Or run:
   ```bash
   mvn clean install
   ```

### Problem 5: Tests failing

**Solution:**
1. Ensure all dependencies are downloaded
2. Check if database is running (some tests might need it)
3. Run tests individually to isolate the issue
4. Check test output for specific error messages

### Problem 6: Application won't run

**Solution:**
1. Verify database is set up correctly
2. Check `database.properties` configuration
3. Ensure port 3306 is not blocked
4. Check logs in `logs/revpassword.log`

## Verifying Successful Setup

✅ **Checklist:**
- [ ] Project imported without errors
- [ ] All dependencies downloaded (check Maven tool window)
- [ ] No red underlines in code
- [ ] Project builds successfully (`mvn clean install`)
- [ ] All tests pass
- [ ] Database connection works
- [ ] Application runs and shows welcome menu

## Project Structure in IntelliJ

After successful import, you should see:

```
revpassword-manager/
├── 📁 .idea/                    (IntelliJ configuration)
├── 📁 src/
│   ├── 📁 main/
│   │   ├── 📁 java/
│   │   │   └── 📁 com/revature/revpassword/
│   │   │       ├── 📁 controller/
│   │   │       ├── 📁 dao/
│   │   │       ├── 📁 model/
│   │   │       ├── 📁 service/
│   │   │       ├── 📁 util/
│   │   │       └── 📄 MainApplication.java
│   │   └── 📁 resources/
│   │       ├── 📄 database.properties
│   │       ├── 📄 log4j2.xml
│   │       └── 📄 schema.sql
│   └── 📁 test/
│       └── 📁 java/
├── 📁 target/                   (compiled classes)
├── 📁 docs/
├── 📄 pom.xml                   (Maven configuration)
└── 📄 README.md
```

## Next Steps

1. **Explore the Code:**
   - Start with `MainApplication.java`
   - Follow the flow through Controller → Service → DAO

2. **Test the Application:**
   - Register a new user
   - Add some passwords
   - Try the password generator
   - Set up security questions

3. **Review Documentation:**
   - Read `README.md` for features
   - Check `docs/ERD.md` for database schema
   - Review `docs/Architecture.md` for system design

4. **Modify and Experiment:**
   - Try adding new features
   - Improve the UI
   - Add more validation rules
   - Enhance security features

## Useful IntelliJ Shortcuts

| Action | Windows/Linux | Mac |
|--------|---------------|-----|
| Run | Shift+F10 | Ctrl+R |
| Debug | Shift+F9 | Ctrl+D |
| Build Project | Ctrl+F9 | Cmd+F9 |
| Find Class | Ctrl+N | Cmd+O |
| Find File | Ctrl+Shift+N | Cmd+Shift+O |
| Go to Declaration | Ctrl+B | Cmd+B |
| Project Structure | Ctrl+Alt+Shift+S | Cmd+; |
| Terminal | Alt+F12 | Option+F12 |

## Support

If you encounter any issues:

1. Check the troubleshooting section above
2. Review error messages carefully
3. Check `logs/revpassword.log` for detailed error information
4. Verify all prerequisites are met
5. Contact your Revature trainer for assistance

---

**Congratulations! Your development environment is ready!** 🎉

You can now start working with the RevPassword Manager application.
