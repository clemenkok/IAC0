# Shell cheat sheet

This is a cheat sheet of common commands you'll encounter during and after uni. The goal isn't to be comprehensive, but to help you get familiar with terminal commands and scripting quickly and without too much googling. 

## Navigation/File management

### `ls` - List Subdirectories
Lists all files/folders in the current folder. Two folders seen are `.` and `..` which are an alias for the current directory and the directory one above the current directory.
|Options|What they do|
|---|---|
|-a|Shows all, even hidden, subdirectories (such as .ssh, .bashrc)|
|-d \<regex> |Lists subdirectories which match the regex|
|-l| Lists more information about each subdirectory|

Usage: `ls -al` lists all subdirectories
`ls folder/` lists visible subdirectories in folder.

### `mkdir` \<folder> - Make Directory
Creates a new folder in the current folder. 

Usage: `mkdir folder`  - creates a folder called folder. To create a folder in a different directory, just write the full path: `mkdir /path/to/directory/folder`.

### `touch` \<file> - Creates a new file
Creates a new file in the current folder.
 
Usage: `touch file.txt` - creates a new text file called file. To create a file in a different directory, just write the full path: `mkdir /path/to/directory/file.txt`.

### `cd` \<directory> - Change directory
Changes the current directory from one to another. \
Usage: `cd folder` - changes the current directory to folder. This can be seen on the command line as the directory will change from `~` to `~/folder`. \
`cd ..` - leaves current folder ie moves from `~/folder` to `~`. You can move to any arbitrary folder by using the full path: `cd /path/to/folder`. \
`cd` with no arguments - moves you to the home directory `~`. \
You can keep track of the current directory from the command line; it will show something like `aranyagupta@aranyagupta:~/iac0/IAC0` before terminal input. 

### rm - Remove
Delete any file. \
**WARNING:** This is irreversible, unless you have initialised a git repository in the current directory. 

|Options|What they do|
|---|---|
|-r|Removes folders and their contents **r**ecursively.|
|-f|**F**orces files to be deleted, even nonexistent ones.|
|-i|Prompt before removal, to be safe.|

Usage: `rm -rf folder` - forces a folder to be removed \
`rm file` - removes file if it exists

## Executing files

Most instructions can be executed on the command line by typing in the instruction and the file it needs access to.

For example, to run a python script, use `python script.py`. To compile a C file using gcc, use `gcc -c file.c`, and to execute the generated binary, use `./file`.

### `source \<shell_script>.sh` - runs a shell script
A shell script can run several instructions one after the other without writing them out separately line by line. For example, you can compile several C/C++ files and then link them together. A shell script may look as such:

**test_main.sh** \
`echo Pulling from repo...` \
`git pull` \
`echo Compiling files...` \
`gcc -c main.c` \
`gcc -c dep1.c` \
`gcc -c dep2.c` \
`echo Executing binary...` \
`gcc -o output main.o dep1.o dep2.o` \
`echo done` 

And can be run using `source test_main.sh` or even `./test_main.sh`. For more on shell scripting, use [this tutorial](https://www.shellscript.sh/).
### 

## `sudo` - Super User Do
A super user can change, edit, or remove any file and its permissions for any user of the system. This may need to be used when downloading packages or removing system-level files, such as in `/etc` or `/usr`.

**BE CAREFUL** when using `sudo`; on local installations it's not a big deal, but when working on large projects or networking systems, it can cause irreparable damage if the wrong files are changed. 

Usage is `sudo <command>` ie it is used to run a command as a super user. Some commands require `sudo` to work correctly, and are listed below:

### `sudo apt-get install \<package_name>` - installs package
Installs a new package; for example, if you have not yet installed Python, you can use `sudo apt-get install python`.

### `sudo apt-get update/upgrade` - updates OS
Updates the Linux OS on WSL.

### `sudo apt-get remove \<package_name>` - removes package
Removes a previously installed package. 

### `sudo update-alternatives --config \<package_name>` - manage package versions
If you've installed different versions of a package, such as gcc or Python, you can choose which version to use using this command. 