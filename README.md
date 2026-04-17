# Java 25 LTS Desktop application with Database Finals Project Overdelivery Edition

An academic team project developed on GitHub to showcase a polished Java 25 desktop application built with Maven, JavaFX, SQLite, and GitHub Actions for automated testing, verification, building, and release workflows.

## Background

- **College**: Developed at Pampanga State University at our `1st Year`, `Computer Engineering` course at a `OOP Class`.
- **Project Description**: This project is a final Project for an Object-Oriented Programming class, where the goal is to create a Java desktop application with a database. The project is designed to be overdelivered and overengineered to impress the professor and demonstrate a strong understanding of software architecture, design patterns, and best practices.

## Constraints and Assumptions

- OOP class project; non-cheating frameworks only (no Electron).
- Windows-based team with non-technical groupmates.
- Single-user application.
- Live presentation on offline laptop.

### Collaborators

- **Stephen Macabulos** - Group Leader, Platform Engineer, Lead Architect, and Reviewer
- **Erin Cuence** - Frontend Developer and Designer
- **Kurt Yaya** - Backend Developer and Backend Manager + Reviewer
- **Justine Castro** - Backend Developer
- **Rhian Ramirez** - Backend Developer

---

## Toolstack

- Java 25 Full JDK Bellsoft Liberica
- Maven + JavaFx
- SQLite JDBC + Flyway
- Github + GitHub Flow + GitHub Actions
- Github Actions - JUnit + AssertJ + Spotless + Spotbugs + Jacoco
- Github Release with Zip compression release.

## Roles

- **FRONTEND** - ./src/main/resources and also ./src/main/java/Controller responsible for JavaFX screens, layout composition, styling, fxml and css editing, and the overall user experience.
- **BACKEND** - ./src/main/java responsible for database access, business rules, validation, frontend and backend connection, and application state management.

Controllers act as the bridge between these two areas, translating user actions into backend operations and updating the UI with the results.

## Prerequisites

- **Git** For version control (if you don't have this, run this commands below.)
  - Run this command below with windows `powershell`

  ```ps
  winget install --id Git.Git -e --source winget
  ```

- **Java 25 LTS JDK** For the Java itself
  - Run this command below with windows `powershell`

  ```ps
  winget install --id BellSoft.LibericaJDK.25.Full -e --source winget

  $env:JAVA_HOME
  ```

  at "$env:JAVA_HOME" if you don't see atleast "\BellSoft\LibericaJDK-25-Full" please restart your computer.

- **VSCode** for text editor + easy source control where you don't have to use git commands.
  - Run this command below with windows `powershell`
  ```ps
  winget install --id Microsoft.VisualStudioCode -e --source winget
  ```

## Maven Wrapper via CLI (Powershell/Linux)

Use these commands when developing locally:

If you use Command prompt, you could use `mvnw.cmd` instead of `./mvnw` or `.\mvnw` Windows Powershell.

```bash
# This all you need for development.
./mvnw javafx:run
./mvnw verify

# For a slow process but clean slate, run this commands below.
./mvnw clean javafx:run
./mvnw clean verify
```

---

## Engineering Standards 101

1. Prompt AI to be your mentor. Do not let it generate code for you that you don't understand.
2. Build your intuition and knowledge. What, Why and How. (Use AI to effectively teach and explain to you)
3. Search for resources you could find, if having trouble. Prompt a Cheat sheet of what you need to know for a concise summary.
4. Follow best coding principles
   - DRY (Don’t Repeat Yourself): If you find yourself copying and pasting the same code in two or more places, stop and find a better way. (eg. Functions)
   - Security: Ensure you don't leave any cracks for the hacker to exploit.
   - Readability: Descriptive naming and simple structure make code easier for others to understand.
   - Maintainability: Well-structured code simplifies our future.

---
