# Technical Details

> This document is intended for technical understanding of how the project is built, validated, reviewed, and released.  
> It is not part of the application runtime logic.

---

## Constraints and Assumptions

- This is a grouped project in a OOP class, cheating frameworks (Electron) might be not allowed.
- Groupmates are likely using Windows.
- Group mates are non-technical.
- The app itself is only expecting 1 user.
- Peers are expected to code and leader is to be managing the architectural system integrity and alternate peer code reviews.
- We will present the app live in class with my laptop offline.

## The Why's of Architecture Decision + Software Design Pattern

- **Monorepo:** Stores all project parts in one repository, making dependency/version alignment, cross-module refactors, and shared standards easier for the whole team.
- **Layered Monolith:** Keeps deployment simple as one application while still separating features into clear layers, so the codebase stays maintainable.
- **MVC + Service + Dao:** Seperates concerns clearly. The UI (View) is only responsible for displaying data and gathering user input. The Controller is a thin layer that translates UI events into backend operations. The Service contains the business logic and rules, orchestrating operations between the UI and data access. The DAO handles database interactions, isolating persistence logic from business logic. This structure promotes maintainability, testability, and scalability.

## Why's of Tools and Frameworks used

- **Java 25 LTS (Liberica Full)** - A full JDK distribution for complete development, not a stripped-down runtime. Java 25 LTS is modern and stable for long-term development.
- **JavaFX** - Modern and popular desktop UI framework with many available learning resources.
- **Maven** - Chosen for simplicity and predictability. It ensures every developer uses the exact same dependencies.
- **SQLite + JDBC** - Best for a local, simplified + embedded, and portable database setup. JDBC is used because Java needs a compatible driver to interact with SQLite. **Con:** less feature-rich than PostgreSQL. Not ideal for multi-user or complex relational data, but sufficient for this project’s scope.
- **GitHub** - Strong platform for team collaboration, version control, and sharing the codebase.
- **GitHub Flow** - **Pros:** clean, maintainable, and reliable workflow; enforces code reviews and protects `main` from bad commits. **Con:** may be too technical for non-technical teammates.
- **GitHub Actions** - Integrated with GitHub, easy to set up, and useful for automated testing and CI.
- **Flyway** - Automates database `schema migrations`. Flyway syncs the database version across everyone’s computer.
- **BCrypt** - Used for secure password hashing. BCrypt is intentionally slow and includes built-in salting, which makes brute-force and rainbow-table attacks much harder than plain hashing methods.
- **JUnit 6** - Easy-to-use framework for `automated integration testing`.
- **AssertJ** - Makes `JUnit assertions` more readable, maintainable, and easier to debug.
- **SpotBugs** - `Static analysis tool` used to detect likely bugs, unused and risky imports, and risky code patterns early, before runtime failures.
- **Spotless** - Enforces `consistent code formatting` automatically, reducing style-related review noise and keeping the codebase clean.
- **Jacoco** - `Code coverage` measurement tool that tracks which parts of the codebase are tested, helping identify untested code and improve test quality.

---
