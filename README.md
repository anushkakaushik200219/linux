

# LINUX

This tutorial will help you get started with Linux.



```bash
 Audience of this tutorial are beginners, so don't expect advanced concepts.
```


## Pre-requisite:
 
 ```bash
  AWS Account or any Linux Distribution.
```


# Table of Content:
-    Introduction
    --   Components of Linux
    --   Linux Distribution/Flavours
    --   Levels and Layers of Abstraction
    --   The Kernal (Process, Memory, Device Drivers and their Management)
 
-    Basic Commands and Directory Hierarchy
    --   Bourne Shell/Shell
    --   Basic and Intermediate Commands
    --   Files modes and permission
    --   Navigating Linux Directory
    --   Archiving, Compressing, and Dot file
 
 
-    Devices, Disk, and Filesystem
    --   Device Name Summary
    --   Filesystem
    --   Partitioning Disk and Swap space
 
 
-    How the Linux Kernal Boot and User Space Start
    --   Kernal Parameters
    --   Boot Loaders
    --   GRUB and UEFI
    --   INIT
    --   System V Runlevels
-    Processes and Resource Utilization
    --   System Call
    --   Tracing Program Execution
    --   Resource Monitoring
    --   I/O Monitoring
 
-    Networking and Its Configuration
    --   Network Basic
    --   Resolving Hostnames
    --   Firewalls
    --   SSH
    --   Diagnostic Tools (Isof, tcpdump, netcat, Port scanning )
    
-    Shell Scripting
    --   Basics
    --   Shell Script Utilities

# INTRODUCTION
- # Components of Linux
    #### If you’ve never worked with Linux before, you may be confused about why so many different versions are available.
    #### First, four main parts make up a Linux system:
    -   The Linux kernel
    -   The GNU utilities
    -   A graphical desktop environment
    -   Application software
    #### Each of these parts has a specific job in the Linux system.

## Looking into the Linux Kernel
The core of the Linux system is the `kernel`. The kernel controls all the hardware and
software on the computer system, allocating hardware when necessary and executing
software when required.

The `uname` command includes additional options that you can use to get more information about your kernel. Simply add an option after the command:


To check kernel version:
    
    [me@linuxbox ~]$ uname -r

or 

    [me@linuxbox ~]$ uname --help  

For displaying all parameters like:

| Parameter | Description          |
| :-------  | :------------------------- |
| `a`       |  Display all information   |
| `o`       |  Display the operating system (usually GNU/Linux)   |
| `r`       |  Display kernel release   |
| `v`       |  Display kernel version   |


- # Linux Distribution/Flavours
#### A complete Linux system package is called a distribution. Many different Linux distributions are available to meet just about any computing requirement you could have.
#### The different Linux distributions are often divided into three categories:
- Full core Linux distributions
- Specialized distributions
- LiveCD test distributions

## Core Linux Distributions
A core Linux distribution contains a kernel, one or more graphical desktop environments,
and just about every Linux application that is available, precompiled for the kernel. It
provides one-stop shopping for a complete Linux installation. Table shows some of the
more popular core Linux distributions.

| Distribution | Description |
| :-------  | :------------------------- |
|Slackware |One of the original Linux distribution sets, popular with Linux geeks|
|Red Hat |A commercial business distribution used mainly for Internet servers|
|Fedora |A spin-off from Red Hat but designed for home use|
|Gentoo |A distribution designed for advanced Linux users, containing only Linux source code|
|openSUSE |Different distributions for business and home use|
|Debian |Popular with Linux experts and commercial Linux products|

## Specialized Linux Distributions
A new subgroup of Linux distributions has started to appear. These are typically based on one of the main distributions but contain only a subset of applications that would make sense for a specific area of use.
Table shows some of the specialized Linux distributions available and what they
specialize in.

| Distribution | Description |
| :-------  | :------------------------- |
|CentOS |A free distribution built from the Red Hat Enterprise Linux source code|
|Ubuntu |A free distribution for school and home use|
|PCLinuxOS| A free distribution for home and office use|
|Mint| A free distribution for home entertainment use|
|dyne:bolic| A free distribution designed for audio and MIDI applications|
|Puppy Linux| A free small distribution that runs well on older PCs|

