# Essentials - the shell and Git

## What's a shell?

A shell is a terminal-based environment that provides a way to communicate with the computer in a text-based format. In Windows, the default shell is CMD. On MacOS, it's zsh, and on Linux, it's typically bash. Every operating system has a different shell, so the commands you use to navigate your system using your shell will be depend on what shell you're using.

For MacOS and Linux, there are tons of common commands. Windows is quite different. If you're using Windows, you have some choices. You can use (1) the built-in CMD shell, which uses some syntax and commands that are very different from those used in MacOS and Linux, and so you'll have to learn them, (2) the Windows Subsystem for Linux (WSL) to host a mini computer running on your machine that runs Linux, or (3) use something like Cygwin or Git Bash. I personally prefer (3) and then (2) and then (1) last, but it's entirely up to you.

### Some basic commands

Here are some useful shell commands for zsh/bash users (unfortunately, I don't know any CMD). To try using them, open your terminal and type them in.

| Command      | What it does | Example |
| ----------- | ----------- | ----- |
| `ls <dir>`      | Lists all folders and files in `dir`. Without `dir`, it lists all folders and files in the current working directory. | `ls`, `ls ~/Desktop` |
| `cd <dir>`      | Changes working directory to `dir`      | `cd ~/Desktop` |
| `pwd`   | Get current working directory        | `pwd`|
| `cp <file> <destination>`   | Copy `file` to new location `<destination>` | `cp secrets.txt Desktop/secrets.txt`|
| `mv <file> <destination>`   | rename `file` to new location `<destination>` | `mv secrets.txt not_secrets.txt`|

A **directory** is a folder in a file system. Each of these commands can accept multiple **flags**, which are options provided to a command. For example, to get a list of sizes and permissions of all files and folders within a directory, use `ls -la <dir>`.

Look [here](https://ss64.com/bash/cp.html) for a list of bash commands and their flags.

## What's a program?

A program is, simply put, a series of instructions a computer follows to accomplish a task. Those instructions are the code, and there are many steps between the computer reading the code and executing it. These tutorials will not cover these in-between steps; we will focus purely on the code.

Code can run in a lot of contexts, and it largely depends on what the program is trying to accomplish. For instance, a website like Wordle must run on a web browser like Chrome or Safari, or a machine learning model can run anywhere that its programming language and dependencies are supported (e.g. server, desktop app, anywhere really with enough resources). Where the code runs determines a lot about how you write your program. This includes what language you use and what external factors need to be considered (e.g. a desktop app has less of a need to worry about resource management than a program running on a toaster).

## How is code written?

Typically, we want to write code with other people, which begs the question: how do we collaborate on a codebase? The bad way is for everyone to write their version of the program and then share code via email or some cloud service like Google Drive. This is bad because attaching code, downloading code, and seeing where other people made changes in the code becomes very tedious. So, most people use Git.

### Git

Git is a [version control system](https://en.wikipedia.org/wiki/Version_control). It gives structure to how people collaborate on code together, and it's invaluable to a productive team. Instead of everyone doing their own thing and tediously exchanging code bits with each other, Git gives a centralized system that saves different versions of the program and automates the process of sharing, uploading, and reconciling code.

#### Branches

The basic idea of Git is this: there are things called **branches** which are essentially just different versions of a program's codebase. The **main branch** is where a finished product of the program is saved. All other branches are copies of the main branch with various changes. For instance, it's common to have **feature branches** which are branches dedicated to the development of a program feature. Once a developer decides the branch's code should be included in the main branch, they issue a **pull request**, or a request merge their branch into the main branch. This merge usually requires the approval of another programmer or set of programmers.

For example, maybe I'm writing a todo list app, and Alice wants to add a search bar to our app. She would make a new branch apart from main on her own feature branch. Once the search bar is finished, she makes a pull request. Someone else approves this request, and the app now has a search bar.

Note other people can work on Alice's branch as well. However, they would not see any of the changes Alice makes until she **commits** and **pushes** them to the cloud. Similarly, they could only get Alice's changes on her branch by **pulling**.

#### Staging and commits

A commit is a checkpoint in a branch's edit history. It's like looking at a previous save version of your program. If you make a mistake/want to look at a previous commit, then you can got to a previous commit to restore the program at that commit. Note that commits do not put your code changes in your respository in the cloud. That is, any code I commit locally is not seen by anyone else on my branch. For them to see the changes I've made, they must pull.

To make a commit, you must first **stage** the changes you've made to the branch. This just tells git which files you want to commit before you make the decision to make the commit. All staged files are put in the **staging area**.

#### Pushing/Pulling

Pulling is exactly what it sounds like: it takes the version of the codebase in the cloud and puts in on the branch you're checked into on your machine. Pushing is also simple; it takes one of your local commits and submits it to the cloud.

### A typical workflow

A typical Git workflow looks like the following. Text that looks like `this` should be put into your terminal:

1. Clone repository (`git clone <repository url>`, in Github, click on the green Code button on a repository and copy the link it gives you)
2. Checkout to a certain branch (`git checkout <branch>`, try to not work directly on the main branch for most projects since that's for final, production ready code)
3. Pull any recent changes to the branch (`git pull <branch>`)
4. Make code edits
5. Add your changes to the staging area (`git add <files>`)
6. Commit your changes (`git commit -m "comment describing what you did"`)
7. Push your changes (`git push -u origin <branch name>`)

There are other ways to work with git, and there are many other git commands to learn. These are the bare necessities.

Note that there is a difference between Git and Github: Git is the program that does all of these magical version control tasks, and Github is just a website built by Microsoft to facilitate the Git workflow. If you wanted to, you could totally make your own git server and set of git tools. If you don't like Github, you can also use services like [Gitlab](https://about.gitlab.com/) or [BitBucket](https://bitbucket.org/product) as well.

#### Installation

Follow [this](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) guide to install Git for your operating system.

## Exercises

1. Clone this repository somewhere to your computer.
2. Go to the next part of the tutorial [here](../how-to-programming/tutorial.md).
