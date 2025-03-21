In this lesson, you use the `passport` and `passport-local` npm packages to handle user authentication, from within a server-side rendered application.

### First Steps

You continue to work with the same repository as the previous lesson, but you create a new branch called `lesson13`.

The user records are stored in the Mongo database, just as for the Jobs API lesson. You have already copied the `models` directory tree from the Jobs API lesson into the `jobs-ejs` repository. The user model is used unchanged. You configure passport to use that model.

To begin, you will need the following views:

```
views/index.ejs
views/logon.ejs
views/register.ejs
```

The `index.ejs` view just shows links to login or register. The `logon.ejs` view collects the email and password from the user. The register collects the name, email, and password for a new user. We want to use the partials as well. We want to modify the header partial to give the name of the logged on user, and to add a logoff button if a user is logged on.

`views/index.ejs`:

```
<%- include("partials/head.ejs") %>
<%- include("partials/header.ejs") %>
<% if (user) { %>
    <a href="/secretWord">Click this link to view/change the secret word.</a>
<% } else { %>
    <a href="/sessions/logon">Click this link to logon.</a>
    <a href="/sessions/register">Click this link to register.</a>
<% } %>
<%- include("partials/footer.ejs") %>
```

`views/logon.ejs`:

```
<%- include("partials/head.ejs") %>
<%- include("partials/header.ejs") %>
<form method="POST">
  <div>
    <label name="email">Enter your email:</label>
    <input name="email" />
  </div>
  <div>
    <label name="password">Enter your password:</label>
    <input type="password" name="password" />
  </div>
  <div>
    <button>Logon</button>
    <a href="/">
      <button type="button">Cancel</button>
    </a>
  </div>
</form>
<%- include("partials/footer.ejs") %>
```

`views/register.js`

```
<%- include("partials/head.ejs") %>
<%- include("partials/header.ejs") %>
<form method="POST">
  <div>
    <label name="name">Enter your name:</label>
    <input name="name" />
  </div>
  <div>
    <label name="email">Enter your email:</label>
    <input name="email" />
  </div>
  <div>
    <label name="password">Enter your password:</label>
    <input type="password" name="password" />
  </div>
  <div>
    <label name="password1">Confirm your password:</label>
    <input type="password" name="password1" />
  </div>
  <div>
    <button>Register</button>
    <a href="/">
      <button type="button">Cancel</button>
    </a>
  </div>
</form>
<%- include("partials/footer.ejs") %>
```

Revised `views/partials/header.ejs`:

```javascript (EJS)
<h1>The Jobs EJS Application</h1>
<% if (user) { %>
   <p>User <%= user.name %> is logged on.</p>
   <form method="POST" action="/sessions/logoff">
   <button>Logoff</button>
   </form>
<% } %>
<% if (errors) {
    errors.forEach((err) => { %>
      <div>
        Error: <%= err %>
      </div>
    <% })
  } %>
  <% if (info) {
    info.forEach((msg) => { %>
      <div>
        Info: <%= msg %>
      </div>
    <% })
  } %>
<hr />
```

These changes won’t suffice to do anything in the application, until routes are added to match. We need to follow best practices, with separate route and controller files.

### Router and Controller

Create a file `routes/sessionRoutes.js`, as follows:

```javascript
const express = require("express");
// const passport = require("passport");
const router = express.Router();

const {
  logonShow,
  registerShow,
  registerDo,
  logoff,
} = require("../controllers/sessionController");

router.route("/register").get(registerShow).post(registerDo);
router
  .route("/logon")
  .get(logonShow)
  .post(
    // passport.authenticate("local", {
    //   successRedirect: "/",
    //   failureRedirect: "/sessions/logon",
    //   failureFlash: true,
    // })
    (req, res) => {
      res.send("Not yet implemented.");
    }
  );
router.route("/logoff").post(logoff);

module.exports = router;
```

Ignore the passport lines for the moment. This just sets up the routes. We need to create a corresponding file `controllers/sessionController.js`. Here we use the `User` model. However, the file you copied makes some references to the JWT library. You must edit `models/User.js` to remove those references in order for `User.js` to load. We aren’t using JWTs in this project.

```javascript
const User = require("../models/User");
const parseVErr = require("../util/parseValidationErr");

const registerShow = (req, res) => {
  res.render("register");
};

const registerDo = async (req, res, next) => {
  if (req.body.password != req.body.password1) {
    req.flash("error", "The passwords entered do not match.");
    return res.render("register", {  errors: flash("errors") });
  }
  try {
    await User.create(req.body);
  } catch (e) {
    if (e.constructor.name === "ValidationError") {
      parseVErr(e, req);
    } else if (e.name === "MongoServerError" && e.code === 11000) {
      req.flash("error", "That email address is already registered.");
    } else {
      return next(e);
    }
    return res.render("register", {  errors: flash("errors") });
  }
  res.redirect("/");
};

const logoff = (req, res) => {
  req.session.destroy(function (err) {
    if (err) {
      console.log(err);
    }
    res.redirect("/");
  });
};

const logonShow = (req, res) => {
  if (req.user) {
    return res.redirect("/");
  }
  res.render("logon", {
    errors: req.flash("error"),
    info: req.flash("info"),
  });
};

module.exports = {
  registerShow,
  registerDo,
  logoff,
  logonShow,
};
```

