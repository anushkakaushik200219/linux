# LINUX

This tutorial will help you get started with Linux.



```bash
 Audience of this tutorial are beginners, so don't expect advanced concepts.
```


## Pre-requisite:
 
 ```bash
  AWS Account or any Linux Distribution.
```

## Making Your First Keystrokes

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

To check kernel version:
    
    [me@linuxbox ~]$ uname -r

or 

    [me@linuxbox ~]$ uname --help  

for displaying all parameters like:

| Parameter | Description          |
| :-------  | :------------------------- |
| `a`       |  Display all information   |
| `o`       |  Display the operating system (usually GNU/Linux)   |
| `r`       |  Display kernel release   |
| `v`       |  Display kernel version   |

The `uname` command includes additional options that you can use to get more information about your kernel. Simply add an option after the command:

- a – Display all information
- o – Display the operating system (usually GNU/Linux)
- r – Display kernel release
- v – Display kernel version