## The Linux LiveCD
A relatively new phenomenon in the Linux world is the bootable Linux CD distribution.
This lets you see what a Linux system is like without actually installing it. Most modern
PCs can boot from a CD instead of the standard hard drive. To take advantage of this,
some Linux distributions create a bootable CD that contains a sample Linux system
(called a Linux LiveCD). Because of the limitations of the single CD size, the sample can’t
contain a complete Linux system, but you’d be surprised at all the software they can cram
in there. The result is that you can boot your PC from the CD and run a Linux distribution
without having to install anything on your hard drive!
Table shows some popular Linux LiveCDs that are available.

| Distribution | Description |
| :-------  | :------------------------- |
|Knoppix |A German Linux, the first Linux LiveCD developed|
|PCLinuxOS |Full-blown Linux distribution on a LiveCD|
|Ubuntu| A worldwide Linux project, designed for many languages|
|Slax |A live Linux CD based on Slackware Linux|
|Puppy Linux |A full-featured Linux designed for older PCs|

- ## Levels and Layers of Abstraction in a Linux System

Using abstraction to split computing systems into components makes things
easier to understand, but it doesn’t work without organization. We arrange
components into layers or levels. A layer or level is a classification (or grouping)
of a component according to where that component sits between the
user and the hardware. Web browsers, games, and such sit at the top layer;
at the bottom layer we have the memory in the computer hardware—the 0s
and 1s. The operating system occupies most of the layers in between.

A Linux system has three main levels:

The `hardware` is at the base.
Hardware includes the memory as well as one or more central processing
units (CPUs) to perform computation and to read from and write to
memory. Devices such as disks and network interfaces are also part of the
hardware.
The next level up is the `kernel`, which is the core of the operating system.
The kernel is software residing in memory that tells the CPU what to
do. The kernel manages the hardware and acts primarily as an interface
between the hardware and any running program.

`Processes`—the running programs that the kernel manages—collectively
make up the system’s upper level, called user space. (A more specific term for
process is user process, regardless of whether a user directly interacts with the
process.For example, all web servers run as user processes.)


| | | 
| :-------  | :------------------------- |
|User Processes| `Graphical User Interface` `Servers` `Shell`|
|Linux Kernel| `System Calls` `Process Management` `Memory Management` `Device Drivers`|
|Hardware| `Processor (CPU)` `Main Memory (RAM)` `Disks` `Network Ports`|


- # The kernel is in charge of managing tasks in four general system areas:
    - ## Processes 
        The kernel is responsible for determining which processes are allowed to use the CPU.
    - ## Memory 
        The kernel needs to keep track of all memory—what is currently allocated to a particular process, what might be shared between processes, and what is free.
    - ## Device drivers
        The kernel acts as an interface between hardware (such as a disk) and processes. It’s usually the kernel’s job to operate the hardware.
    - ## System calls and support 
        Processes normally use system calls to communicate with the kernel.

        Two system calls, `fork()` and `exec()`, are important to understanding how processes start up:

        `fork()` : When a process calls fork(), the kernel creates a nearly identical copy of the process.

        `exec()` : When a process calls exec(program), the kernel starts program, replacing the current process.


# Basic Commands and Directory Hierarchy
-   ## Bourne Shell/Shell
The shell is one of the most important parts of a Unix system. A shell is a
program that runs commands, like the ones that users enter. The shell also
serves as a small programming environment. Unix programmers often
break common tasks into little components and use the shell to manage
tasks and piece things together.

There are many different Unix shells, but all derive several of their 
features from the Bourne shell (/bin/sh), a standard shell developed at Bell 
Labs for early versions of Unix. Every Unix system needs the Bourne shell in 
order to function correctly, as you will see throughout this book.
Linux uses an enhanced version of the Bourne shell called bash or 
the “Bourne-again” shell. The bash shell is the default shell on most Linux 
distributions, and /bin/sh is normally a link to bash on a Linux system. You 
should use the bash shell when running the examples in this book.


- ## Basic Commands

Now let’s look at some more Unix commands. Most of the following programs
take multiple arguments, and some have so many options and formats
that an unabridged listing would be pointless. This is a simplified list
of the basic commands; you don’t need all of the details just yet.

