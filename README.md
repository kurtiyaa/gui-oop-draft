# Java 25 LTS Desktop application with Database Finals Project Overdelivery Edition

## Project Overview

An academic team project developed on GitHub to showcase a polished E-Commerce Java 25 desktop application built with Maven, JavaFX, SQLite, and GitHub Actions for automated testing, verification, building, and release workflows.

## Features

- User Registration and Login with secure password hashing (BCrypt).
- Product Catalog with search and filtering.
- Shopping Cart with add/remove functionality.
- Image handling for products.
- Checkout Process with order summary and confirmation.
- Order History and Management.
- Responsive JavaFX UI with FXML and CSS styling.
- SQLite database with Flyway for migrations.

## Application Usage Example

The github releases page contains the latest release of the project. You can download zip file of the app-image of the latest release and run the executable file to run the project and can be run without needing to download java.

- Run the executable file in the downloaded zip file.
- The app will open with the login screen. You can register a new account or login with an existing account.
- After logging in, you will see the main screen with a list of products. You can add products to your cart, view your cart, and proceed to checkout.

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
- **Erin Cuenco** - Frontend Developer and Designer
- **Kurt Yaya** - Backend Developer and Backend Manager + Reviewer
- **Justine Castro** - Backend Developer
- **Rhian Ramirez** - Backend Developer

---

## Toolstack + Architecture Summary

- Layered architecture with clear separation of concerns (UI, Controller, Service, DAO, Model).
- Java 25 Full JDK Bellsoft Liberica - JavaFX for UI, JDBC for database access.
- Maven for build and dependency management.
- Maven + JavaFx plugin for running the app.
- SQLite JDBC + Flyway for database and migrations.
- BCrypt for password hashing.
- Github + GitHub Flow + GitHub Actions for version control and CI/CD.
- Github Actions - JUnit + AssertJ + Spotless + Spotbugs + Jacoco for CI pipeline.
- jpackage for packaging the app into an executable.
- Github Release with Zip compression release.

**refer to the [Architecture_Records](docs/Architecture_Records.md) for more detailed information about the architectural decisions made during the development of the project.**

## Application Flow

**Simple Application Flow - UI and Backend interaction flow diagram. This is a simplified version of the actual flow, but it gives you an idea of how the different components of the application interact with each other.**

![alt text](/.github/code_diagrams/Simple_Application_Flow.png)

## Roles

- **FRONTEND** - ./src/main/resources and also ./src/main/java/Controller responsible for JavaFX screens, layout composition, styling, fxml and css editing, and the overall user experience.
- **BACKEND** - ./src/main/java responsible for database access, business rules, validation, frontend and backend connection, and application state management.

Controllers act as the bridge between these two areas, translating user actions into backend operations and updating the UI with the results.

## Quick Start

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

  at "$env:JAVA_HOME" if you don't see at least "\BellSoft\LibericaJDK-25-Full" please restart your computer.

- **VSCode** for text editor + easy source control where you don't have to use git commands.
  - Run this command below with windows `powershell`
  ```ps
  winget install --id Microsoft.VisualStudioCode -e --source winget
  ```

If you use Command prompt, you could use `mvnw.cmd` instead of `./mvnw` or `.\mvnw` Windows Powershell.

Use these commands when developing locally:

```bash
# This all you need for development.
./mvnw javafx:run
./mvnw verify

# For a slow process but clean slate, run this commands below.
./mvnw clean javafx:run
./mvnw clean verify
```

**Automated tests run on every push on main via GitHub Actions. See Actions tab for results.**

**refer to the [Contributing Guide](docs/Contributing.md) for more detailed instructions on how to set up and contribute to the project.**

## Troubleshooting and Help

**GDrive Link:** https://drive.google.com/drive/folders/1a6pCo_QgS-lzT49429IeU90hzxB_QM2f

- Contains the latest backup of the project files, including vidoe demo, ERD Diagrams Pictures, Application Flow Diagrams, and any other relevant materials. This is a backup in case you have trouble running the project locally.

- Refer to all documents, I know it’s a lot, but it’s all there. If you can’t find it, ask in the group chat.

## Engineering Standards 101

1. Prompt AI to be your mentor. Do not let it generate code for you that you don't understand.
2. Build your intuition and knowledge. What, Why and How. (Use AI to effectively teach and explain to you)
3. Search for resources you could find, if having trouble. Prompt a Cheat sheet of what you need to know for a concise summary.
4. Follow best coding principles
   - DRY (Don’t Repeat Yourself): If you find yourself copying and pasting the same code in two or more places, stop and find a better way. (eg. Functions)
   - KISS (Keep It Simple, Stupid): The simplest solution is often the best. Avoid unnecessary complexity.
   - YAGNI (You Ain't Gonna Need It): Don’t add features until you actually need them. Focus on the core functionality first.
   - Security: Ensure you don't leave any cracks for the hacker to exploit.
   - Readability: Descriptive naming and simple structure make code easier for others to understand.
   - Maintainability: Well-structured code simplifies our future.

---

### License

> Feel free to use this code as a reference for your own projects, but please do not copy-paste it directly. Always review and adapt the code to fit your specific use case and requirements. This project is intended for educational purposes and to demonstrate architectural patterns and best practices in Java desktop application development.
