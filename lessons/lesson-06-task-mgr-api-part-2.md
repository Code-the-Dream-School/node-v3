This week begins at 1:29 of **[this video](https://www.youtube.com/watch?v=rltfdjcXjmk&t=5280s)**, and continues until the end of the task manager project, at 3:07:18 of the video.

In this lesson you will continue to develop the Task Manager API, testing with Postman as you go. You will add:

* Input Validation
* Error Handling
* Additional CRUD Operations



Create a file in the starter directory called `QuizAnswers2.txt`. Put answers to the following questions in it.

1. In this lesson, you created a middleware function called `asyncWrapper`. Why?
2. Suppose that you want to make sure that both a status code and an error message are sent back to the user when they request the URL for a task that does not exist. Assume that you’ve created a `CustomAPIError` class and an error handler that references that class. Complete the code:  
```javascript  
const getTask = asyncWrapper(async (req, res, next) => {  
  const { id: taskID } = req.params;  
  const task = await Task.findOne({ _id: taskID });  
  if (!task) {  
    // your code here  
  }  
  res.status(200).json({ task });  
});  
```

As you will see in the lessons that follow, you do not have to always create the `asyncWrapper` middleware, because you can instead use an NPM package called `express-async-errors` that provides the same capability.