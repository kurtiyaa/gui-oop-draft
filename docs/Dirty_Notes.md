# Java Desktop application with database finals project overdelivery \& overengineered to impress (professor) and progress

> This document is intended for drafted architectural decision of how the project is planned, built, and decided.
> It is not part of the application runtime logic.

---

OOP Professor Criteria: A Simple Java desktop application with database

Q1. We want to practice Clean Architecture and Industry standards by separating our UI from our logic. Is it okay if we use JavaFX and Maven to organize our project? Also, are we allowed to use external libraries to handle eg. like pashword hashing for security(BCrypt), auto table setup and organization(), and code verification(CI/CD)

**CONSTRAINTS:**

- this is a grouped project
- the class is oop, cheating frameworks(electron) might be not allowed
- no using electron
- avoid using too much dependencies as much as possible
- groupmates are likely using windows
- group mates might not be technical
- the app all itself is only expecting 1 user
- i will do less of the coding an managing the achitectural system integrity and peer code reviews
- we will present the app live in class with my laptop probably offline

**PROJECT ARCHITECHTURE:**

- **Language + Runtime**: Java JDK **25 LTS** (lock major version; minor/patch can vary by environment).
- **Build + Project Structure**: Maven-based JavaFX desktop application.
- **Database**: SQLite via JDBC for a single-user local setup (portable and easy to run offline).
  - Include DB schema script.
  - Include migration scripts.
  - Include startup seed script.
  - Include ERD visuals/documentation.
- **Database Migration Tool**: Flyway (keeps SQL migration files separate from hardcoded app initialization).
- **Security**: BCrypt for password hashing + salting.
- **Testing**: JUnit integration tests for key workflows.
- **CI Pipeline**: GitHub Actions.
- **Packaging/Distribution**: `jpackage` to produce an app-image build for demo/use.

**SCRAPPED IDEA (DUE TO: OFFLINE, AND PROJECT SCOPE CONSTRAINTS)**:

- **curl testing**
- **Spring Boot + PostgreSQL** (later simplified to SQLite)
- **PostgreSQL containerized setup** (Docker - reduced scope)
- **PostgreSQL fallback on Pi via Tailscale VPN** (out of scope)
- **Chatbot with AI RAG + Vector DB** (out of scope)
- **Dedicated website** (Nginx + Cloudflare Tunnel + custom domain - out of scope)
- **n8n workflow automation** (forms + chatbot human fallback notifications - out of scope)
- **REST API syncing** (out of scope for single-user desktop app)
- **Dependabot** (automated dependency updates)
- **removed module-info** (jlink issue with SQLite JDBC automatic modules)
- **Testing tools removed** (Checkstyle, Mockito, Testcontainers, TestFX, JReleaser - out of scope)
- **CodeRabbit** (automated code review assistant - out of scope)

## NOTES FOR STEPHEN

**AI NOTES:**

Even with FXML, 90% of students fail because they build "Fat Controllers."

- The Sin: If your Controller.java has a Connection conn = DriverManager.getConnection(...) inside an @FXML method,
  you have failed as an Architect.
- The Architecture Way: Your Controller should be a "Thin Layer." It should only gather data from the UI and pass it
  to a Service or Repository class.
- The "Pro" Standard: In Big Tech (e.g., building trading terminals or desktop IDEs), we use Dependency Injection
  (DI) (like Google Guice or Spring) to inject these services into the Controller. Since you're just starting, manual
  "Constructor Injection" or a "Service Registry" is fine, but never let your UI logic touch your DB logic.

JavaFX is powerful, but it's a Stateful UI.
_ The Trap: Most beginners put their SQL logic or Business Logic inside the JavaFX Controller.
_ The Harsh Truth: If I see a ResultSet or an INSERT statement inside your .java file that handles a "Button Click," \* The Architecture Way: Use the MVC (Model-View-Controller) or MVVM pattern. Your Controller should only talk to a "Service Layer," which talks to a "Repository Layer" (SQLite). Decouple or Die.

Instead of controllers talking directly to the DAOs (e.g., StoreController calling CartDao.addOrIncrement()), they would introduce a Service Layer.

Why? The Controller should only know about JavaFX UI events (button clicks, text fields). The DAO should only know about SQL queries (INSERT, SELECT).
The Pro Move: You create a CartService. The controller says CartService.addItem(user, product). The Service handles the business logic (Does the user have enough money? Is the product in stock?) and then calls the DAO. This keeps your architecture pristine, heavily decoupled, and much easier for your groupmates to work on without stepping on each other's toes.

---

## PERSONAL STRUGGLES

- debugged jpackage not packaging with app-image, turns out the freaking thing wasnt pointing to the whole jdk, it was building runtimes without the main components to run the jvm "JVM not found error" or something, had to debug in like 4 hours even with ai assisted debugging session. (lesson learnt, have ai have the terminal if tough, for reading context off codebase but limit what it do like writing to the terminal only. only write to vscode where it can ask for permission for. and also i should provide a prompt checklist for debugging sessions that could be very helpful and speedup the process even with prompted context, specific, and clarifications question driven by AI.)

- always afraid to implement features and dependecies i dont understand and first time using, im am very hesitant it will introduce comlexity and waste only my time configuring.

- constantly paranoid of contrainst to use javafx fxml and using external dependencies because of vauge description of criteria of my professor.

- github flow to perfectly managed a team project with non technical groupmates, and also trying to do a overengineered project with a lot of moving parts, code reviews, and also manage the github flow process. it is a lot of work and responsibility on my shoulders, and it is hard to kinda balance everything and also try to learn new things along the way.
