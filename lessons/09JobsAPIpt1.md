## Thinking About Your Final Project


In this lesson, as in the previous one, you can choose to implement some content different from what the instructor shows. Parts of this lesson and the following lesson will be iterative, especially with initial set up. Dust off vacation, and launch right in. Try to imagine something for an application you’d like to invent! The instructor shows CRUD operations for job records, and uses a Job model. However, **you can choose to store objects of a different kind instead of job records, this is especially recommended if you fell behind before break**. This work could then comprise the beginning of your final project. Look at the **[final project rubric here](https://github.com/Code-the-Dream-School/node-v3/blob/c21bba9b92cd445ba649396219a742914d52749a/assignments/rubric.md)** to see what is required. (Bear in mind, though, that there are two ways to go in the final project — either using a front end and back end, or using server side rendering, which we haven’t covered yet.)

If you do implement a model different from the Job model, it should still have a `createdBy` attribute, which is a reference to a `User` record, to associate each entry with a particular user, and the `createdBy` attribute should be of type `mongoose.Types.ObjectId`. This is for access control: A particular user can do CRUD operations only on their own records. Your model should also have an entry that is an `enum` type. You use an enum when an attribute can take only a small set of values, like “vanilla”, “chocolate”, and “strawberry” for ice cream flavors. See the instructor’s work for the `Job` model in the final directory for an example, both of how to do the `createdBy` attribute and how to do an enum. You are encouraged to use a variety of data types in your model such as numbers, strings, and dates.

## Concepts: Authentication with JWT Tokens

In this lesson as in the previous one, you use JSON web tokens (JWTs) for authenticating the user. But, in this case, you do store user records in MongoDB, so you have a User model established. You store the User’s name, email, and hashed password in the database. **We never store passwords in plain text**. Instead, they are cryptographically hashed so that even if the database is compromised, the passwords are not. The cryptography for the password comes from the `bcryptjs` npm package. The hashing is performed in a middleware routine that is added to the `User` model, which is a pre-routine for the save operation (meaning that it will run before saving data to the database for any `.save()` call). You also add instance methods to the `User` model for generating the `JWT` and for validating the user password. When you do so, you use the `function` keyword, not the arrow function syntax, so that the function is associated with the `this` variable correctly. In this case `this` will be the user instance that’s being operated on. You also set timestamps on your entries, just as the instructor does.

As in the previous lesson, you use authentication middleware to protect routes.

## Concepts: Access Control for Entries

The `createdBy` field is used to control who can access certain entries. For each CRUD operation (Create, Read, Update, Delete), you use the User ID of the currently logged-in user. This User ID is stored in `req.user` by the authentication middleware when it checks the JWT token.

When you create a new `Job` entry (or a new model if you use a different one), you save the User ID in the `createdBy` field. This ensures that each entry is linked to the user who created it.

When retrieving, updating, or deleting `Job` entries, you include the User ID in your Mongoose query to ensure users can only access or modify their own records and not those of other users.

For this lesson, you will create an API only. Although the instructor mentions a front end, it is not provided. Therefore, you need to test your API routes using Postman.




## Continuing with the Video

This lesson runs from 6:28:35 to 8:20:35. **Read the Coding Assignment Instructions before watching the video, so that you know how your assignment will differ from the video instructions.**  

**[FreeCodeCamp Video](https://www.youtube.com/watch?v=rltfdjcXjmk?t=23306)** 

As with previous lessons, you duplicate the work that the instructor shows, except that instead of creating a Job model, you can choose to create a model of your own choosing. (You can use the `Job` model the instructor uses if you prefer, but it would have to be extended to make a final project.)


