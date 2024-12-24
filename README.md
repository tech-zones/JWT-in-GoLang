
# JWT authentication with Golang

- This application uses JWT based authorization method to protect REST api endpoint

### Run app

- Run the application with the below commands and access the URLs

  ```bash
  go run main.go
  
  ```

- Access home route - http://localhost:4000 - No auth needed
  ```json
  {
    "status": "Success",
    "message": "Welcome to Golang with JWT authentication"
  }
  ```
- Access secure route - http://localhost:4000/secure - Expect auth error as we didn't pass JWT token

  ```json
  {
    "Status": "Failed",
    "Msg": "You are not authorized to view this page"
  }
  ```

- Generate JWT token - http://localhost:4000/login with payload with the below body

  ```json
  {
    "username": "admin",
    "password": "admin"
  }
  ```

  ```json
  {
    "status": "Success",
    "message": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX25hbWUiOiJBa2lsYW4iLCJMb2dnZWRJblRpbWUiOiIxMC0xMi0yMDIyIDIwOjU3OjMyIiwiaXNzIjoiQWtpbGFuIiwiZXhwIjoxNjcwNjg2MTEyfQ.E--k9nMc-uOHb6VWJCrTyzSgGQ6JGAT_m3J1z_z-Ohs"
  }
  ```

- Copy the JWT token from the above response and pass it in request header as Token value - http://localhost:4000/secure

  ```json
  {
    "status": "Success",
    "message": "Congrats and Welcome to the Secure page!. You gave me the correct JWT token!"
  }
  ```
