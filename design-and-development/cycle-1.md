# 2.2.1 Cycle 1

## Design

In this first cycle, I want to set up the database I will be using to be able to store the data about the people who play my game. I will need to have a database that can store the usernames and passwords of the accounts of my players, and should be able to add new accounts to it. The usernames should always be unique to others in the database, and both the username and password need to have an input.&#x20;

### Objectives

* [x] Create the database
* [x] Create username and password fields
* [ ] Be able to make changes to the database
* [ ] Have it ready to be implemented for use in my game

### Usability Features

The player needs to be able to create an account [effectively](systems-diagram.md#effective) and [efficiently](systems-diagram.md#efficiency), and be able to know and then meet the requirements. The player should know firstly that they have to make an account, and then that if there entry doesn't meet the requirements, why this is.

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

At the end of this first cycle, I have a database that I can use to create accounts for my game, and allow users to have their own username and password. The database also ensures usernames are unique, and allows me to query the data, finding the rows it is on and also safely close the connection.

### Challenges

A challenge was definitely trying to get used to sql as a language and the syntax involved. This presented me with the challenge of trying to know what language to use when trying to have the code do as I want. Although generally this wasn't too much of an issue, it did make debugging and trying to find errors in my code a lot harder.

### Tests

| Test | Instructions                                                                  | What I expect                                                                                                                                      | What actually happens                                       | Pass/Fail |
| ---- | ----------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------- | --------- |
| 1    | Run creating table                                                            | Table named users created                                                                                                                          | As expected                                                 | Pass      |
| 2    | Run with adding a user included                                               | Create table and add user with message of success or failure                                                                                       | Error displayed as it failed to input username and password | Fail      |
| 3    | Run and be able to select information about data that has been input          | To be able to select data from users                                                                                                               | As expected                                                 | Pass      |
| 4    | Run and then being able to close the database when finished with it           | A message after displaying that the database connection is closed                                                                                  | As expected                                                 | Pass      |
| 5    | Run and be able to input multiple new values for users through a new function | To be able to input a value for username and password, it be checked if there is an input and if username is unique and then it be in the database | Error displayed due to syntax error                         | Fail      |

### Evidence