- ## `ls`
The ls command lists the contents of a directory. The default is the current
directory. Use `ls -l` for a detailed (long) listing and `ls -F` to display file
type information. (For more on the file types and permissions displayed
in the left column below, see Section 2.17.) Here is a sample long listing; it
includes the owner of the file (column 3), the group (column 4), the file
size (column 5), and the modification date/time (between column 5 and
the filename):

- `$ ls -l`

        total 3616
        -rw-r--r-- 1 juser users 3804 Apr 30 2011 abusive.c
        -rw-r--r-- 1 juser users 4165 May 26 2010 battery.zip
        Basic Commands and Directory Hierarchy 15
        -rw-r--r-- 1 juser users 131219 Oct 26 2012 beav_1.40-13.tar.gz
        -rw-r--r-- 1 juser users 6255 May 30 2010 country.c
        drwxr-xr-x 2 juser users 4096 Jul 17 20:00 cs335
        -rwxr-xr-x 1 juser users 7108 Feb 2 2011 dhry
        -rw-r--r-- 1 juser users 11309 Oct 20 2010 dhry.c
        -rw-r--r-- 1 juser users 56 Oct 6 2012 doit
        drwxr-xr-x 6 juser users 4096 Feb 20 13:51 dw
        drwxr-xr-x 3 juser users 4096 May 2 2011 hough-stuff


- ##  cp
In its simplest form, cp copies files. For example, to copy file1 to file2,
enter this:

        $ cp file1 file2
 
To copy a number of files to a directory (folder) named dir, try this instead:

        $ cp file1 ... fileN dir

- ##  mv
The mv (move) command is like cp. In its simplest form, it renames a file. For
example, to rename file1 to file2, enter this:

        $ mv file1 file2
You can also use mv to move a number of files to a different directory:

        $ mv file1 ... fileN dir

- ##  touch
The touch command creates a file. If the file already exists, touch does not
change it, but it does update the file’s modification time stamp printed with
the ls -l command. For example, to create an empty file, enter this:

        $ touch file
Then run ls -l on that file. You should see output like the following,
where the date and time u indicate when you ran touch:

        $ ls -l file
        -rw-r--r-- 1 juser users 0 May 21 18:32u file


- ##  rm
To delete (remove) a file, use rm. After you remove a file, it’s gone from your
system and generally cannot be undeleted.

        $ rm file


- ##  echo
The echo command prints its arguments to the standard output:

        $ echo Hello again.
        Hello again.

The echo command is very useful for finding expansions of shell globs
(“wildcards” such as *) and variables (such as $HOME), which you will encounter
later        


- # File Modes and Permissions
Every Unix file has a set of permissions that determine whether you can read,
write, or run the file. Running ls -l displays the permissions. Here’s an
example of such a display:

        -rw-r--r--u 1 juser somegroup 7041 Mar 26 19:34 endnotes.html

The file’s mode u represents
the file’s permissions and some
extra information. There are four
parts to the mode, as illustrated in
Figure 2-1.
The first character of the mode
is the file type. A dash (-) in this position,
as in the example, denotes
a regular file, meaning that there’s
nothing special about the file. This is
by far the most common kind of file.
Directories are also common and are
indicated by a d in the file type slot.

The rest of a file’s mode contains the permissions, which break down into
three sets: user, group, and other, in that order. For example, the `rw-` characters
in the example are the user permissions, the `r--` characters that follow are the
group permissions, and the final `r--` characters are the other permissions.
Each permission set can contain four basic representations:
`r` Means that the file is readable.
`w` Means that the file is writable.
`x` Means that the file is executable (you can run it as a program).
- Means nothing.
The user permissions (the first set) pertain to the user who owns the
file. In the preceding example, that’s juser. The second set, group permissions,
are for the file’s group (somegroup in the example). Any user in that
group can take advantage of these permissions.

Everyone else on the system has access according to the third set, the
other permissions, which are sometimes called world permissions.

| Mode | Meaning          | Used For |
| :-------  | :------------------------- |:------------------------- |
|644 user: |read/write; group, other: |read files|
|600 user: |read/write; group, other: |none files|
|755 user: |read/write/execute; group, other: |read/execute directories, programs|
|700 user: |read/write/execute; group, other: |none directories, programs|
|711 user: |read/write/execute; group, other: |execute directories|

- #### Symbolic Links

        lrwxrwxrwx 1 ruser users 11 Feb 27 13:52 somedir -> /home/origdir

 ##### Creating Symbolic Links

