## Refresh
JSON (JavaScript Object Notation) is a simple format for storing and exchanging data, which is consistent and easy to read and write for both humans and machines.

## Watch the Video

- Finish watching **[this video](https://youtu.be/Oe421EPjeBE?t=13246)**.
- Focus on the part from **6:10:46** to the end of the video.
- The video explains how to handle form data and JSON data in requests and responses.

## What You Will Learn

1. **Middleware**
   - Learn about middleware, which is code that runs before your main request handlers.

2. **HTTP Methods**
   - How you will use different HTTP methods in your API development:
     - **`GET`**: Retrieve data.
     - **`POST`**: Send new data.
     - **`PUT`**: Update existing data.
     - **`PATCH`**: Partially update data.
     - **`DELETE`**: Remove data.

3. **Testing with Postman**
   - Test these HTTP methods using Postman to make sure requests and responses are working as expected.

4. **Refactoring Code**
   - Improve your code by separating the router and controller functions.

## Front End Interaction

- **Two Ways to Call APIs:**
  1. **Using HTML**
     - Send `GET` and `POST` requests from a standard HTML page.
     - `POST` requests send form data.

  2. **Using JavaScript**
     - JavaScript can send `GET`, `POST`, `PUT`, and `DELETE` requests.
     - Use JSON to send and receive data.

- **Find the Front End**
  - Check the `methods-public` directory.
  - Review the two HTML files to see how to call the backend using HTML and JavaScript.



This optional assignment gives some idea of how authentication might work. You will use the `cookie-parser` npm package, so do an `npm install` for that package. Cookies are set, typically by the back end, the browser then stores them and attaches them to each subsequent request. This allows us to add some “state” to each HTTP request. That is, the browser and backend can ‘remember’ some information automatically across requests, like for example, which user is making these requests. Add to `app.js` a require statement for `cookie-parser`. Then, right after you parse the body of the request, add a statement to parse the cookies:

```javascript
app.use(cookieParser());
```

Now write a middleware function called `auth`. This checks for `req.cookies.name`. If that cookie is present, it sets` req.user` to the value, and calls `next`. If it is absent, it sets the res status to [401](https://http.dev/401) (which means unauthorized), and returns a message in a JSON object that says “unauthorized”. It **_does not_** call `next()` in this case. (Typically middleware would throw an error at this point, instead of returning a result.) Now add an `app.post("/logon")`, which should require a name in the body. If it is present, it should do a `res.cookie("name", req.body.name)`, and send back a 201 result code plus a message that says hello to the user. If name is not present, it should return a 400 and an error message in JSON. Now add an a`pp.delete("/logoff")`. This should do a `res.clearCookie("name")`, and then it should return a 200, with a message in JSON that the user is logged off. Now add an `app.get("/test")`. The auth middleware should be invoked in this `app.get` statement. The get should just return a 200, plus a message in JSON that says welcome to the user, whose name is in `req.user`. Then test this with Postman. You should be able to logon, logoff, and test, and the test should do something different depending on whether or not you are logged in.

When you have completed your programming assignment, git add, git commit, and git push your branch, and create a pull request, so that you can include a link to your pull request in your homework submission.
