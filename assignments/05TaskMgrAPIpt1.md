### Warm Up: Array Methods

The Task Manager you develop for this assignment requires you to use a number of methods of the JavaScript `Array` class. You should review those (lesson on [javascript.info](https://javascript.info/array-methods) & handbook on [FreeCodeCamp](https://www.freecodecamp.org/news/the-javascript-array-handbook/)). Open the `03-task-manager/optionalArrayMethodsReviewExtraAssignment.js` file. Instructions are inside the file, with examples. You can optionally implement the challenges required; this is recommended!

### Task Manager with Mongo Database

In this lesson, you will

* Set up a free Mongo Cloud account, and connect to a Mongo NoSQL database
* Perform CRUD operations on that database
* Only work on the back end. This means that to test your work, you must use Postman.

## Warning: Skip download

The instructor suggests that you download code via a link on johnsmilga.com.  
**Don’t do this.**

Just continue to work on the same git repository you initially forked and downloaded for this course, which is `node-express-course`. You do not need to move directories from this git repository.

Merge week 4 to main, update your local main using `git pull origin main`. Create a new git branch called `week5`. **This should be created when the most current main branch is active, so that your work adds on to the work from week 4 that you merged to main.**

This week’s work is to be created in the `03-task-manager/starter` directory. Note that answers, if you get stuck, are in the `03-task-manager/final` directory, but try not to refer to that. Once you have changed directories to the `03-task-manager/starter` directory, you do an `npm install`. This loads the Node modules you will need for the assignment.

> [!CAUTION]
> **Be Careful of Your Mongo Password!**

The instructor pastes the Mongo database URI into the code. It includes a password. You may do the same to make sure it works. However, in general, you would _**NEVER**_ put a password or API key into your code because, when you push it to Github, it becomes public and anyone can access your data. There are hackers with Github scrapers that go looking for just such an exposure. A little later in the lesson, the instructor moves the Mongo URI into a `.env` file. This is where it should be kept.

You will notice a `.gitignore` file in the `03-task-manager/starter` directory. That contains lines for `/node_modules` and `.env`, which are the files you _do not_ want in Github. The `.gitignore` file is very important! **Do not git add, git commit, or git push your code while the Mongo URI is included in the code.** Be sure it is _**completely removed**_ from the code, not just commented out! If you make a mistake and git commit your code with a password in it, the ONLY recovery is to change the password. This is because git keeps every old version of your code!

In the future, you would create the `.env` file at the start of any project, and you would make sure that the `.gitignore` file includes `.env`, before putting any secrets like the Mongo password into the `.env`. You would never put such secrets in your code, even temporarily.


## Coding Challenges:
You'll notice in the article you will read during your mindset assignment for this week that FizzBuzz and other programming challenges are mentioned. Let's take a peek at the wonderful world of coding challenges.
 - Make a Leet Code and HackerRank account and solve FizzBuzz
[https://leetcode.com/problems/fizz-buzz/](https://leetcode.com/problems/fizz-buzz/)
