aIn this lesson, you create a front end for the Jobs API you created in the previous lesson. Front ends may be created in various ways, for example using React, and they may run in various environments, such as an app for a smart phone. The front end for this lesson is created using just HTML and JavaScript. It runs in a browser, and is loaded from the same Express instance as the API it calls. That is, you will be creating “server-rendered” pages.

**There is no video for this lesson. Instead, there are detailed instructions in the Assignment section.**

**Note:** This lesson appears to be mostly copy/paste — but it may not be depending on what you did the last few weeks! You create forms and tables, but if you used a data model different from Job, as was recommended in lessons 9 and 10, you must modify the HTML and JavaScript so that the forms, tables, and JavaScript variables match your data model. This may seem like a lot of work, and perhaps it is, but once you have completed it, if you used a data model different from the Job model used by the instructor (or you at least substantially extended that model) then you are well on your way to completing your class final project.


In this lesson, you learn `EJS` (Embedded Javascript), a templating language for Express. The templates contain embedded JavaScript, which is executed on the server side. This constructs an ordinary HTML page, but with dynamic content. Because the embedded JavaScript runs on the server, before the page is sent to the client, dynamic content can be delivered, such as information from a database. 

This allows you as a developer to "inject" data and functionality into your html.
This is called “server-side rendering”. The templates are ordinary HTML files, which may be combined with CSS and client-side JavaScript.

Server-side rendering is in some respects easier for you as the developer than writing first an API and then a front end for it, where the front end makes fetch calls to the API. On the other hand, if you don’t create an API, you can’t access the data via React or other front ends that run outside the application itself. There are other advantages and disadvantages. Frequently, an application will use both methods, using some server-side rendering for the administrator user interface and front-end/back-end for the end-user interface. 

After creating a .ejs file, you will primarily use these syntax tags (also known as scriplets or squids) to inject data and functionality into your HTML 


```
<%- include 'filename' %>
<% no-output code ie. conditionals %>
<%= output code or retreived data %>
```


In the file (template) itself it might looks something like this:

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
 <% if(typeof user !== 'undefined'){ %>
      <button> Log In!
      </button>
  <% } else { %>

<%- 'partials/user-navbar' %>

 <% } %>

<p> Here is the hike trail: <%- 'views/trail' %></p>

<% let items = ['backpack', 'flashlight', 'canteen', 'tent', 'compass'] %>

<% for(let i = 1; i < items.length; i++) { %>

  <p>You will need: <%= items[i] %></p>

<% } %>

<%- 'partials/footer' %>

</body>
</html>
```



All are encased in the `<% %>` sequence.
Using these scriplets you can include 

`<%-` “includes” other templates, so that you can have headers, footers, and other partials without repeating surrounding HTML

`<%` executes code but does not return any change to the HTML. This is used for logic statements, such as `if` statements and `for` loops.

`<%=` executes code and returns the result in line as HTML.

---

Please be sure that you understand where each piece of JavaScript executes!

The JavaScript for your controllers, routes, middleware, etc. executes on the server side. If you do a `console.log` for this code, it appears in the server terminal. The code you put into an EJS file also executes on the server side, to customize the page with variable data before it is sent to the browser.

However, you can also put JavaScript into an HTML or EJS page, or load it from a script, where the JavaScript is _not_ within the EJS `<% %>` enclosure. That JavaScript is loaded by the browser and runs in the browser context, which means that it has access to the window and the DOM, but it does not have access to server side data and the database. Anything logged by `console.log` in thatcase would appear in the browser DevTools console.
