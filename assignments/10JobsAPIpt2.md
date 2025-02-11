Complete and test all CRUD operations for your model (or the `Jobs` model). Be sure that each operation uses the ID of the user, so that you have good access control.

**Test each step with Postman, creating a Postman collection of tests just like the instructor is doing.**

### Deploying to Render.com

You deploy your application once you have your assignment completed and working, and once you have pushed your `week10` branch to Github.

To deploy to Render.com, follow these steps:

1. Specify the version of Node that Render is to use. One way is to create a `.node-version` file in the root of your project repository, specifying the same version of node as you are running on your machine. On my machine, when I type `node -v`, I get back v16.19.0 . So I would create a `.node-version` file with the single line: `16.19.0`
2. Create a [Render.com](https://render.com/) account. You do not need to install anything on your workstation for Render deployment. You do not need to enter any credit card information.
3. From your Render.com dashboard, click on the New button in the upper right. Select Web Service. You will then be prompted to connect a repository. Scroll down to the entry field that says “public git repository”, and enter the URL of your 06-jobs-api repository. Then press continue.
4. The next page prompts you for the name of the service. This becomes the first part of the URL for your application. You need to give it a unique name that no one else is using, maybe something like `jobs-api-<your name>`.
5. Scroll down to the entry field for branch. Put in `week10`.
6. Scroll down until you see the “advanced” button. Click on that. You then click on Add Environment Variable. You need to add an environment variable for each of the values in your .env file: the Mongo URI, the JWT key, and so on.
7. Scroll to the bottom and click on Create Web Service. Render.com then builds the application for deployment. The process takes a while. Once the process completes, you see a link in the upper right for your new web service. The URL will be something like `https://jobs-api-<your name>.onrender.com`.
8. Copy that URL and put it into your Postman tests for the assignment. Then test with Postman. Your application is live!

<video controls="" title="Deploying backend on Render.com" src="./images/lesson10-deploying-on-render.mp4"></video>

### Swagger / OpenAPI documentation

The section of the video from 9:34:30 to the end discusses setting up a Swagger configuration. When you have an API, you need to document it so that implementers of applications that call the API (like the frontend) know what the available endpoints and operations are. Swagger is the best way to do that. It also creates a graphical user interface so that one can call the APIs directly from the UI. You should watch this section so that you understand how a Swagger configuration may be created and what functions it provides. However, this section of the video gets a bit complicated, so you are not required to implement Swagger for your application, but it’s a great idea to watch this section and familiarize yourself with the concept of Swagger. If possible, try to implement it as a bonus task this week.


## Hungry for more 
Depending on your background with React this will either be refresh or review! Let's jump into React (And keep this link on deck!)
<https://react.dev/learn/thinking-in-react>

If you're more familiar with React and you feel solid, jump into Hooks: 
<https://react.dev/reference/react/hooks>

### RMOR Comprehension Check:
So you don't redirect off this lesson page, right click the link and select "Open Link in New Tab" to [take the RMOR Comprehension Check as review of what you learned during the ninth course lesson on Jobs API part 1](https://airtable.com/appoSRJMlXH9KvE6w/shrN7Aa29Ctcgh2mj?prefill_Lesson=Node%20v3:%20Lesson%209%20-%20Jobs%20API%20-%20part%201)
