
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



