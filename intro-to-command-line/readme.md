# Introductory Command Line

## Introduction

People interact with their operating system (be it Mac OS, Windows, or Linux) through the Graphical User Interface - or, in short, the GUI. GUIs use graphics, along with a keyboard and a mouse, to provide an easy-to-use interface. They provide windows, pull-down menus, buttons, scrollbars, and icons, enabling users to interact with the operating system or application.

A command line interface (CLI) enables users to type commands in a terminal or console window to interact with an operating system. Users input commands and (usually) receive responses back from the system. The command-line, while simpler in appearance, is more powerful and typically faster to use than a GUI.

Once you learn the basic structure of how to run things in a CLI and learn some basic commands, each subsequent set of commands will become easier to learn. This is unlike a GUI, which will be different for every program and each tends to have its own idiosyncrasies.

**Note**: We utilize "terminal" and "command line" interchangeably here - though they aren't exactly the same thing.

## Learning Objectives

By the end of this lesson, you should be able to:

- Differentiate between the GUI and the CLI.
- Define and build absolute paths.
- Define and build relative paths.
- Use the `open` command from the command line.
- Use the command line to navigate via absolute and relative paths.
- List files and folders in your current directory with `ls`.
- Define and use flags on the command line.
- Create new directories with the `mkdir` command.
- Create new files with the `touch` command.
- Install and use the `code` command to open VSCode.

<hr>

## Your Mac's File Structure

### Computer filesystem

In using your computer, you usually have a few places where you save files (like Desktop or Downloads), and when you install things it only requires you to click on a few prompts.

Therefore, you may not have taken the time to think about how your computer organizes itself under the hood. As a developer, you'll use aspects of your computer that most people don't know about.

Pretty much all computers are organized in a hierarchical filesystem. This means that there is a top-level directory, which contains subdirectories, which include directories.

Here's an example. Your computer should have a similar layout:

```
/
├── Applications
├── Library
├── System
├── Users
    ├── YOUR_USER_NAME*
        ├── Applications
            ├── Zoom
            │ └── Recordings
        ├── Desktop
        ├── Documents
        ├── Downloads
        | ├── ls_ex1.png
        | ├── ls_ex2.png
        | └── ls_ex3.png
        ├── Library
        ├── Movies
        ├── Music
        ├── Pictures
        ├── Public
├── tmp
├── usr
└── var

```

On a mac, `/` is the root directory and <YOUR_USERNAME> will be named after the username you chose for your Mac. The folder with your username is also referred to as your `home` directory.

File hierarchies are often described like family trees.

In the above example `Applications` is the `parent` directory of `Zoom` and `Recordings` is a `child` directory of `Zoom`. `Documents` and `Downloads` would be siblings.

## Getting Started

We recommend using `iTerm`, which you should have installed during the setup day.

You can use Terminal if you don't have it.

Use Spotlight (`command + space`) to search for `iterm` and open it.

