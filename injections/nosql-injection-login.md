NoSQL Injection at Login Endpoint

Injection Type:
NoSQL

Affected Endpoint
POST rest/user/login

What the application was supposed to do
The login endpoint must clean and validate the user inputs in the field email and password, without affecting any part of the backend working and database.

What went wrong
The backend failed to validate user input and directly allowed it to manipulate as mongo-db query, MongoDB operators supplied by user were considered as queries to be executed in the database.

Steps to Reproduce
1.Login as a user with test credentials (POST)
2.Modify the input and add mongodb operator,
  {
    "email":{$ne":null},
    "password":{"$ne":null}
  }

  or try for either one of the fields to identify which one of it allows direct changes to DB.
3.500 Internal server error can be observed from the server.

Evidence
The server returned a stack trace denoting that the object passed by the user is treated as a string during authentication process.
