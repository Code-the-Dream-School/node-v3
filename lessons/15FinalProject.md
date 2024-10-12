As you complete your final projects this week keep in mind the following:

## Goal of the Application
The goal of the project is to showcase what you have learned during class. You will have the opportunity to demonstrate your knowledge and creativity. You are required to create an Express application from scratch. Refer back to your approved proposal to make sure your project is taking shape how you intend.

## Check your work
* Does your project demonstrate the skills you have learned in the class series so far?  
* Did you have an opportunity to demonstrate creativity, which is important for a developer.
You may find that you want to use some concepts, technologies, or npm packages we didn’t cover now or in the future to improve your application, but remember to keep a working version to demo.
* Have you successfully deployed the full application to Render.com?

Although you will need to keep your final project simple, think about an application you might want to create eventually. Perhaps you could implement some subset or feature of this future application.

## Remember to be careful with Your MongoDB Password
Do not include the MongoDB URI in your code, even temporarily. Use the dotenv NPM package so that it can be stored in a .env file. Be sure you have a .gitignore file so that the .env file and the node_modules directory are not delivered to Github or Render.com.

## Reminder of Requirements for the Project (Rubric)
 - [ ] Create a Node/Express application from scratch using the MongoDB database. It must contain the following elements: 

### Models & Controllers

 - [ ] At least two Mongoose data models. One of these must be a User data model, as you need to implement logon.
 - [ ] Implement user registration and logon. If you are doing server side rendering, authentication must use Passport. If you are doing a full stack project, authentication must use JWT tokens. Passwords must be stored hashed.
 - [ ] Model attributes should use several different data types (number, string, boolean, date, array etc.).
 - [ ] Include validation of your attributes to prevent the creation of invalid records.
 - [ ] For any models beside the User model, implement all the CRUD (create, read, update, delete) operations in your controllers and routes.
 - [ ] Bonus: implement some non-CRUD operations (like searching, sorting, paging, etc.).
 - [ ] Implement access control middleware so that at least the create/update/delete operations require authentication. You can have unauthenticated read operations if it makes sense in your application.
 - [ ] Implement access control logic in your controllers, so that one user can’t access another user’s data. This logic must be present for every controller operation or your application is not secure.
 - [ ] Include appropriate notifications to the user. For full stack applications, the messages should be returned as needed with the API. (For some APIs, the HTTP status code suffices.) Then the front end displays the message or messages to the user. For server side rendered applications, you need to store the message in the user session, perhaps using the connect-flash NPM package.
 - [ ] Implement error handling middleware so that all exceptions and error conditions are handled and so that the user gets user friendly messages for each event.
 - [ ] Use best practices in the organization of application code and in indentation. You may want to use eslint and prettier to make sure your code complies.

### User Interface

The user interface is the front end for full stack applications, or the EJS views for server side rendered applications. In either case, the UI should have these capabilities:
 - [ ] Registration, logon, and logoff are supported.
 - [ ] All CRUD operations for each of the data models besided the User model are supported.
 - [ ] Links or buttons should be provided to help the users navigate the application.
 - [ ] Style your application. Again, this is not the focus, so keep it simple until you have done everything else.

### Deployment

 - [ ] Include security protections for your application. Include security packages like xss-clean and helmet, appropriately configured.
 - [ ] Deploy the application to Render.com.

### Bonus Items (these are entirely optional)

 - [ ] Do something extra.  This could be the implementation of a more complicated data model, or use of additional NPM packages, callouts to other public APIs, or whatever your creativity inspires.
 - [ ] Implement some test cases using Mocha, Chai, and Puppeteer.
 - [ ] For full stack applications, implement Swagger to document the API.

## Submission

You should submit a link to a Github repository which contains your application in the first Link field on the submission form. Submit the link to your deployed application on Render.com using the second link field.  It is highly encouraged that you use git branches to implement each feature. This is so that if you make a mistake, it does not ruin the work you have done up to that point. Use your usual Submit Assignment button on your lesson page for the Final Project Completion lesson. The form will be slightly different than usual as we will ask what you would like to do with our program next.

## Presentation

Each student should make a 3-5 minute recording demonstrating your final project.  The presentation of your final project is not graded or assessed in anyway.  Presentations are intended to give you practice speaking to others about your work and for classmates to celebrate the successes they have achieved throughout class.