We have two endpoints that handle just rendering an EJS page, `registerShow` and `logonShow`.

We then have endpoints for actually performing the logoff and register actions. We don’t need a controller handler for login, because Passport handles that for us.

The `registerDo` handler will check if the two passwords the user entered match, and refresh the page otherwise. If all is good there, it will create a user in the database and redirect to the home page. The creation of the user entry in Mongo is just the same as it was for the Jobs API. We also have some error handling cases here.

If there is a Mongoose validation error when creating a user record, we need to parse the validation error object to return the issues to the user in a more helpful format, and we do that in the file util/parseValidationErrs.js:

```javascript
const parseValidationErrors = (e, req) => {
  const keys = Object.keys(e.errors);
  keys.forEach((key) => {
    req.flash("error", key + ": " + e.errors[key].properties.message);
  });
};

module.exports = parseValidationErrors;
```

We need some middleware to load `res.locals` with any variables we need, like the logged in user and flash properties. Create `middleware/storeLocals.js`:

```javascript
const storeLocals = (req, res, next) => {
  if (req.user) {
    res.locals.user = req.user;
  } else {
    res.locals.user = null;
  }
  res.locals.info = req.flash("info");
  res.locals.errors = req.flash("error");
  next();
};

module.exports = storeLocals;
```

Now, we need a couple of `app.use` statements. Add these lines right after the `connect-flash` line:

```javascript
app.use(require("./middleware/storeLocals"));
app.get("/", (req, res) => {
  res.render("index");
});
app.use("/sessions", require("./routes/sessionRoutes"));
```

The storeLocals middleware sets the values for errors, info, and user, but in registerDo above, we have to pass the value for errors on the render call, because we changed the value of the flash errors after storeLocals ran.

We are now using the database. So, we need to connect to it at startup. You need a file, `db/connect.js`. Check that it looks like the following:

```javascript
const mongoose = require("mongoose");

const connectDB = (url) => {
  return mongoose.connect(url, {});
};

module.exports = connectDB;
```

Then add this line to `app.js`, just before the listen line:

```javascript
await require("./db/connect")(process.env.MONGO_URI);
```

Then try the application out, starting at the `"/"` URL. You can try each of the new views. But you still can’t logon. The logon operation is commented out, because Passport is not set up.

### Configuring Passport

To use Passport, you have to tell it how to authenticate users, retrieving them from the database. Create a file `passport/passportInit.js`, as follows:

```javascript
const passport = require("passport");
const LocalStrategy = require("passport-local").Strategy;
const User = require("../models/User");

const passportInit = () => {
  passport.use(
    "local",
    new LocalStrategy(
      { usernameField: "email", passwordField: "password" },
      async (email, password, done) => {
        try {
          const user = await User.findOne({ email: email });
          if (!user) {
            return done(null, false, { message: "Incorrect credentials." });
          }

          const result = await user.comparePassword(password);
          if (result) {
            return done(null, user);
          } else {
            return done(null, false, { message: "Incorrect credentials." });
          }
        } catch (e) {
          return done(e);
        }
      }
    )
  );

  passport.serializeUser(async function (user, done) {
    done(null, user.id);
  });

  passport.deserializeUser(async function (id, done) {
    try {
      const user = await User.findById(id);
      if (!user) {
        return done(new Error("user not found"));
      }
      return done(null, user);
    } catch (e) {
      done(e);
    }
  });
};

module.exports = passportInit;
```

Here we are registering a “strategy” to tell Passport how to handle requests that we pass to it `passport.use` is a function that takes the name you want to give this passport strategy (here we’re using `"local"`) and the strategy as the second argument, where we’re passing in a `new LocalStrategy` from the `passport-local` library.

The `LocalStrategy` constructor takes two arguments: an options object, and a callback function. The options object expects us to tell the strategy what field on the request will have the user identifier, and what field will have the password. Here, we tell it to look for `"email"` as the identifier, and `password` for the password.

The second argument passed to the `LocalStrategy` constructor is the callback function that will be called when we do `passport.authenticate(...)` in the login route in `sessionRoutes.js`. The `local-strategy` library will extract the `email` and `password` fields that we defined in the options/first argument, from the `req.body`. If it doesn’t find those fields, it will return a 400 error. If it does find them, then it will then pass those (along with a `done` callback) to the function we’ve defined above. It’s up to us then to write the code specific to our application, that handles checking if the user exists and has used to correct password.

The `done` callback accepts three arguments:

1. An error, if there is one, otherwise just pass in `null`
2. The user object, if the user is found and used valid credentials, otherwise `false`
3. An object with a `message` property and `type`, this can be used in both error and success cases to show flash messages. Here we’e only using it in non-error failure cases (user not found or wrong credentials used).

In addition to registering our local strategy, we also define `serializeUser` and `deserializeUser` functions on the `passport` object.

