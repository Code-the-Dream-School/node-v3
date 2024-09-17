In this lesson, you complete implementation of the CRUD operations for the API, using either the `Job` model as the instructor does, or the model you invented in the last lesson. You test with Postman as you go. Your Postman configuration should have environment variables for the URL and, as the instructor explains, the accessToken. You will improve the error handling to return meaningful error messages to the user when Mongoose validation errors occur. You then add security protection for the application so that it can be deployed on the Internet. The security configuration uses the following node packages:

* [helmet](https://www.npmjs.com/package/helmet) for setting various HTTP headers to protect against well-known vulnerabilities
* [cors](https://www.npmjs.com/package/cors) for enabling cross-origin resource sharing
* [xss-clean](https://www.npmjs.com/package/xss-clean) for preventing cross-site scripting attacks. Note that this package is now deprecated. We can still use it for this assignment, but we will need to find a replacement for it in the future.
* [express-rate-limit](https://www.npmjs.com/package/express-rate-limit) for limiting the number of requests from a single IP address. This is to prevent denial of service attacks.

These packages must be used whenever you deploy an application publicly, to minimize the chance of a security exposure. For your class final project, you will use these same packages, because you will deploy your final project on the Internet, and you want it to be secure.

As for the previous lesson, you may duplicate the work that the instructor shows, or if in the last lesson you invented your own model to use instead of the `Job` model, you instead implement CRUD operations for your model. You continue to put your work in the new `06-jobs-api` **repository** that you forked and cloned last session. If you get stuck, answers are in the `node-express -course/06-jobs-api/final` directory, and it’s certainly a good idea to read the instructors code, **but please try to do your own work.** Before you start this lesson, you create the `week10` git branch, **which should be created when the `week9` git branch is active**. This lesson runs from 8:20:35 to 9:34:30 of **[this video](https://youtu.be/rltfdjcXjmk?t=30036)**.

The instructor shows how to deploy to Heroku. However, since this video was made, Heroku has announced that they are ending free access for deploying web applications. **Therefore, do not install the Heroku CLI, and do not deploy to Heroku.** Instead, you deploy your application to Render.com. Instructions for deploying to Render.com are found in the [Assignment section](/node-express/lesson10-a1).

### Concepts: Internet Deployment

When you put your application online, it's important to make sure it's secure. Even though your application doesn't handle sensitive information, taking steps to ensure security is still crucial. Luckily, the packages recommended by the instructor are great starting points!

**CORS** (Cross-Origin Resource Sharing) helps web applications interact with each other, even if they come from different origins (base URLs). For our lesson 12, since the front end and back end are on the same base URL, CORS isn’t needed. However, if you use a framework like React for your final project and it runs on a different base URL, you'll need to set up CORS. Don't worry—by configuring it properly, you can avoid potential security issues. The `npm CORS` package documentation will guide you through the setup.

**xss-clean** is a handy package that protects your application from Cross-Site Scripting (XSS) attacks. This kind of attack happens when an attacker inserts malicious JavaScript into your app through URLs, REST requests, or HTML forms. The `xss-clean` package will automatically remove these harmful scripts to keep your app safe.

**helmet** adds extra security by setting special headers on your web pages, helping to control which scripts can be loaded. It might seem a bit complex at first, especially if you're using resources like Bootstrap, but it’s a powerful tool for enhancing your app’s security.

**express-rate-limit** is like a safeguard for your app, limiting how many requests a single client can make in a minute. This prevents attackers from flooding your app with too many requests and helps keep your application running smoothly.

You're doing great by learning and applying these practices that ensure security for your Users. Let's Go!!!