---
layout: default
---

# Command-Line Tools for Linguists, Fall 2024
This course offers a comprehensive exploration of the command-line environment, where we will learn various tools to enhance our productivity and streamline our workflow. Each week, we will tackle different topics related to command-line usage, ranging from navigating UNIX systems to scripting and version control.

| Week    | Overview        | Key Points         |
| ------- | --------------------- | ------------------- |
| Week 1 | Introduction to Command Line Environments |  |
| Week 2 | Navigating a UNIX System |  |
| Week 3 | Basic Corpus Processing |  |
| Week 4 | Advanced Corpus Processing | |
| Week 5 | Scripting and Configuration Files | |
| Week 6 | Installing and Running Programs | |
| Week 7 | Version Control | |

## Week 1 Introduction to Command Line Environments
- Setting up and launching command-line on Windows using [Ubuntu](https://ubuntu.com/download)
- Command line basics
  | Command | Role |
  | ------ | --------------------- |
  | `ls` | list files in a directory |
  | `ls /mnt/c/Users` | list files in a specific Windows directory |
  | `pwd` | show the current directory path |
  | `whoami` | show username |
  | `cp` | copy files |
  | `mv` | move / rename files |
  | `rm` | delete files |
  | `mkdir` | creat a directory |
  | `rmdir` | delete a directory |
  | `cd` | change the working directory |
  | `cat` | display file contents |
  | `less` | view file page by page |
  | `wget` | download files from websites |
- Quitting applications
  - Quit `less` using `q`
  - Quit `vim` using `Esc`
  - Quit input (like `cat`) or log out of terminal using `Ctrl+D`
  - Quit text editors (like `nano`) using `Ctrl+X`
  - Quit almost everything using `Ctrl+C`

Reflection: 1-3 sentences

## Week 2 Navigating a UNIX System
- Handling directories
  - `mkdir` creat a new directory
  - `rmdir` delete empty directory
  - `rm -R` remove directories with content
  - `cp -R` copy directories
  - `mv` move / rename directories
  - `tar` and `gzip` compress directories and files
  ```bash
  tar -czf archive.tar.gz /path/to/directory
  ```
  `-c`create a new archive, `-z`compress the archive using `gzip.`, `-f`specify the name of the archive file
- File system
  - `/home` user home directories
  - `/bin` for essential commands like `ls`
  - `/tmp` for temporary files
  - `which` or `where` return the path of executable files
- Process management
  - monitoring processes:
    - `top`: displays real-time information about running processes, including their CPU and memory usage.
  - foreground & background processes:
    - `&`: at the end of a command, runs that command as a background process
    - `fg`: brings a background process to the foreground
    - `CTRL+Z`: suspends a foreground process and sends it to the background. paused but not terminated
  - kill processes:
    - `ps`: displays information about currently running processes, including their Process IDs (PIDs)
    - `kill`: terminates a process by sending a signal, typically using the process’s PID
- **Remote server**
  - conneting to remote servers with `ssh` (secure shell)
    - `ssh puhti.csc.fi`，`CTRL+D` or `quit` to quit
    - `ssh <username>@<servername>`
  - copying to/from remote servers with `scp` (secure copy protocol)
    - `scp <user_1>@<server_1>:<path_1> <user_2>@<server_2>:<path_2>`<br>`scp -r` for directories
    - from local to remote: `scp <local_path> <username>@<remote_server>:<remote_path>`
    - from remote to local: `scp <username>@<remote_server>:<remote_path> <local_path>`
    - example: `scp KIK-LG219/week1/life_of_bee.txt puhti:~` `scp puhti:~/life_of_bee.txt .`

## Week 3 Basic Corpus Processing


## Week 4

## Week 5

## Week 6

## Week 7

<img src="assets/images/rei_picture.jpg" alt="Photo" hspace="20" width="30%" align="left"/>

```makefile
Makefile
```

```bash
terminal
```
- key points 2<br>
`code`
