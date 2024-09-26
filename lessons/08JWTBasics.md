
### Concepts: Authentication with JWT Tokens

This lesson is a crunch, but stay focused, stay alert. A holiday break is on the way and a chance to catch up once this loaded lesson is complete. You got this!

## Summary:

 - Store passwords securely using hashes.
 - Use JWTs for authentication, but prefer HTTP-only cookies for better security.
 - Protect routes with middleware and handle errors with clear, structured responses.
 - Authentication with JWT Tokens
 - Security Testing

## Refresh
Client-server architecture involves:

**Client:** Requests and displays data through a web browser or app. (For User, User facing)</br>
**Server:** Hosts the application, processes requests, and returns data.

They communicate over the internet using HTTP/HTTPS, enabling dynamic web interactions.

## Overview: 

To secure web applications, especially those that handle user data, authentication is necessary. When users register, their passwords are stored securely as cryptographic hashes rather than in plain text. This ensures that even if the database is compromised, passwords remain protected. This also largely prevents those with internal access to systems (developers/engineers), access to users passwords. The users password information is safe/secure.

JWT Tokens: Upon login, users receive a JSON Web Token (JWT). This token, signed by the server, identifies the user and is included in subsequent requests. JWTs should not contain sensitive data and are stored in browser storage, which is generally less secure due to vulnerabilities like Cross-Site Scripting (XSS). Cross-Site Scripting (XSS) is a vulnerability that allows attackers to inject malicious scripts into web pages viewed by other users, potentially compromising their data and session.

Secure Storage: For improved security, use HTTP-only cookies to store tokens. These cookies are not accessible via JavaScript, reducing the risk of XSS attacks. Ensure cookies are protected against Cross-Site Request Forgery (CSRF) by using appropriate measures like the host-csrf package. The CSRF package helps prevent Cross-Site Request Forgery (CSRF) attacks by ensuring that requests to a server are made intentionally by the authenticated user, not an attacker.

Route Protection: In Express applications, use authentication middleware to protect routes. The middleware checks for and validates the JWT, storing user details in req.user for use by route handlers. Public routes (e.g., login and registration) should remain accessible without authentication.

Regular security testing is crucial to protect your Node.js CRUD application from common vulnerabilities. By focusing on input validation, authentication, data security, and error handling, and using appropriate tools, you can ensure that your application remains secure.

Error Handling: 

Errors HAPPEN, it's best to prepare for them. Handle errors with the following: 

-express-async-errors to manage asynchronous errors.

-A StatusError class for structured error messages and HTTP status codes.

-An error handling middleware to return appropriate responses, including descriptive messages for expected errors (like validation issues) and generic messages for unexpected errors (server crashes or unhandled exceptions, like null reference errors, edge cases).
Example: 

The `StatusError` class could look like this:

# Refresh:
A class is a blueprint for creating objects with actual values and states.

```javascript
class StatusError extends Error {
  constructor(message, resultCode) {
    super(message);
    this.statusCode = resultCode;
  }
}
```

Using this class, if your authentication middleware finds that the JWT token is missing or invalid, you can just throw the error as follows:

```javascript
throw new StatusError(
  "The request was not authenticated",
  StatusCodes.UNAUTHORIZED
);
```

Then you add appropriate code to the error handler to handle this case, sending back the status code and an appropriate JSON message to the caller.


## Continuing with the Video- DON'T LOSE STEAM, SECURITY IS ESSENTIAL!! YOU GOT THIS! ONE MORE STEP AFTER THIS!

The video instruction for this lesson starts at 5:05:30 and continues to 6:28:35 of this video:
**[CodingAddict - Node.js Projects](https://youtu.be/rltfdjcXjmk?t=18325)**


We want to give you an opportunity to get creative and to do your own work, so for this assignment, you should try creating your own Express applications. Reminder, this is the funnest part where you get to be independent and establish muscle memory. 



1. **Setup:**
   - **Switch to the `05-JWT-Basics` directory and create a `week8` branch.**
     - *Why:* This ensures you're working in the correct directory and on a separate branch for this week’s assignment.
   - **Create a `preferred` folder inside `05-JWT-Basics`.**
     - *Why:* Organizes your work by keeping it separate from other assignments or example code.

2. **Create Express Application:**
   - **Run `npm init` and install `express`, `jsonwebtoken`, and `dotenv`.**
     - *Why:* Initializes a new Node.js project and installs the necessary packages for building and securing your application.
   - **Create a `.gitignore` file with `.env` and `/node_modules`.**
     - *Why:* Prevents sensitive information and unnecessary files from being tracked by Git.

3. **Application Structure:**
   - **Create `app.js` and organize into `routes`, `middleware`, and `controllers` directories.**
     - *Why:* Follows best practices for code organization, making your application modular and easier to manage.

4. **JWT Implementation:**
   - **Use `jsonwebtoken` functions `jwt.sign` and `jwt.verify`.**
     - *Why:* `jwt.sign` generates tokens and `jwt.verify` validates them, essential for secure authentication.
   - **Generate a secure key using [this generator](https://www.random.org/strings/).**
     - *Why:* Ensures your JWTs are secure by using a strong, unpredictable key.

5. **Routes:**
   - **Create the `POST /api/v1/logon` route:**
     - *Why:* Allows users to log in and receive a token, which is necessary for authentication.
   - **Create the `GET /api/v1/hello` route:**
     - *Why:* Provides a protected endpoint that requires a valid token, demonstrating how to secure routes with JWT.

6. **Testing with Postman:**
   - **For the `POST` request: Get and copy the token.**
     - *Why:* You need the token to authenticate requests to protected routes.
   - **For the `GET` request: Configure authorization with the token in Postman.**
     - *Why:* Tests that your application correctly validates the token and handles protected routes.

7. **Optional Frontend:**
   - **Create a simple HTML/JS front end in `preferred/public`.**
     - *Why:* Provides a user interface to interact with your backend, demonstrating how front-end and back-end can work together.