To create a symbolic link from target to linkname, use ln -s:

        $ ln -s target linkname

- ## Navigating Directories

Unix has a directory hierarchy that starts at /, sometimes called the root
directory. The directory separator is the slash (/), not the backslash (\).
There are several standard subdirectories in the root directory, such as
/usr.

When you refer to a file or directory, you specify a path or pathname.
When a path starts with / (such as /usr/lib), it’s a full or absolute path.
A path component identified by two dots (..) specifies the parent of a
directory. For example, if you’re working in /usr/lib, the path .. would refer
to /usr. Similarly, ../bin would refer to /usr/bin.

One dot (.) refers to the current directory; for example, if you’re in
/usr/lib, the path . is still /usr/lib, and ./X11 is /usr/lib/X11. You won’t have
to use . very often because most commands default to the current directory
if a path doesn’t start with / (you could just use X11 instead of ./X11 in the
preceding example).

A path not beginning with / is called a relative path. Most of the time,
you’ll work with relative pathnames, because you’ll already be in the directory
you need to be in or somewhere close by.

Now that you have a sense of the basic directory mechanics, here are
some essential directory commands.

- cd

The current working directory is the directory that a process (such as the shell) is
currently in. The cd command changes the shell’s current working directory:

        $ cd dir

If you omit dir, the shell returns to your home directory, the directory you
started in when you first logged in.

- mkdir

The mkdir command creates a new directory dir:

        $ mkdir dir

- rmdir

The rmdir command removes the directory dir:

        $ rmdir dir

If dir isn’t empty, this command fails. However, if you’re impatient, you
probably don’t want to laboriously delete all the files and subdirectories
inside dir first. You can use rm -rf dir to delete a directory and its contents,
but be careful! This is one of the few commands that can do serious damage,
especially if you run it as the superuser. The -r option specifies recursive
delete to repeatedly delete everything inside dir, and -f forces the delete
operation. Don’t use the -rf flags with globs such as a star (*). And above
all, always double-check your command before you run it.

- ## Archiving and Compressing Files

Now that you’ve learned about files, permissions, and possible errors, you
need to master gzip and tar.

- gzip
The program gzip (GNU Zip) is one of the current standard Unix compression
programs. A file that ends with .gz is a GNU Zip archive. Use gunzip
file.gz to uncompress <file>.gz and remove the suffix; to compress it again,
use gzip file.

- tar

Unlike the zip programs for other operating systems, gzip does not create
archives of files; that is, it doesn’t pack multiple files and directories into
one file. To create an archive, use tar instead:

        $ tar cvf archive.tar file1 file2 ...

- Unpacking tar files

To unpack a .tar file with tar use the x flag:

        $ tar xvf archive.tar

- ## Compressed Archives (.tar.gz)

Many beginners find it confusing that archives are normally found compressed,
with filenames ending in .tar.gz. To unpack a compressed archive,
work from the right side to the left; get rid of the .gz first and then worry
about the .tar. For example, these two commands decompress and unpack
<file>.tar.gz:

        $ gunzip file.tar.gz
        $ tar xvf file.tar        

- zcat

The method shown above isn’t the fastest or most efficient way to invoke tar
on a compressed archive, and it wastes disk space and kernel I/O time. A
better way is to combine archival and compression functions with a pipeline.
For example, this command pipeline unpacks <file>.tar.gz:

        $ zcat file.tar.gz | tar xvf -
        $ tar ztvf file.tar.gz

-  ## Dot Files
Change to your home directory, take a look around with ls, and then run
ls -a. Do you see the difference in the output? When you run ls without the
-a, you won’t see the configuration files called dot files. These are files and
directories whose names begin with a dot (.). Common dot files are .bashrc
and .login, and there are dot directories, too, such as .ssh.
There is nothing special about dot files or directories. Some programs
don’t show them by default so that you won’t see a complete mess when listing
the contents of your home directory. For example, ls doesn’t list dot
files unless you use the -a option. In addition, shell globs don’t match
dot files unless you explicitly use a pattern such as .*.
### NOTE
        You can run into problems with globs because .* matches . and .. (the current and
        parent directories). You may wish to use a pattern such as .[^.]* or .??* to get all
        dot files except the current and parent directories.
