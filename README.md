# Java 25 LTS Desktop application with Database Finals Project

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

## Demo Application Usage Example (Not Development Environment)

- Download the latest release from the GitHub releases section (sidebar).
- Run the executable file in the downloaded zip file.
- The app will open with the login screen. You can register a new account or login with an existing account.

### Collaborators

- **Stephen Macabulos** - Group Leader, Platform Engineer, Lead Architect, and Reviewer
- **Erin Cuenco** - Frontend Developer and Designer
- **Kurt Yaya** - Backend Developer and Backend Manager + Reviewer
- **Justine Castro** - Backend Developer
- **Rhian Ramirez** - Backend Developer

---

## Application Flow

**Simple Application Flow - Simplified UI and Backend interaction flow diagram using only 6 shape processes.**

![alt text](/.github/code_diagrams/Simple_Application_Flow.png)

## Quick Start (What to do next)

### Prerequisites

- Run these command below with windows `powershell`

* **Git** For version control (if you don't have this, run this commands below.)

  ```ps
  winget install --id Git.Git -e --source winget
  ```

* **Java 25 LTS JDK** For the Java itself

  ```ps
  winget install --id BellSoft.LibericaJDK.25.Full -e --source winget

  $env:JAVA_HOME
  ```

  at "$env:JAVA_HOME" if you don't see at least "\BellSoft\LibericaJDK-25-Full" please restart your computer.

* **VSCode** for text editor + easy source control where you don't have to use git commands.
  - Clone the repository by running this command in your terminal:

  ```bash
  git clone https://github.com/notseekeru/gui-oop-draft.git
  cd gui-oop-draft
  code .
  ```

**For more detailed instructions on how to set up and run the project locally and troubleshooting, please refer to the [Contributing Guide](docs/Contributing.md).**

---

### License

> No License - Feel free to use this code as a reference for your own projects.
