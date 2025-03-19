layout: page
title: "Scripts for Introduction to the Command Line; 19 March 2025 @ O'Leary 202"
permalink: https://jananiharan.github.io/teaching.io/DCDS-cmdline

---

Adapted from the shell-novice lesson plan from [Software Carpentries](https://github.com/swcarpentry/shell-novice/tree/main)

### Meet The Shell

Let's get started.

When the shell is first opened, you are presented with a **prompt**,
indicating that the shell is waiting for input.

```bash
$
```

The shell typically uses `$ ` as the prompt, but may use a different symbol.
In the examples for this lesson, we'll show the prompt as `$ `.
Most importantly, *do not type the prompt* when typing commands.
Only type the command that follows the prompt.
This rule applies both in these lessons and in lessons from other sources.
Also note that after you type a command, you have to press the <kbd>Enter</kbd> key to execute it.

An example prompt from my screen:

```bash
Jananis-Air:~ jananihariharan$ 
```

## ls : List contents of a directory

```bash
$ ls
```

``` Sample output
Desktop     Downloads   Movies      Pictures
Documents   Library     Music       Public
```
::::::::::::::::::::::::::::::::::::::::::::::::::

## Nelle's Pipeline: A Typical Problem

Nelle Nemo, a marine biologist, has just returned from a six-month survey of the
[North Pacific Gyre](https://en.wikipedia.org/wiki/North_Pacific_Gyre),
where she has been sampling gelatinous marine life in the
[Great Pacific Garbage Patch](https://en.wikipedia.org/wiki/Great_Pacific_Garbage_Patch).

She has 1520 samples that she's run through an assay machine to measure the relative abundance of 300 proteins.

She needs to run these 1520 files through an imaginary program called `goostats.sh`.
In addition to this huge task, she has to write up results by the end of the month, 
so her paper can appear in a special issue of *Aquatic Goo Letters*.

If Nelle chooses to run `goostats.sh` by hand using a GUI, she'll have to select and open a file 1520 times.
If `goostats.sh` takes 30 seconds to run each file, the whole process will take more than 12 hours
of Nelle's attention.
With the shell, Nelle can instead assign her computer this mundane task while she focuses
her attention on writing her paper.

As a bonus,
once she has put a processing pipeline together,
she will be able to use it again whenever she collects more data.

:::::::::::::::::::::::::::::::::::::::: keypoints

- A shell is a program whose primary purpose is to read commands and run other programs.
- This lesson uses Bash, the default shell in many implementations of Unix.
- Programs can be run in Bash by entering commands at the command-line prompt.
- The shell's main advantages are its support for automating repetitive tasks, and its capacity to access networked machines.
- A significant challenge when using the shell can be knowing what commands need to be run and how to run them.

::::::::::::::::::::::::::::::::::::::::::::::::::

## Where am I? : pwd

```Sample output
/Users/jananihariharan

This is my **home directory**

## Slashes

Notice that there are two meanings for the `/` character.
When it appears at the front of a file or directory name,
it refers to the root directory. When it appears *inside* a path,
it's just a separator.

## Playing around with ls

ls -l
ls -la
ls -r
ls -F
ls -S
ls -F Desktop

## Getting help

```bash
  $ ls --help
  ```

```bash
  $ man ls
  ```
## Challenge #1
List the contents of the folder (directory) you just downloaded, "shell-lesson-data", from your home directory.

## Changing directories: cd

```bash
$ cd Desktop
$ cd shell-lesson-data
$ cd exercise-data
```

What happens if you run these commands now?

```bash
$ pwd
```

```bash
$ ls -F
```

We now know how to go down the directory tree (i.e. how to go into a subdirectory),
but how do we go up (i.e. how do we leave a directory and go into its parent directory)?
We might try the following:

```bash
$ cd shell-lesson-data
```

```error
-bash: cd: shell-lesson-data: No such file or directory
```

But we get an error! Why is this?

Let's try returning to the `exercise-data` directory from before. Last time, we used
three commands, but we can actually string together the list of directories
to move to `exercise-data` in one step:

```bash
$ cd Desktop/shell-lesson-data/exercise-data
```

Check that we've moved to the right place by running `pwd` and `ls -F`.

## File Paths: Make or Break!

```bash
$ pwd
```

```output
/Users/nelle/Desktop/shell-lesson-data/exercise-data
```

```bash
$ cd /Users/nelle/Desktop/shell-lesson-data

This is called an ##absolute path.

Paths can be relative too!

The shell interprets a tilde (`~`) character at the start of a path to
mean "the current user's home directory".

`cd` will translate `-` into *the previous directory I was in*, 
which is faster than having to remember, then type, the full path. 
This is a *very* efficient way of moving
*back and forth between two directories* -- i.e. if you execute `cd -` twice,
you end up back in the starting directory.

cd .. : brings you UP
cd - : brings you BACK

## Absolute vs Relative Paths

Starting from `/Users/nelle/data`,
which of the following commands could Nelle use to navigate to her home directory,
which is `/Users/nelle`?

1. `cd .`
2. `cd /`
3. `cd /home/nelle`
4. `cd ../..`
5. `cd ~`
6. `cd home`
7. `cd ~/data/..`
8. `cd`
9. `cd ..`

## Essential Shell terminology

Consider the command below as a general example of a command,
which we will dissect into its component parts:

```bash
$ ls -F /
```

`ls` is the **command**, with an **option** `-F` and an
**argument** `/`.

```bash
$ cd ~/Desktop/shell-lesson-data
$ ls -s exercise-data
```

```output
total 28
 4 animal-counts   4 creatures  12 numbers.txt   4 alkanes   4 writing
```

Note that the sizes returned by `ls -s` are in *blocks*.
As these are defined differently for different operating systems,
you may not obtain the same figures as in the example.

```bash
$ ls -S exercise-data
```

```output
animal-counts  creatures  alkanes  writing  numbers.txt
```

### Nelle's Pipeline: Organizing Files

Knowing this much about files and directories,
Nelle is ready to organize the files from the protein assay machine.

She creates a directory called `north-pacific-gyre`
(to remind herself where the data came from),
which will contain the data files from the machine
and her data processing scripts.

Each of her physical samples is labelled according to her lab's convention
with a unique ten-character ID,
such as 'NENE01729A'.
This ID is what she used in her collection log
to record the location, time, depth, and other characteristics of the sample.
Since the output of the assay machine is plain text,
she will call her files `NENE01729A.txt`, `NENE01812A.txt`, and so on.
All 1520 files will go into the same directory.

Now in her current directory `shell-lesson-data`,
Nelle can see what files she has using the command:

```bash
$ ls north-pacific-gyre/
```

This command is a lot to type,
but she can let the shell do most of the work through what is called **tab completion**.

:::::::::::::::::::::::::::::::::::::::: keypoints

- Information is stored in files, which are stored in directories (folders).
- Directories can also store other directories, which then form a directory tree.
- `pwd` prints the user's current working directory.
- `ls [path]` prints a listing of a specific file or directory; `ls` on its own lists the current working directory.
- `cd [path]` changes the current working directory.
- Most commands take options that begin with a single `-`.
- Directory names in a path are separated with `/` on Unix, but `\` on Windows.
- `/` on its own is the root directory of the whole file system.
- An absolute path specifies a location from the root of the file system.
- A relative path specifies a location starting from the current location.
- `.` on its own means 'the current directory'; `..` means 'the directory above the current one'.

::::::::::::::::::::::::::::::::::::::::::::::::::

