---     
layout: "../../layouts/genericMarkdownFile.astro"     
title: "Getting Started with Node Development"     
description: "imported from WordPress,Getting Started with Node Development"     
---

# Getting Started with Node Development

Welcome to Code the Dream’s Node/Express class! You will be learning Node, an implementation of the JavaScript engine that runs standalone or as a web server. This page describes how to begin.

You can develop Node applications on MacOS, Linux, or Windows. If you are developing on Windows, there is no need to do development in a virtual machine, as Node development works fine in Windows native environments.

You will need the git program. This is typically already present on MacOS and Linux. You can run

```
git --version
```

to see if it is installed. On Windows, you should install Git for Windows, if you haven’t already. It is available **[here.](https://gitforwindows.org/)** 

You will also need an editor. For JavaScript development the VSCode editor is strongly recommended.

Finally, you will need to install Node and the Node Package Manager npm. That package is available **[here](https://nodejs.org/en/download/)**. You should install the latest LTS version.

The other package you need is called Postman. In this class, you create REST APIs. You may have no front end for those APIs, so you need to test them with Postman. The Postman package is available **[here](https://www.postman.com/downloads/)**.

MacOS and Linux users can skip the next section — but please continue with the Your Assignments section below.

## Windows Setup

A few additional steps are recommended when setting up a Windows machine for Node development. When you install Git for Windows, you get a terminal shell program called Git Bash. This is the terminal environment you should use for Node development. Do not use cmd.exe or PowerShell, as these terminal environments work differently. With Git Bash, your terminal will work like the LInux or MacOS terminals, so you can enter the same commands as the students with Linux or MacOS. It helps to have some basic understanding of these shell commands: cd, ls, mkdir, touch, pwd. If you are not familiar with these, there is a tutorial **[here](https://ubuntu.com/tutorials/command-line-for-beginners#1-overview)**.

You should always start a Git Bash session to issue git, node, or npm commands. You should also configure git to handle line endings in the Linux way, via these commands:

```
git config --global core.eol lf
git config --global core.autocrlf input
```

You should also configure npm to integrate with Git Bash. This is done with the following command:

```
npm config set script-shell "C:\\Program Files\\git\\bin\\bash.exe"
```

You should also configure VSCode to handle line ends as Linux does, and to use Git Bash as the terminal shell. Start VSCode from your Git Bash session by typing

```
code .
```

You can then bring up the settings for VSCode by typing Ctrl, (the ctrl key plus the comma). The settings has a Search settings entry field. Type line end in that entry field. You will then be able to set the Eol to /n which is what you want. Then do a Search settings for: terminal integrated default profile windows. This brings up a dropdown, from which you should choose Git Bash.

That completes Windows specific setup.


## AI - tool or weapon?

This topic is a popular one these days... Artificial Intelligence. Countless news reports have praised the capabilities of this new tech tool, and also warned against the dangers. While intelligence is in the name of the tool, it’s important we identify how AI is different from human intelligence:

- AI doesn't have volition or a sense of self
- AI doesn't have long term memory between sessions, each session is independent
- AI is essentially providing a generalized consensus of its training data
- Unless combined with a web search like Bing Chat, AI’s knowledge can be out of date
- AI sometimes make mistakes providing incorrect or even absurd answers (but then so do humans! so this is actually a similarity or rather a reflection of humanity within a tool humans created)
- Like anything else on the internet, AI answers need to be verified

Take a few minutes now and watch at least these 15 minutes (from timestamp 5:33 to about 18:00) of this podcast interview

 with the creator of Khan Academy (the tool you used for your prework). The interviewer, Adam Grant, asks Sal Khan about his thoughts on using AI in learning.

Have you ever used any AI tools (ex. chatGPT, Grammerly, Dall-E, etc.)? If yes, what did you use it for? If no, did you choose not to use AI, or you just haven't explored it/aren't aware of how to use it?
What did you think about your interaction with AI?
What are ways you think AI can help you as you learn content throughout this class?
What are ways that AI can cause frustration or negatively impact your learning?

If you're interested in leveraging AI throughout class, download for free these articles on how to use AI for good in your learning:
Help understanding complex topics
Help to create study plans and beat procrastination

## Auditory Processing with Video Lessons
It is vital to find the best speed and groove for your learning when it comes to the video lessons. Here's a cool article on processing language. https://blog.cognifit.com/neurons-process-language-at-multiple-speeds/ 

This is a reminder that any video on Youtube can have increased or decreased speed (bottom right settings) and the languages for captions can be toggled to most languages (captions aren't always completely accurate, but it's translated closely overall).


## Regular Bookmarking
It's important to keep your physical workspace clutter free, and also your virtual workspace! While working try to keep your browser tabs under 5 and to keep all related materials bookmarked and ordered on deck based on what you will need each week.
 
## 

## Your Assignments

For each of the assignments, you will have a starter Git repository. To do the assignments, you will have to have a github account, if you don’t have one already. You open the link to the starter repository, and click on the fork button in the upper right to make a fork of that repository in your own github account. Then, you clone your fork of the repository to your development workstation. This is done with the git clone command, passing the URL of your repository. It is important that you clone from your fork, and not from the starter repository.

After you have cloned, you cd to the directory created when you cloned. You then create a new git branch for your work. For example, for the week 1 assignment, you would enter the command

```
git checkout -b week1
```

which will create the week1 branch. You should do this before doing any of the work for the assignment. You then cd to the directory where you will be working, and type code . to bring up VSCode for that directory. For the early assignments, you will be following along with an instructor in a video, repeating the same coding he is doing.

When you have finished the week’s assignment, you push it to github as follows:

```
git status
git add -A
git commit -m "Week 1 assignment"
git push origin week1
```

You then go to your github and open your fork of the repository. You create a pull request. The target of the pull request must be the main branch of your fork. Then you use the assignment submission form. A link to this form is in the assignment page. You include a link to your pull request in the assignment submission form.

For the first few weeks, you will use the same repository for several weeks of work. Each week’s work must be in a different git branch, and you create the week2 branch from the week1 branch so that each week builds on the work from the weeks before.

## Good Luck With the Class, and Happy Coding!