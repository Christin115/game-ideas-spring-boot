# Game Ideas

A Spring Boot web app where users sign up, post ideas for video games, and browse the ideas other people have shared. Built as my solo project for Coding Dojo's Java stack.

## Features

- **Accounts:** register and log in; passwords are hashed with BCrypt and never stored in plain text
- **Validation:** required fields, length limits, valid email, unique email, and matching password confirmation, with errors shown on the form
- **Game ideas (CRUD):** create, view, edit, and delete game ideas, each with a name, genre, and description
- **Ownership:** every game idea is linked to the user who created it (one-to-many relationship)
- **Protected pages:** every page except login and registration requires a signed-in user

## Tech stack

| Layer | Technology |
|-------|------------|
| Language | Java 17 |
| Framework | Spring Boot 3 (Spring MVC) |
| Data | Spring Data JPA / Hibernate, MySQL |
| Views | JSP with JSTL, Bootstrap |
| Security | jBCrypt password hashing, session-based login |
| Build | Maven |

## How it's organized

```
Games/src/main/java/com/codingdojo/game/
├── controllers/    LoginController (register, login, logout, dashboard)
│                   HomeController (create, view, edit, delete game ideas)
├── services/       UserService (registration and login rules), GameService
├── repositories/   Spring Data JPA repositories for users and games
└── models/         User, Game, LoginUser
Games/src/main/webapp/WEB-INF/   JSP pages
```

Requests go from a **controller** to a **service**, which holds the business rules, and from there to a **repository**, which talks to the database.

## Run it locally

**Prerequisites:** Java 17 and a running MySQL server.

1. Set your MySQL credentials as environment variables (the app creates a database named `project` on first run):

   ```bash
   # macOS / Linux
   export DB_USERNAME=root
   export DB_PASSWORD=your_mysql_password
   ```
   ```powershell
   # Windows PowerShell
   $env:DB_USERNAME = "root"
   $env:DB_PASSWORD = "your_mysql_password"
   ```

2. Start the app:

   ```bash
   cd Games
   ./mvnw spring-boot:run      # Windows: mvnw.cmd spring-boot:run
   ```

3. Open http://localhost:8080, create an account, and add a game idea.
