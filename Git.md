# Git

Git is a version-control system that was created by Linus Tovalds in '05. You can read about his experience [here](https://www.linuxfoundation.org/blog/blog/10-years-of-git-an-interview-with-git-creator-linus-torvalds). Reading about why he created it will help you understand its place in software engineering.  

You may be familiar with GitHub, the very site which you are using to read this document. Git is a Version Control System, whereas GitHub is a cloud-based hosting service that lets you manage Git repositories (such as this one). GitHub makes it easy for us to work together with other developers. You can also host your own Git server, by the way. Read about that [here](https://www.linuxfoundation.org/blog/blog/classic-sysadmin-how-to-run-your-own-git-server) - it may make for a nifty project if you have some free time.  

# How to use Git

Now the important bit - how do I use this piece of software (properly!). You may have worked with Git in the past, but let's start with the basics.  

If you learn better from an interactive game - feel free to try this [site](learngitbranching.js.org). But this won't get things working on your local machine.  

If you learn better from text and want a 'cheat sheet' (which you can contribute too as well!), scroll down. Don't forget to check out the official [docs](https://git-scm.com/book/en/v2) as well.  

# Basics

To use Git, you will first need to install it. Install Git by folowing the instructions [here](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git). If you are using Windows / Mac, go and find the corresponding section.    

## Configuring Credentials

Create an account on GitHub. The email address you use there will be the same one you set in `git config` later on. This email address associates your commits with your account on GitHub.com.  

Set a Git username by doing something like `git config --global user.name "eiestudent"`. This should correspond to your GitHub account username.  

Set up your email address via the command `git config --global user.email "eiestudent@gmail.com"`.  

## Authentication

You need to authenticate with GitHub when you connect to a GitHub repository from Git. You can do this using the GitHub CLI. Install the GitHub CLI via the instructions [here](https://github.com/cli/cli). Find the instructions corresponding to your system OS and execute the commands accordingly.  

## Initiate Git Repository

You can execute the following commands to create a new repository (taken from Git documentation):

```
cd /path/to/my/codebase
git init      
git add .     
git commit    
```

What this does is that it (1) creates a path to your directory, then (2) adds all existing files to the index, and lastly (3) records the pristine state as the first commit in the history. Go back to your GitHub account and create a new repository. There will be some instructions on how to link your GitHub repository with the directory you created earlier, which will look like this:  

```
git remote add origin https://github.com/clemenkok/test.git
git branch -M main
git push -u origin main
```

Now you have a repository you can start writing code in. Every time you want to push your code to the repository, execute the `add`, `commit` and `push` commands so others can work with it.  

## Cloning

You can also clone existing Git repositories so that you can work on a copy. Run the `git clone https://github.com/clemenkok/IAC0` for example if you want to edit the code on this repository and later possibly push it (note, you will need to have collaborator access).  

If you don't have collaborator access, you can also fork this repository and clone that repository onto your local machine. Forking means to create your own copy of a repository in a remote location, such as your own GitHub. Subsequently, you can edit the code and submit a [Pull Request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests) to have your code reviewed by the repository maintainers / contributors (think admins) and then merged.  

## READMEs and .gitignore

READMEs are the markup text you see when you first open a repository. Always create one and write about what you did so others can understand and access your code!  

`.gitignore` is used to ignore certain folders or files in your repository that you don't want to upload to GitHub. For example, you may have a huge folder containing dependency files such as `node_modules` - you wouldn't want to have everyone pull this when they can just run `npm install` using `package.json`. Or if you have a `.env` file which contains credentials which you don't want to push to a public repository.  

# Advanced Topics

If you would like to delve further into Git, definitely read up about how to use `git log`, merge, rebase, squash and so on. These will be very useful when you are working on larger scale projects.  

# A call to Open Source

I would like to encourage all students if you have time to take a look at open-source and opportunities such as [Linux Foundation Menteeships](https://mentorship.lfx.linuxfoundation.org/) and [Google Summer of Code](https://summerofcode.withgoogle.com/). If you would like to get started with FOSS software contributions, these are great avenues.  

Happy coding! Feel free to approach any of the repository maintainers if you need any help.

