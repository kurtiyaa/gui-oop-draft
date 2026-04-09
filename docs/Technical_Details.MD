# Technical Details

> This document is intended for technical understanding of how the project is built, validated, reviewed, and released.  
> It is not part of the application runtime logic.

---

## Overview

This project relies on a focused DevOps toolchain to keep development, validation, review, and release consistent.

## Application Flow

1. UI: JavaFX screens and user interactions
2. Controller: Translates UI events into backend operations and updates the UI with results.
3. Service: Contains business logic and rules, orchestrating operations between the UI and data access
4. DAO: Handles database interactions, isolating persistence logic from business logic.
5. Database: SQLite for local data storage, accessed via JDBC.

UI -> Controller -> Interface -> Service -> Interface -> DAO -> DB.

## Why's of Achitectural decision + Software Design Pattern

- **Modular Monolith:** Keeps deployment simple as one application while still separating features into clear modules, so the codebase stays maintainable and can evolve toward microservices later if needed.
- **Monorepo:** Stores all project parts in one repository, making dependency/version alignment, cross-module refactors, and shared standards easier for the whole team.
- **MVC + Service:** Separates UI concerns (View/Controller) from business logic (Service), improving testability, readability, and long-term maintainability.
- **Dependency Injection:** Manages object creation and dependencies, promoting loose coupling and easier testing.
- **Dao:** Isolates database access from business logic, so persistence changes are localized and data operations are easier to test and review.
- **Strategies:** Encapsulates interchangeable algorithms/behaviors behind a common interface, making feature variation cleaner and reducing conditional-heavy code.

## Why's of Tools and Frameworks used

- **Java 25 LTS (Liberica Full)** - A full JDK distribution for complete development, not a stripped-down runtime. Java 25 LTS is modern and stable for long-term development.
- **JavaFX** - Modern and popular desktop UI framework with many available learning resources.
- **Maven** - Chosen for simplicity and predictability. It ensures every developer uses the exact same dependencies. **Con:** FXML usage can feel complex for some team members.
- **SQLite + JDBC** - Best for a local, simplified, and portable database setup. JDBC is used because Java needs a compatible driver to interact with SQLite. **Con:** less feature-rich than PostgreSQL.
- **GitHub** - Strong platform for team collaboration, version control, and sharing the codebase.
- **GitHub Flow** - **Pros:** clean, maintainable, and reliable workflow; enforces code reviews and protects `main` from bad commits. **Con:** may be too technical for non-technical teammates.
- **GitHub Actions** - Integrated with GitHub, easy to set up, and useful for automated testing and CI.
- **CodeRabbit** - It acts like an automated tutor. It checks our code for obvious mistakes before we waste time reviewing it manually, which speeds up our workflow.
- **Flyway** - Automates database `schema migrations`. Flyway syncs the database version across everyone’s computer.
- **JUnit 6** - Easy-to-use framework for `automated integration testing`.
- **AssertJ** - Makes `JUnit assertions` more readable, maintainable, and easier to debug.
- **BCrypt** - Used for secure password hashing. BCrypt is intentionally slow and includes built-in salting, which makes brute-force and rainbow-table attacks much harder than plain hashing methods.
- **SpotBugs** - `Static analysis tool` used to detect likely bugs and risky code patterns early, before runtime failures.
- **Spotless** - Enforces `consistent code formatting` automatically, reducing style-related review noise and keeping the codebase clean.
- **Jacoco** - `Code coverage` measurement tool that tracks which parts of the codebase are tested, helping identify untested code and improve test quality.

---
