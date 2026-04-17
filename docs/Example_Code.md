## Example Code

> Note: This is an example code snippet to illustrate the architectural patterns and principles we will be following. It is not meant to be copy-pasted directly, but rather to serve as a reference for how to structure your code according to the layered architecture we discussed. Also note this is co authored by AI and may not be perfect. Always review and adapt to your specific use case.

---

## Application Flow

1. UI: JavaFX screens and user interactions
2. Controller: Translates UI events into backend operations and updates the UI with results.
3. Service: Contains business logic and rules, orchestrating operations between the UI and data access
4. DAO: Handles database interactions, isolating persistence logic from business logic.
5. Model: Plain data objects representing entities in the application (e.g., User, Product).
6. Database: SQLite for local data storage, accessed via JDBC.

### WFolder Structure (ASCII Diagram)

```
src
└── main
        ├── java
        │   ├── controller   // Controllers (e.g., LoginController.java)
        │   ├── dao          // DAOs (e.g., UserDAO.java)
        │   ├── service      // Services (e.g., AuthService.java)
        │   └── model        // Models (e.g., User.java)
        └── resources
                ├── db
                │   └── migration   // SQL migration scripts
                ├── login.fxml      // UI layout
                └── style.css       // Styles
```

---

### 1. The JavaFX FXML UI (The Eyes and Ears)

Only user interaction and display logic lives here.  
_This is not runnable code. It’s an architectural pattern._

```java
// Layer: UI
public class LoginView {
    private final LoginController controller;

    public LoginView(LoginController controller) {
        this.controller = controller;
        // Set up JavaFX UI components (TextFields, Buttons, etc.)
        // Add event listeners that call controller.handleLogin(...)
    }
}
```

---

### 2. The Controller (The Nervous System)

Only triggers. "User clicked button."  
Check for nulls, empty strings, or invalid input here, but no business logic.

```java
// Layer: Controller
public class LoginController {
    private final AuthService authService; // Injected!

    public LoginController(AuthService authService) {
        this.authService = authService;
    }

    public void handleLogin(String user, String pass) {
        if (authService.login(user, pass)) {
            // Forward to Dashboard
        } else {
            // Show Alert
        }
    }
}
```

---

### 3. The DAO (The Hand)

Only SQL lives here. Database access code, mapping ResultSets to Models, and nothing else.

```java
// Layer: DAO
public class UserDAO {
    public User findByUsername(String username) {
        // Example using prepared statement (real code would handle exceptions)
        // try (PreparedStatement stmt = conn.prepareStatement("SELECT * FROM users WHERE username = ?")) { ... }
        // Map ResultSet to User object
        return new User(username, "password");
    }

    public void updatePassword(String username, String newPassword) {
        // Example: "UPDATE users SET password = ? WHERE username = ?"
        // Use prepared statements to avoid SQL injection
    }
}
```

---

### 4. The Service (The Brain)

Only business rules here. "Check if password matches," "Hash the password."

```java
// Layer: Service
public class AuthService {
    private final UserDAO userDAO;

    public AuthService(UserDAO userDAO) {
        this.userDAO = userDAO;
    }

    public boolean login(String username, String password) {
        User user = userDAO.findByUsername(username);
        if (user == null) return false;
        // Compare password (in real code, use secure hash comparison)
        return password.equals(user.getPassword());
    }

    public void updatePassword(String username, String newPassword) {
        // Add business rules if needed (e.g., password strength)
        userDAO.updatePassword(username, newPassword);
    }
}
```

---

### 5. Models (The Data Carriers)

Plain data objects with no logic. Just getters, setters, and constructors.  
_Immutable models are preferred. If you must mutate, document why._

```java
// Layer: Model
public class User {
    private final String username;
    private final String password;

    public User(String username, String password) {
        this.username = username;
        this.password = password;
    }

    public String getUsername() { return username; }
    public String getPassword() { return password; }
}
```

---

### 6. Database (The Storage)

SQLite accessed via JDBC. No SQL queries outside of the DAO.

```sql
-- Layer: Database
CREATE TABLE users (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    username TEXT UNIQUE NOT NULL,
    password TEXT NOT NULL
);
```

_Note: Use prepared statements for all database interactions to prevent SQL injection._

---

**This is an architectural reference. Adapt the patterns, not the literal code.**
