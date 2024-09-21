In this lesson, you parse the query parameters passed with the REST request, appending the search filters that result to your find operation. As in the previous lesson, you communicate with a MongoDB database. The lesson starts at 3:07:00 of **[this video](https://www.youtube.com/watch?v=rltfdjcXjmk&t=11220)**, and continues to 5:05:34.

### Concept: Thenables

One part of this assignment is a little confusing. You will see code like this:

```javascript
let result = Product.find(queryObject);
...
result = result.sort(sortList);
...
result = result.select(fieldsList);
...
const products = await result;
```

### How Can This Work? Isn’t `Product.find` Asynchronous?

`Product.find` is indeed asynchronous, but it doesn’t return a standard `Promise`. Instead, it returns a special type of object called a "thenable." A thenable acts like a `Promise` but has additional features.

- **What is a Thenable?**  
  A thenable is an object that has methods like `.then`, allowing you to chain additional actions and refine your query.

- **How Does It Work?**  
  The `Product.find` call doesn’t immediately send a query to the MongoDB database. Instead, it returns a thenable that waits for further instructions.

- **When is the Query Sent?**  
  The actual database query is sent when you use `await` (or `.then`) on the thenable. At that point, the fully defined query is executed, the `Promise` is resolved, and the results are returned.

### Concept: Regular Expressions

A regular expression can be used to identify strings that match a pattern. Like verification for email and phone number strings for example. Regular expressions can also be used to create modified strings by substituting character patterns. There are several tutorials on regular expressions on the web. Here is a selection of them:

* [Regex Tutorial](https://regexlearn.com/)
* [Game to help learn regex](http://play.inginf.units.it/#/)
* [Interactive regex exercises](https://regexone.com/)

In this course, we will not teach the use of regular expressions, but you should absolutely be aware of their purpose. They are often used in most fullstack positions. Most developers don't have the regex syntax memorized, but they have a good grasp of the concept and ability to navigate the documentation. To complete your homework, you can just copy the regular expressions used by the instructor from their location in the final directory.


### Debugging - part 1

By this stage in the course, you’ve probably run into a bug or two that has taken some time—maybe much longer than your anticipated!—to figure out, or perhaps one that required showing your code to a mentor to get unstuck. If you did work with a mentor to figure out that bug, you likely observed them put a few debugging practices into action.

Debugging is the process of working through technical challenges when something is broken or not working as expected, and it is a HUGE part of most developer’s day-to-day. Ideally, we would write beautiful, perfect code the first time around and introduce no bugs… but we’re human after all, so that’s not the reality.

Given, we humans do (often) introduce bugs into our programs, it’s important to invest time into strengthening your debugging processes. Read this article about some common and helpful debugging practices. By coming up with hypotheses, observing and investigating how things are working, and piecing together the clues to figure out what’s going on is the best way to figure out how to fix something!

Please answer the below prompts in your assignment submission:

When asked to think about debugging, what are the first 3 adjectives that jump to mind?
Are there any debugging practices that you’ve already tried and found helpful?
Any you haven’t tried yet, but want to practice in this upcoming week?


