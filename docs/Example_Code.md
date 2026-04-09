1. The Model (The Blood)
This is just data. No logic, no SQL, no UI.

public class User {
    private final String username;
    private final String passwordHash; // Store BCrypt hash, NEVER plaintext

    public User(String username, String passwordHash) {
        this.username = username;
        this.passwordHash = passwordHash;
    }
    // Getters only, no setters to keep immutability (except for password update via service)
    public String getUsername() { return username; }
    public String getPasswordHash() { return passwordHash; }
}

2. The DAO (The Hand)
Only SQL lives here. If you see a System.out or Alert, the layer is broken.

public class UserDAO {
    public User findByUsername(String username) {
        // "SELECT * FROM users WHERE username = ?"
        // Map ResultSet to User object
        return new User(username, "hash");
    }
}

3. The Service (The Brain)
Only business rules here. "Check if password matches," "Hash the password."
If you need to change how the database works, only touch UserDAO. Don't touch the Service. If you need to change how the UI works, only touch the Controller. Don't touch the Service.

public class AuthService {
    private final UserDAO userDAO;

    public AuthService(UserDAO userDAO) {
        this.userDAO = userDAO;
    }

    public boolean login(String username, String password) {
        User user = userDAO.findByUsername(username);
        if (user == null) return false;
        // "Verify hash using BCrypt"
        return BCrypt.checkpw(password, user.getPasswordHash());
    }
}

4. The Controller (The Nervous System)
Only triggers. "User clicked button."
check for nulls, empty strings, or invalid input here, but no business logic.

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

---

1. UI (View): "I take input." -> Calls Controller.
2. Controller: "I tell Service what to do." -> Calls Service.
3. Service: "I do the math and check the rules." -> Calls DAO.
4. DAO: "I talk to the Database, and pour it into a Model." → Returns the Model to the Service.
5. Model: "I am the data carrier. I hold the data in the right structure so the Service and UI can read it easily."

---