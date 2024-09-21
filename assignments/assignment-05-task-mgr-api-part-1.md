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

Create a new git branch called `week5`. **This should be created when the week4 branch is active, so that your work adds on to the work of the week4 branch.**

This week’s work is to be created in the `03-task-manager/starter` directory. Note that answers, if you get stuck, are in the `03-task-manager/final` directory, but try not to refer to that. Once you have changed directories to the `03-task-manager/starter` directory, you do an `npm install`. This loads the Node modules you will need for the assignment.

## ⚠️ **Warning: Be Careful of Your Mongo Password!** ⚠️

The instructor pastes the Mongo database URI into the code. It includes a password. You may do the same to make sure it works. However, in general, you would _**NEVER**_ put a password or API key into your code because, when you push it to Github, it becomes public and anyone can access your data. There are hackers with Github scrapers that go looking for just such an exposure. A little later in the lesson, the instructor moves the Mongo URI into a `.env` file. This is where it should be kept.

You will notice a `.gitignore` file in the `03-task-manager/starter` directory. That contains lines for `/node_modules` and `.env`, which are the files you _do not_ want in Github. The `.gitignore` file is very important! **Do not git add, git commit, or git push your code while the Mongo URI is included in the code.** Be sure it is _**completely removed**_ from the code, not just commented out! If you make a mistake and git commit your code with a password in it, the ONLY recovery is to change the password. This is because git keeps every old version of your code!

In the future, you would create the `.env` file at the start of any project, and you would make sure that the `.gitignore` file includes `.env`, before putting any secrets like the Mongo password into the `.env`. You would never put such secrets in your code, even temporarily.


### Mindset Assignment
Comfort with the Unknown

Being afraid of the unknown is part of the human experience. None of us know what tomorrow may bring. The interesting thing about that fear is that it can be positive or negative. If you’ve been excited about the prospect of starting a new job, starting a new relationship, or venturing to a new place, you’re experiencing the positive side. If you’re worried about something in the future that may be an unpleasant experience like having to confront someone about a problem or ending a personal or professional relationship, you’re experiencing the negative side.

You may be feeling this way in this class; excited to learn new things and start a new chapter in your life, frustrated if you struggle with a concept, happy when you understand and succeed, worried about how to juggle class with the rest of what is going on in your life. Whether your fear of the unknown is positive or negative, read this article about embracing the unknown and how it allows you to continue on your journey and see where it goes.

<https://dev.to/finnhvman/embrace-the-unknown-35an>

“The expert in anything was once a beginner”
— Helen Hayes

This week think about where you’re at in your journey.

Please answer the below prompts in your assignment submission:

So far in class, have you had any “aha” moments? What have you enjoyed the most? What has been the hardest?
What were you excited/worried about before class started?
How do you feel about what’s still to come in this class and in your journey ahead?

## Coding Challenges:
You'll notice in your mindset materials for this week that FizzBuzz is mentioned. Let's take a peek at the wonderful world of coding challenges.
-Make a Leet Code and HackerRank account and solve FizzBuzz
https://leetcode.com/problems/fizz-buzz/ 
