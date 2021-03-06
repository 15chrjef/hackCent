# User Auth

## Frontend

### Components / Containers
- [x] Auth Errors
  - [x] Map errors from LoginContainer + SignupContainer to Auth
  - [x] Pass these errors as props to the Auth Form
  - [x] Render any errors above the email/password inputs
- [x] Dispatch thunk action for user creation on form submission

### Actions
- [x] User Creation
  - [x] RECEIVE_USER constant
  - [x] RECEIVE_CURRENT_USER constant
  - [x] RECEIVE_USERS constant
  - [x] AUTH_ERRORS constant
  - [x] receiveAuthErrors (dispatches AUTH_ERRORS, errors)
  - [x] receiveUser (dispatches RECEIVE_USER, user)
  - [x] receiveCurrentUser (dispatches RECEIVE_CURRENT_USER, user)
  - [x] receiveUsers (dispatches RECEIVE_USERS, users)
  - [x] createUser ((axios POST `users/`).then(receiveUser))
    - [x] catch errors and dispatch AUTH_ERRORS
- [x] User Login
  - [x] loginUser ((axios POST `session/`).then(receiveUser))
    - [x] catch errors and dispatch AUTH_ERRORS

### Reducers
  - [x] usersReducer
    - [x] Manage RECEIVE_USER
    - [x] Manage RECEIVE_USERS
  - [x] sessionReducer
    - [x] holds currentUser data
  - [x] errorsReducer
    - [x] Manage AUTH_ERRORS
  - [x] entitiesReducer
    - [x] users: usersReducer
  - [x] rootReducer
    - [x] entities: entitiesReducer
    - [x] errors: errorsReducer
    - [x] session: sessionReducer

### Routes
  - [x] AuthRoute
    - Route that redirects an authenticated user
    - Ex: This will be used in the router as a route for `/login` to redirect an authenticated user to the `/tutors` or `/students` page
  - [x] ProtectedRoute
    - Route that redirects an unauthenticated user
    - Ex: This will be used to prevent redirect unauthenticated users from any page besides `/tutors` or `/students`

## Backend

### Models
  - [x] User
    - [x] email, `not null`
    - [x] password_digest, `not null`
    - [x] public_key, `not null` (will be created before user persist)
    - [x] private_key `not null` (will be created before user persist)
### Routes
  - [x] Users
    - [x] `POST /users` (user creation, returns user)
    - [x] `GET users` (returns all users)
    - [x] `GET users/${id}` (returns user with `id`)
  - [x] Session
    - [x] Login
      - [x] `POST /session` (user login, returns user)
      - [x] Establish user's session_token as a safe base64 string
      - [x] Store this sessionToken in the application's session
    - [x] Logout
      - [x] Clear session's sessionToken

### Seeds
  - [x] Create 5 user seeds like: {email: 'example@email.com', password: '123456'}
    - The user creation process must assign values to these columns:
      - password_digest
      - public_key
      - private_key