`serializeUser` is used when saving a user to the request session object. We can’t save an object to the session cookie, so we need to “serialize” it a.k.a. encode it as a string. In the above function, we’re doing that by telling Passport to save just the user id to the session cookie.

Then when Passport is handling a protected route, it will use the `deserializeUser` function to retrieve the user from the database, using the id that was saved to the session cookie.

You can now add the following lines to `app.js`, right _after_ the `app.use` for session (Passport relies on session):

```javascript
const passport = require("passport");
const passportInit = require("./passport/passportInit");

passportInit();
app.use(passport.initialize());
app.use(passport.session());
```

First we call the `passportInit` function that we created in the previous section. This registers our `local` Passport strategy, and sets up the `serializeUser` and `deserializeUser` functions onto the `passport` object.

Then we call `passport.initialize()` (which sets up Passport to work with Express and sessions) and `passport.session()` (which sets up an Express middleware that runs on all requests, checks the session cookie for a user id, and if it finds one, deserializes and attaches it to the `req.user` property).

Finally, you can now uncomment the lines having to do with Passport in `routes/sessionRoutes.js`, so that the require statement for Passport is included, and so that the route for logon looks like

```javascript
router
  .route("/logon")
  .get(logonShow)
  .post(
    passport.authenticate("local", {
      successRedirect: "/",
      failureRedirect: "/sessions/logon",
      failureFlash: true,
    })
  );
```

This means that when someone sends a `POST` request to the `/sessions/logon` path, Passport will call the function we defined earlier and registered to the name `"local"`. If that function completes successfully (`done(...)` is called with no error argument), then it will redirect the page to the `successRedirect` page. If there is an error, then it will redirect to the `failureRedirect` page, and also set a flash message with the `message` property from the object we passed to `done(...)`.

Since we’re letting Passport handle setting the `req.flash` properties now, we can remove the lines in `controllers/sessionController.js` that set the flash messages for the `loginShow` handler. So that should now just look like:

```javascript
const logonShow = (req, res) => {
  if (req.user) {
    return res.redirect("/");
  }
  res.render("logon");
};
```

After that, try logon for one of the accounts you have created. You should see that you are logged in and can access the `secretWord` page. You should also see appropriate error messages for bad logon credentials. Also, test logoff.

### Protecting a Route

To protect a route, you need some middleware, as follows.

`middleware/auth.js`:

```javascript
const authMiddleware = (req, res, next) => {
  if (!req.user) {
    req.flash("error", "You can't access that page before logon.");
    res.redirect("/");
  } else {
    next();
  }
};

module.exports = authMiddleware;
```

`req.user` is injected into the `req` object by `passport.session()`. We can check if it exists (a.k.a. if the user is logged-in) in this middleware and use that to determine if the non-logged-in requester should be redirected to the home page, or if the logged-in user should be allowed to continue to the next middleware or controller handler function.

We want to protect any route for the `"/secretWord"` path. The best practice is to put the code for those routes into a router file, as follows.

`routes/secretWord.js`:

```javascript
const express = require("express");
const router = express.Router();

router.get("/", (req, res) => {
  if (!req.session.secretWord) {
    req.session.secretWord = "syzygy";
  }

  res.render("secretWord", { secretWord: req.session.secretWord });
});

router.post("/", (req, res) => {
  if (req.body.secretWord.toUpperCase()[0] == "P") {
    req.flash("error", "That word won't work!");
    req.flash("error", "You can't use words that start with p.");
  } else {
    req.session.secretWord = req.body.secretWord;
    req.flash("info", "The secret word was changed.");
  }

  res.redirect("/secretWord");
});

module.exports = router;
```

We could further refactor this by moving the code for handling the routes (`(req, res) => {...}`) a controller file, like we’ve done for the session routes, but we’ll leave it like this for now.

Next let’s replace the `app.get` and `app.post` statements for the `"/secretWord"` routes in `app.js` with these lines:

```javascript
const secretWordRouter = require("./routes/secretWord");
app.use("/secretWord", secretWordRouter);
```

Then try out the secretWord page to make sure it still works. Turning on protection is simple. You add the authentication middleware to the route above as follows:

```javascript
const auth = require("./middleware/auth");
app.use("/secretWord", auth, secretWordRouter);
```

That causes the authentication middleware to run before the `secretWordRouter`, and it redirects if any requests are made for those routes before logon. Try it out: login and verify that you can see and change the secretWord. Then log off and try to go to the `"/secretWord"` URL.


## Hungry For More
Introducing Typescript, Let's Go Docsss!!

<https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes.html>

<https://www.typescriptlang.org/docs/>

### RMOR Comprehension Check:
So you don't redirect off this lesson page, right click the link and select "Open Link in New Tab" to [take the FINAL RMOR Comprehension Check as review of what you learned throughout our class](https://airtable.com/appoSRJMlXH9KvE6w/shryhKpeBKvsEl1Q9?prefill_Lesson=Node%20v3:%20Lesson%2013%20-%20Authentication%20with%20Passport)
