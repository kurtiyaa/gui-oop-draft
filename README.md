# Java 25 LTS Desktop application with Database Finals Project Overdelivery Edition

An academic team project developed on GitHub to showcase a polished Java 25 desktop application built with Maven, JavaFX, SQLite, and GitHub Actions for automated testing, verification, building, and release workflows.

- **Tools:**
  - Java 25 Full JDK Bellsoft Liberica
  - Maven + JavaFx
  - SQLite JDBC + Flyway
  - Github + GitHub Flow + GitHub Actions
  - Github Actions - JUnit + AssertJ + Spotless + Spotbugs + Jacoco
  - Github Release with Zip compression release.

---

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

## GitHub Flow with PR and Branching in VS Code

- **Technical Terms:**
  - Commit - commit your changes / saves your latest staged changes
  - Pull - fetches and integrates the latest changes from the remote repository into your current local branch.
  - Push - uploads your local commits from the current branch to the remote repository.
  - Branch - a working copy for this task. Why? that's how team manage and keep the `"main"` branch (where everybody based from) to be clean,nobody harms production, and ensure everyone is on the same page.
  - PR - means pull request, where you pull from created branch to the main branch to `merge` the branch, making the code be part of the `main` branch. Why? because we can't just merge to main with any branch, we need to review it first before merging to main.

1. Start from a clean `main` branch.
   - In VS Code, open the **Source Control** view.
   - Make sure there are no unfinished local changes before you begin.
   - The "Pull Before You Push" Mantra:
     1. Check group chat for claiming then claim yourself making sure no conflicts on agreed upon changes
     2. Git checkout main -> git pull
     3. Git checkout feature/my-task -> git rebase main
     4. Solve the conflicts locally. (If you see 'REBASING' in your branch name and get stuck, run: git rebase --abort to return to safety.)

2. Create a short-lived branch for the task.
   - In the lower-left corner of VS Code, click the current branch name.
   - Choose **Create new branch**.
   - Use a focused branch name such as `feature/login-validation` or `fix/cart-total`.

3. Work only on the files needed for the change.
   - Keep the effort centered on `src/main` so the change stays in the application code.
   - Use the editor and the Source Control panel together so you can see exactly what changed.
   - Review the diff often to catch accidental edits early.

4. Stage only the intended files.
   - Use the `+` icon next to a file to stage it.
   - If only part of a file should be included, stage carefully and keep the commit limited to the relevant work.

5. Write a clear commit message and commit from VS Code.
   - Enter a message that describes the change, such as `fix: login button validation`.
     1. `feat` - Feature - Adds new functionality to the application.
     2. `fix` - Bug Fix - Patches a bug in the codebase.
     3. `refactor` - Refactor - Changes code structure without fixing bugs or adding features.
     4. `chore` - Maintenance - Updates build scripts, dependencies, or non-functional tasks.
     5. `docs` - Documentation - Changes to documentation files (like README) or code comments.

6. Push the branch and Validate CI/CD GitHub.
   - Use **Publish Branch** or **Sync Changes** in VS Code to send the branch to the remote repository.
   - If you see red/x mark (CI/CD) beside your commit changes, please address the issue using the logs inside and identify the problem.

7. Open a pull request.
   - Create the PR from GitHub or from the VS Code GitHub workflow if available.
   - Use a title that matches the branch purpose, and describe what changed.

8. Merge after review and successful validation.
   - Merge only after the PR is approved and the build is green.
   - Delete the branch after merge to keep the repository clean.

9. Return to `main` and repeat for the next task.
   - Switch back to `main` in VS Code with `git checkout main`.
   - Pull the latest changes before starting the next branch with `git pull`.
   - Run `git fetch --prune` to clean up any deleted branches from the remote repository.
   - Delete the local branch after merge to keep your workspace clean: `git branch -d feature/my-task`.
   - Repeat the same flow for each new feature or fix.

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
