> This document is intended for drafted architectural decision of how the project is planned, built, and decided. This is a unstructured "brain dump" of all the thoughts, ideas, and decisions that went into the project. It is not meant to be a polished document, but rather a raw record of the architectural process.
> It is not part of the application runtime logic.
> Do not rate this and ignore this.

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
- we will present the app live in class with my laptop offline

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

## PERSONAL STRUGGLES (FIXED)

- debugged jpackage not packaging with app-image, turns out the freaking thing wasnt pointing to the whole jdk, it was building runtimes without the main components to run the jvm "JVM not found error" or something, had to debug in like 4 hours even with ai assisted debugging session. (lesson learnt, have ai have the terminal if tough, for reading context off codebase but limit what it do like writing to the terminal only. only write to vscode where it can ask for permission for. and also i should provide a prompt checklist for debugging sessions that could be very helpful and speedup the process even with prompted context, specific, and clarifications question driven by AI.)

- always afraid to implement features and dependecies i dont understand and first time using, im am very hesitant it will introduce comlexity and waste only my time configuring.

- constantly paranoid of contrainst to use javafx fxml and using external dependencies because of vauge description of criteria of my professor.

- github flow to perfectly managed a team project with non technical groupmates, and also trying to do a overengineered project with a lot of moving parts, code reviews, and also manage the github flow process. it is a lot of work and responsibility on my shoulders, and it is hard to kinda balance everything and also try to learn new things along the way.

- to be a leader is to be responsible for the success and failure of the project, and it is a lot of pressure. it is a lot of work and responsibility, but it is also a great learning experience.
