# 2.2.1 Cycle 1: Database

## Design

In this first cycle, I want to set up the database I will be using to be able to store the data about the people who play my game. I will need to have a database that can store the usernames and passwords of the accounts of my players, and should be able to add new accounts to it. The usernames should always be unique to others in the database, and both the username and password need to have an input.&#x20;

### Objectives

* [x] Create the database
* [x] Create username and password fields
* [x] Be able to make changes to the database
* [x] Have it ready to be implemented for use in my game

### Usability Features

The player needs to be able to create an account [effectively](systems-diagram.md#effective) and [efficiently](systems-diagram.md#efficiency), and be able to know and then meet the requirements. The player should know firstly that they have to make an account, and then that if their entry doesn't meet the requirements, why this is.

### Key Variables

| Variable Name | Use                                           |
| ------------- | --------------------------------------------- |
| users         | Stores both the name and password being input |
| name          | The desired username                          |
| password      | The desired password                          |

### Pseudocode

```
create database = Database

function Register (user) 
select all from users where user = (username), (password)
if error
  display error
else if name already used
  display name already taken
else 
  add to Database

create Table if it doesnt exist named users
id = incrementing integer
name not null, unique
password not null
if error
  display error
if already exists
  table already exists
  
const user = (name) (password)
Register user
if error
  "Registration failed"
else 
  "Registration succeeded"
  
Select all from users 
if error
  display error
for each row
  get row id and row name
  
close database
if error
  display error
else 
  "Database connection closed"

```

## Development

### Outcome

At the end of this first cycle, I have a database that I can use to create accounts for my game, and allow users to have their own username and password. The database also ensures usernames are unique, and allows me to query the data, finding the rows it is on and also safely close the connection. &#x20;

```javascript
const sqlite3 = require("sqlite3").verbose();

const db = new sqlite3.Database("Database.db");    //Creating a database named Database

function Register(user, callback) {
  db.get(`SELECT * FROM users WHERE name = "${user.name}"`, (err, row) => {
    if (err) {
      callback("sqlerr");
      return;
    } else if (row) {
      callback("User already exists");
      return;
    }
    db.run(
      `INSERT INTO users (name, password) VALUES ("${user.name}", "${user.password}")`,
      function (err) {
        if (err) {
          callback("sqlerr");
          return;
        }
        callback(false);
      }
    );
  });
}

db.serialize(() => {
  db.run(
    `CREATE TABLE IF NOT EXISTS users (
        id INTEGER PRIMARY KEY AUTOINCREMENT,
        name TEXT NOT NULL UNIQUE,
        password TEXT NOT NULL
    )`,
    (err) => {                                               // Creating the database
      if (err) {
        console.error(err.message);
      } else {
        console.log(`Table created or already exists.`);
        
          
          const user = { name: `Max`, password: `password` };     // Inputting values
        Register(user, function (err, registrationStatus) {
          if (err) {
            console.log("Registration failed:", err);
          } else {
              console.log("Registration succeeded");
            } 
          }
        );

        db.all(`SELECT * FROM users`, [], (err, rows) => {          // To query the data
          if (err) {
            console.error(err.message);
          } else {
            rows.forEach((row) => {
              console.log(row.id, row.name);
            });
          }
        });

        db.close((err) => {                   // Closing the database
          if (err) {
            console.error(err.message);
          } else {
            console.log(`Database connection closed.`);
          }
        });
      }
    }
  );
});
```

### Challenges

A challenge was definitely trying to get used to sql as a language and the syntax involved. This presented me with the challenge of trying to know what language to use when trying to have the code do as I want. Although generally this wasn't too much of an issue, it did make debugging and trying to find errors in my code a lot harder.

### Tests

<table><thead><tr><th width="119">Test</th><th>Instructions</th><th>What I expect</th><th>What actually happens</th><th>Pass/Fail</th></tr></thead><tbody><tr><td>1</td><td>Run creating table</td><td>Table named users created  </td><td>As expected</td><td>Pass</td></tr><tr><td>2</td><td>Run with adding a user included</td><td>Create table and add user with message of success or failure</td><td>Error displayed as it failed to input username and password</td><td>Fail</td></tr><tr><td>3</td><td>Run and be able to select information about data that has been input</td><td>To be able to select data from users</td><td>As expected</td><td>Pass</td></tr><tr><td>4</td><td>Run and then being able to close the database when finished with it</td><td>A message after displaying that the database connection is closed</td><td>As expected</td><td>Pass</td></tr><tr><td>5</td><td>Run and be able to input multiple new values for users through a new function</td><td>To be able to input a value for username and password, it be checked if there is an input and if username is unique and then it be in the database</td><td>Error displayed due to syntax error</td><td>Fail</td></tr></tbody></table>

### Evidence

[https://youtu.be/ugBxMsOEy5o](https://youtu.be/ugBxMsOEy5o)
