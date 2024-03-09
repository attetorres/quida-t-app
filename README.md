# QUIDA-T

## DESCRIPTION
Task lists management app for therapists, patients, and general users, enabling the sharing of task lists and tracking their completion on a daily, weekly, or monthly basis.

## TEAM
- Atteneri Torres González: https://github.com/attetorres
- Aitor Díaz Santana: https://github.com/ocsilisab
- Fran Arteaga: https://github.com/franArteaga8

## TECH
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![Node.js](https://img.shields.io/badge/Node.js-339933?logo=node.js&logoColor=white)](https://nodejs.org/)
[![Express](https://img.shields.io/badge/Express-000000?logo=express&logoColor=white)](https://expressjs.com/)
[![Sequelize](https://img.shields.io/badge/Sequelize-52B0E7?logo=sequelize&logoColor=white)](https://sequelize.org/)
[![MySQL](https://img.shields.io/badge/MySQL-4479A1?logo=mysql&logoColor=white)](https://www.mysql.com/)

## INSTALLATION
- Run `$ npm i` on console

- Config a `.env` file as explained on `.env.example`

## DATABASE

### DATA STRUCTURE & MODELS
![image](/db_diagram.png)

### DB_TABLES


## API ROUTES (/api)


<details>
<summary> AUTH ENDPOINTS (/auth)</summary>

|Method |Endpoint |Token|Role |Description      |Params  |Returns  |
|-------|---------|-----|-----|-----------------|--------|---------|
| POST  | /signup | NO  | -   | Creates an user | -      | {token} |
| POST  | /login  | NO  | -   | Logs in         | -      | {token} |
</details>


<details>
<summary> USER ENDPOINTS (/users)</summary>

|Method  |Endpoint        |Token|Role          |Description                     |Params  |Returns                                 |
|--------|----------------|-----|--------------|--------------------------------|--------|----------------------------------------|
| GET    | /              | YES | Psychologist | Get all Users                  | -      | [{users}]                              |
| GET    | /profile       | YES | -            | Get self profile               | -      | {user}                                 |
| GET    | /psychologist  | YES | -            | Get assigned Psychologist      | -      | {psychologist}                         |
| GET    | /:userId       | YES | -            | Get one user                   | userId | {user}                                 |
| PUT    | /              | YES | -            | Update user                    | -      | {user}                                 |
| PUT    | /:userId       | YES | Psychologist | Assign psychologist to an user | userId | {user}                                 |
| PUT    | /admin/:userId | YES | Admin        | Validate psychologist role     | userId | "Updated successfully", {psychologist} |
| PUT    | /close/:listId | YES | -            | Close task list registry       | listId | [{tasks}]                              |
| DELETE | /              | YES | -            | Delete user                    | -      | "User deleted"                         |
</details>


<details>
<summary> LIST ENDPOINTS (/lists)</summary>

|Method  |Endpoint          |Token|Role            |Description    |Params          |Returns                                                 |
|--------|------------------|-----|----------------|---------------|----------------|--------------------------------------------------------|
| POST   | /                | YES |  -             | Create a List | -              | message, {list}                                        |
| POST   | /:listId/:userId | YES |  Psychologist  | Assign a List | listId, userId | {assignedUser}                                         |
| GET    | /                | YES |  -             | Get all Lists | -              | [{lists}]                                              |
| GET    | /myLists         | YES |  -             | Get my Lists  | listId         | {"createdLists": [{lists}], "assignedLists": [{lists}] |
| GET    | /:listId         | YES |  -             | Get a List    | listId         | {list}                                                 |
| PUT    | /:listId         | YES |  -             | Update a List | listId         | "List updated successfully"                            |
| DELETE | /:listId         | YES |  -             | Delete a List | listId         | "List deleted"                                         |
</details>


<details>
<summary> TASK ENDPOINTS (/tasks)</summary>

|Method  |Endpoint          |Token|Role |Description                |Params         |Returns                      |
|--------|------------------|-----|-----|---------------------------|---------------|-----------------------------|
| POST   | /:listId         | YES | -   | Create a task             | listId        | [{users}]                   |
| GET    | /                | YES | -   | Get all my tasks          | -             | [{list: {tasks}}]           |
| GET    | /:listId/:taskId | YES | -   | Get a task                | listId,taskId | {task}                      |
| GET    | /:listId         | YES | -   | Get all tasks from a list | listId        | [{tasks}]                   |
| PUT    | /:listId/:taskId | YES | -   | Update a task             | listId,taskId | "Task updated successfully" |
| DELETE | /:listId/:taskId | YES | -   | Delete a task             | listId,taskId | "Task deleted successfully" |
</details>