Depending on your shell (bash is the default, but hopefully, you installed zsh, you should see something like this:

```
➜ ~
```

The `~` symbol stands for your home directory. This is the default directory you will start in whenever you open a new terminal window.

## Finding Where We Are

You are always in a directory (AKA folder) in the console. The terminal's currently selected directory is called the working directory. You can see where you are using `pwd` (which is short for "**p**rint **w**orking **d**irectory").

```bash
$ pwd
# /Users/yourUserNameHere
```

Before we get into other commands, let's break down some syntax.

## Command syntax

All terminal commands follow the same convention, which can be similar to a sentence.

```
commandName -flags parameters
```

Let's break it down.

### `commandName`

Command name is the name of a utility or program that runs. Examples are `ls`, `cd`, `pwd`, etc. You can think of these like verbs and are the minimum required to run something in terminal.

```bash
$ pwd
```

`pwd` - print the working directory:

#### Single parameter

Often you want to tell the command WHAT to act on. So parameters are the names of files or directories you want to do something with. You can think of these like parameters like nouns.

```bash
$ cd Documents
```

`cd` (**c**hange **d**irectory) into the directory `Documents`.

#### Multiple parameters

Some commands let you specify multiple parameters, which you do just by putting a space between each one.

```bash
$ touch first.txt second.txt
```

The `touch` program creates (if the files don't exist) or updates the last time a file was `touched` (will update the timestamp of `Date Modified`).

#### Default parameters

Some commands also have a default value. A value that is implied if no arguments are supplied.

For example, if we type `cd` it will automatically take us to the home directory, also known as `~`.

```bash
$ cd
```

**flags**

Many commands take flags, which modify the way a command behaves. For example you may be asked to "please read from a list." By default, you plan to read the first name. But if the person asks "please read all the details from a list." You would read all the details instead of just the first names.

```bash
$ ls -l Documents
```

`list` in **l**ong form the contents of the directory `Documents`.

There are usually several flags available:

```bash
$ ls -a Documents
```

`list` **a**ll the contents (including hidden files and directories) of the directory `Documents`.

Hidden directories start with a `.` like `.git`. Directories are hidden as a way to note to the user that they likely should not be modifying this file.

To combine multiple flags, just put them next to each other.

```bash
$ ls -alp Documents
```

This is the equivalent of writing `ls -a -l -p Documents`.

Can you figure out what `-p` does?

Try to write out (or say out loud) what `ls -lap Documents` does in your own words.

Is there a difference between `-alp` and `-lap`?

Finally, try out various combinations and see what the results are! This is the best way to improve your knowledge and abilities.

## Flags Documentation

To see the possible flags for any command, type `man` (for manual) and the command you want to look up - no googling needed! This will open an interactive window where you can scroll up and down using the arrow keys—press `q` to quit. It is helpful if you make your terminal full-screen to read the text provided. The `man` command is available for all terminal commands.

```bash
$ man ls
```

## Listing Files

Listing files is a common command. Let's look at it in more depth.

The `ls` command lists the contents of the current directory.

Output:

![ls output](./assets/ls_ex1.png)

We can also list the contents of any directory by just providing the path.

![ls output](./assets/ls_ex2.png)

And we can change how the output looks by providing a flag. The most useful one is probably `-l` because it makes the output `long`, which puts every result on its line, making it easier to read when you have a lot of files.

![ls output](./assets/ls_ex3.png)

## Navigation

You can change your directory with cd ("change directory"). If you follow this command with a name, it will move you to that directory. Without an argument, it will take you to your home directory (`~`).

```bash
$ pwd
# /Users/jabyess
$ ls
# Documents
# Downloads
# Desktop
# etc.
$ cd Downloads
$ pwd
# /Users/jabyess/Downloads
$ cd
$ pwd
# /Users/jabyess
```

### Relative vs. Absolute paths

A crucial concept in navigating directories is thinking about _how to specify where we go_.

There are two main differences here - relative and absolute.

Think of absolute paths like a street address or GPS coordinates. They are always the same value and tell you exactly where a location is, regardless of where you are. All the information you need is embedded in an absolute path.

Relative paths are different. You can think of them more like directions. To understand a relative path you need to know **where you are** AND **where you're going**. If you are at the store, what steps do you need to take to go home?

Understanding the difference between these two concepts will help you navigate your computer.

`cd` to it and then `ls` to see what's inside - you'll discover similar folder names as above (though some were excluded for brevity).

> If you type `cd /`, is that a relative or absolute path?

We can jump to any path anywhere in the system by providing its full path name. Since `/` is the root, all paths start with `/`. Each "level" of a folder is separated by a `/`.

So if we wanted to jump to `curriculum` (from anywhere!), we could type:

```bash
$ cd /Users/jabyess/curriculum
```

For anything inside of the home directory (`/Users/jabyess`), we can save some typing and do this instead:

```bash
$ cd ~/curriculum
```

Since `~` always means the home directory, you can think of it as a substitution for writing the whole thing out.

### Up and down

There are two special symbols that you should know when navigating relatively.

`.` represents the current directory

`..` represents the parent directory

So if you want to go up a directory, regardless of where you are, you can type:

```bash
$ cd ..
```

Similarly, you can navigate up multiple directories by doing the following:

```bash
$ cd ../..
$ cd ../../../
```

You can keep adding on lines, but if you put too many, you will wind up at the root.

The following two lines are equivalent - if you want to specify `.`, you can explicitly, but it's not required.

```bash
$ cd ./Documents
$ cd Documents
```

Note that `cd .Documents` is not valid. That's because it's not a proper path. You still need the `/` after `.`

Think of the `.` as "start here". Therefore the `./` can be thought of as "start here, then go down".

## Creating Files and Folders

The `touch` command creates a new file with the provided name. If the file already exists, nothing will appear to change in terminal: however the timestamp for `date last modified` would be updated. For example:

```bash
$ touch hello.js
```

This command will create a new JavaScript file with the name `hello.js` in the current directory. If the operation is successful, it won't give you any feedback. You can check by running the `ls` command - you should now see this file listed in the directory. Try to run the command again (press the up arrow):

```bash
$ touch hello.js
```

What happens?

When using `touch` you can create files in other locations. You can include a path that can be an absolute or relative path.

```bash
# assuming you are in the home directory
$ touch /Users/jabyess/curriculum/test/hello.js
$ touch ~/curriculum/test/hello.js
$ touch ./curriculum/test/hello.js
# all 3 of these are equivalent
```

The `mkdir` command creates a new folder with the provided name. For example:

```bash
$ mkdir js
```

This command will create a folder named `js` inside the current directory.

If you want to create multiple levels of folders at once, you can use the `-p` (create **p**arent directories, if missing) command.

```bash
$ mkdir -p /curriculum/tests/javascript/unit1
```

This command will create the following structure:

```
curriculum
└── tests
    └── javascript
        └── unit1
```

## Opening Files

To open a file and view its contents, type the name of the app you would like to use to open it. For example, we will use a text editor called **Visual Studio Code** to open a text file in the app:

```bash
$ code foo.js
```

To open all files in a folder, enter the following.

```bash
$ code .
```

The keyword **open** will open a file/folder with its default application in the Finder (on Mac) or the GUI-based file manager (on Linux).

```bash
# opens the current directory in the finder
$ open .
# opens the curriculum directory in the finder
$ open ./curriculum
```

The file extension `html` typically will open your default web browser.

```bash
$ touch index.html
open index.html
```

## Tips

- Use the tab key to autocomplete. For example, if the current folder has subfolders titled `games`, `photos`, and `photography`, typing `pho` and pressing the tab key will display `photo` and `photography`. If we type the letter `g` to get `photog` and press the tab key - the command will autocomplete to `photography`.

- You can also use the up and down arrow keys to cycle through all the commands you've typed.

## Resources

A lot of information was covered in this lesson. If you would like some additional visual walkthroughs, here are some good places to start.

- Tree House: [Introduction to the Mac OS X Command Line](http://blog.teamtreehouse.com/introduction-to-the-mac-os-x-command-line)
- Git Tower: [Command Line 101](https://www.git-tower.com/learn/git/ebook/en/command-line/appendix/command-line-101)
- Command Line Cheat Sheet : [Cheat Sheet](https://www.makeuseof.com/tag/mac-terminal-commands-cheat-sheet/)
- Linux command line for beginners : [Beginner tutorial](https://tutorials.ubuntu.com/tutorial/command-line-for-beginners#0)

## Keywords

- Operating System (OS)
- Graphical User Interface (GUI)
- Command Line Interface (CLI)
- Terminal
- Shell
- Folder = directory
- `pwd` - print working directory
- `cd ..` - go to the parent directory (aka up)
- `cd [folder]` - go into the folder
- `~` - represents your home folder
- `ls` - list files and subfolders in the current folder
- `touch [filename]` - create a new file
- `mkdir [directory name]` - make a new directory
- `code [filename]` - open the VSCode editor
