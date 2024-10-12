When you are creating APIs, you can perform authentication using JavaScript Web Tokens (JWTs). The front end makes an API call passing credentials to the back end, and the back end returns a token, either in the body of the response or by setting a cookie. The front end then passes this token to the back end on all subsequent requests.

When the application does not have a separate front end to invoke the APIs, only the cookie approach can work. The browser is making the requests, and browsers cannot call arbitrary APIs or send authorization headers. But there has to be _some_ way to save state, such as the state of being logged on. For applications without a way to call various API endpoints, like server-side rendered applications (that don’t have any client-side scripts), this is done using “sessions”, and sessions are established and maintained using cookies.

This way of handling security can be used for APIs as well, if the APIs are to be called from a browser. And, when using a browser, the cookie based approach is more secure, because sensitive information such as the JWT is not stored in local storage. However, when one server calls another, the cookie-based approach can’t be used, as cookies only have meaning for browsers.

This is the general pattern that would be used in a cookie-based authentication flow:

1. The browser requests the logon page from the server (`GET` request), and then sends the credentials (eg: username and password) that were obtained from the user (`POST` request).
2. The server verifies the credentials, and if verification is successful, the server sends a response that includes a `set-cookie` response header to the browser. The cookie is a cryptographically signed string, signed with a secret key so that it can’t be counterfeited by a malicious user. The browser automatically includes the cookie in the header of all subsequent requests to the same URL, until the cookie expires.
3. For all protected routes, the server has middleware that validates the cookie. Different browser sessions from different users have different cookie values, so the server can tell which user is making the request. On the server side, the cookie is used as a key to access session state data, which is kept on the server. This state data is the user’s session.


### Accessibility (also referred to as A11y)

Take a moment and think of a time when there was something you wanted or needed but didn’t have access to it for some reason or another. Being denied access to something you want or need can feel beyond frustrating.

The internet is a very powerful tool. So many businesses give extra discounts to people with accounts on their sites; government offices keep forms on their sites now instead of keeping paper copies; medical offices now use client portals for people to be able to access and pay their accounts, scheduled appointments and services. Not being able to get around and use any of these sites can make something that was supposed to be a better/easier alternative seem like a huge stumbling block.

Accessibility focuses on making sure that those of us who are helping building these structures build them in a way that EVERYONE can use them easily. Last week you got an introduction into the challenges some people face when trying to use and interact with websites. Read the [WebAim site](https://webaim.org/intro/#implementing) starting with the “Implementing Web Accessibility” section then check out the [A11y Checklist](https://www.a11yproject.com/checklist/). We strongly recommend bookmarking a tool you can run your code through to help check for accessibility compliance ([Wave](https://wave.webaim.org/) from WebAIM) or a simple tool you can add to your code to help you check accessibility features on your site (like [totA11y](https://khan.github.io/tota11y/) from Khan Academy).

Accessibility is a way bigger topic than we can cover here, but hopefully this starts your wheels turning about how to be sure that the awesome things you build throughout your career can be easily used by everyone.

This article talks about [the importance of color alone](https://userway.org/blog/why-is-color-contrast-so-critical)

Take a few moments now and consider the following: 
When you’ve had limited or no access to something, what did you do? Were you ultimately able to get what you needed? If not, how did your lack of access impact your life?

Now that you’ve read about accessibility, and hopefully considered some of the challenges others face using the internet, perhaps there are things you can/will do differently in your current/future project(s) to help get into good accessibility habits as a programmer.


## Hungry For More
Introducing Typescript, Let's Go Docsss!!

<https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes.html>

<https://www.typescriptlang.org/docs/>
