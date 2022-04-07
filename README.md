# golang-jwt-project
Simple go server that performs user authentication using JWT, gin-gonic :cocktail:, and MongoDB :leaves:. Monolithic app :moyai:. Serves as the backend for signup/login functionality.

## Prerequisites
1. Go installed
2. MongoDB installed

## Build and run
1. Start the server with the following commands:

    ```
    cd <cloned_repo>
    go run main.go
    ```
    
2. In a service like Postman, create 4 new requests
    | Request Name | Method | URL |
    | --- | --- | --- |
    | AUTH SIGNUP | POST | http://localhost:9000/users/signup |
    | AUTH LOGIN | POST | http://localhost:9000/users/login |
    | AUTH USERS | GET | http://localhost:9000/users |
    | AUTH USER BY ID | GET | http://localhost:9000/users/{id} |
    
3. Experiment with running the various requests to signup and login. The user account entries will now persist between restarts of the go server. Note that this API does not implement a DELETE request handler even for ADMIN users.
    
    AUTH SIGNUP requests require a json body of the format:
    ```
    {
      "First_name": "John",
      "Last_name": "Doe",
      "Password": "password",
      "Email": "johndoe@fake.com",
      "Phone": "7205555555",
      "User_type": "USER"
    }
    ```
    where the User_type value can be either "USER" or "ADMIN"  
    
    
    AUTH LOGIN requests require a json body with Email and Password fields of a registered user. The json response to a successful AUTH LOGIN request will contain a token value.  
    
    
    The AUTH USERS request requires an added header "token" where the value should be the token of a logged in user. AUTH USERS will return all users in the database only if the requesting user is of type "ADMIN"  
    
    
    The AUTH USER BY ID request also requires an added header "token". AUTH USER BY ID should run for any valid user.
    
