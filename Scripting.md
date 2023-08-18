# Scripting

## What's Scripting?

Scripting acts as a mediator between the user and the kernel (operating system). It is the "developer friendly" way of navigating folders, compiling programs, automating tasks and managing services.

## Why have I never used scripting before?

Modern OSes generally give a GUI for the user to interact with files, as it is much simpler for the everyday user, and modern IDEs often have built-in compilers or interpreters, such as Python's IDLE and IntelliJ for Java, reducing the need for shell scripting. However, when working with different languages and several files in a project, it becomes tedious to use a GUI. 

Furthermore, modern OSes generally automate system administration tasks, such as managing services, disk backups and system logs. Shell scripting allows you to customise these tasks, which becomes important in situations such as setting up web servers or managing code error logs.

## Getting started

If you're using a Windows operating system, you should consider installing [Windows Subsystem for Linux (WSL)](https://learn.microsoft.com/en-us/windows/wsl/install). This guide only describes scripting for UNIX-like systems, which use the Bourne Again Shell (Bash), not Powershell.

If you have a Linux or MacOS based system, you're good to go!

## Advice

Although it looks intimidating at first, most of shell scripting is exactly the same as using File Explorer (Windows) or Finder (Mac) - navigating around folders, making and editing folders/files, and learning the shell commands.  

A cheat sheet is available in this repository for common/useful commands. It may help at the start to have a regular File Explorer/Finder window open on the side while learning at the start to see which directory you're in and what files you can/can't access.

## Useful Resources

- Read about [UNIX-like systems](https://en.wikipedia.org/wiki/Unix-like) and [Bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell)), for general knowledge. 
- If you already have experience in shell scripting, you might want to look at build systems such as [Make](https://makefiletutorial.com/) or [CMake](https://cmake.org/cmake/help/latest/guide/tutorial/index.html) for C/C++ or [SCons](https://scons.org/doc/2.3.0/HTML/scons-user/c258.html) for C/C++/Python. Build systems are ubiquitously used at companies to manage projects which can have hundreds of files, so getting used to them early is a good idea. 