Continue to work in the `node-express-course` repository. Create a new branch, `week7`. **This should be created when the `week6` branch is active, so that your new work adds to the previous work.** You will work in the directory `04-store-api/starter`. Once you have changed to that directory, be sure to run `npm install` to install the required Node modules. As in previous lessons, you will duplicate the work of the instructor, testing as you go with Postman.

**This is a difficult lesson, so take your time with it**, stopping the video as needed so that you understand what is being done. Also, if you get stuck, the instructor’s solution is in the `04-store-api/final` directory. The idea is that one can search by any or all of these attributes: `featured`, `name`, `price`, `rating`, and `company`. For the numeric fields (`price` and `rating`), one can also specify that you are comparing the number given to see if its “greater than”, “less than”, or “equal to” that value. One can also specify a sort order (ascending or descending). Also, one can specify a `skip` and a `limit`, to facilitate pagination through the result. Be sure that you test each step with Postman. Almost all the work will be done in the `controllers/product.js` file. That file has two methods, `getAllProducts` and `getAllProductsStatic`. The `getAllProductsStatic` method is there for you to experiment with and won’t be directly reviewed.

## Mindset Assignment
Asking for Help - part 2

At the start of class we discussed how to effectively ask for help (the Lesson 8 JWT Basics week). Feel free to review that topic and recall your answers from that mindset assignment. We’ll be talking about asking for help again, but this time let’s focus on the _when _since we’ve already covered the how.
At the beginning of this course (or at the beginning of your first ever course) you may have wanted to ask for help as soon as you hit a problem and before you even tried to debug or problem solve on your own. You don’t have to do that anymore since you have those problem solving and debugging processes we’ve been talking about. But the opposite can happen too; sometimes you get so determined to solve the problem on your own that you spend hours longer than you needed to trying to fix something, when asking for help could have saved you time and frustration.
Read this article about knowing when to ask for help at work, then answer the following questions:

Please answer the below prompts in your assignment submission:

Have you implemented/used any new strategies since the previous post on how to ask for help? If so what were they and how did they turn out for you?
After reading the article what changes (if any) will you make to your strategy?
What are some ways you can determine which “circle” (inner circle of things you know, middle circle of things you can figure out on your own, outer circle of things you don’t know and can’t learn by yourself) your blocker/bug/issue falls into?
