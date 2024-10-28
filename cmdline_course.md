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
- **Command line basics**
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
- **Quitting applications**
  - Quit `less` using `q`
  - Quit `vim` using `Esc`
  - Quit input (like `cat`) or log out of terminal using `Ctrl+D`
  - Quit text editors (like `nano`) using `Ctrl+X`
  - Quit almost everything using `Ctrl+C`

*Reflection*: 1-3 sentences

## Week 2 Navigating a UNIX System
- **Handling directories**
  - `mkdir` creat a new directory
  - `rmdir` delete empty directory
  - `rm -R` remove directories with content
  - `cp -R` copy directories
  - `mv` move / rename directories
  - `tar` and `gzip` compress directories and files<br>`tar -czf archive.tar.gz /path/to/directory`, `-c`create a new archive, `-z`compress the archive using `gzip.`, `-f`specify the name of the archive file
- **File system**
  - `/home` user home directories
  - `/bin` for essential commands like `ls`
  - `/tmp` for temporary files
  - `which` or `where` return the path of executable files
- **Process management**
  - monitoring processes:<br>
    `top`: displays real-time information about running processes, including their CPU and memory usage.
  - foreground & background processes:<br>
    `&`: at the end of a command, runs that command as a background process<br>
    `fg`: brings a background process to the foreground<br>
    `CTRL+Z`: suspends a foreground process and sends it to the background. paused but not terminated<br>
  - kill processes:<br>
    `ps`: displays information about currently running processes, including their Process IDs (PIDs)<br>
    `kill`: terminates a process by sending a signal, typically using the process’s PID
- **Remote server**
    ```bash
    $ ssh puhti.csc.fi
    $ CTRL+D
    $ scp KIK-LG219/week1/life_of_bee.txt puhti:~
    $ scp puhti:~/life_of_bee.txt .
    ```
  - conneting to remote servers with `ssh` (secure shell)<br>
    `ssh puhti.csc.fi`<br>
    `CTRL+D` or `quit` to quit<br>
    `ssh <username>@<servername>`
  - copying to/from remote servers with `scp` (secure copy protocol)<br>
    `scp <user_1>@<server_1>:<path_1> <user_2>@<server_2>:<path_2>`<br>`scp -r` for directories<br>
    from local to remote: `scp <local_path> <username>@<remote_server>:<remote_path>`<br>
    from remote to local: `scp <username>@<remote_server>:<remote_path> <local_path>`

*Reflection*: 

## Week 3 Basic Corpus Processing
- **Basic text processing**
  - `tr`: `tr "a" "A"` translate characters in a text stream
    - `tr -d`: delete specified characters
    - `tr -s`: squeeze multiple consecutive characters into one<br>`cat filename.txt | tr -s "[:space:][:punct:]" "\n" > new_filename.txt` tokenize the text into one word per line
  - `sort`: `sort new_filename.txt > sort_filename.txt` sort lines in alphabetical order
    - `sort -f`: ignore case
    - `sort -r`: in reverse order
  - `uniq`: remove duplicate lines
    - `uniq -i`: ignore case
    - `uniq -c`: count the number of occurrences of each line
    - `uniq -d`: display only th duplicate lines
    - `uniq -u`: delete all repeated lines, extrace lines that are completely unique
  - `wc`: word count
    - `wc -l`: count the number of lines
  - `cut`: extract specific sections
    - `cut -d',' -f1 file.csv > new_file.csv`: `-d','`specifies the delimiter that separates the fields in the input, `-f1`specifies which field to extract, '1' indicates the first field (or column) from each line
  - `tail`: output the last part of files, also be used to skip the first few lines of a file
    - `tail -n +2 file.csv > tail_file.csv`: `-n +2`start printing from line 2
- **`egrep` and regular expression**<br>
  `egrep` is used for searching text using regular expressions
  - `egrep " had [a-z]*ed "`, `*`means the character can occur zero or more times
  - `egrep "\bhad [a-z]*ed\b"`, `\b` is used to specify word boundaries
  - `egrep "^[Aa][a-zåäö]*"`, `^`beginning of the line
  - `egrep "[a-zA-ZåäöÅÄÖ]*ss[aä]$"`, `$` end of the line
  - `egrep "^[a-zA-ZåäöÅÄÖ]{4}ss[aä]$" `, `{}`the preceding character class must occur exactly certain times
  - `egrep --color "\b[a-zåäö]*ss[aä] [a-zåäö]*ss[aä]\b" file.txt > new_file.txt`, highlight and store matching lines in a new file
- **Basic analysis of CSV files**
  `egrep -w -f`: `-w` only match whole words, `-f` read a file<br>`egrep -w -f search.csv basic.csv` read the patterns from `search.csv`, and searches through the 'basic.csv' file for lines that match those patterns
  ```bash
  $ wc -l Languages.csv
  $ wc -l LanguagesDirectionality.csv
  $ cut -d',' -f1,1 Languages.csv > Languages_cut.csv
  $ cut -d',' -f1,1 LanguagesDirectionality.csv > LanguagesDirectionality_cut.csv
  $ cat Languages_cut.csv LanguagesDirectionality_cut.csv > Languages_all.csv
  $ tail -n +2 LanguagesDirectionality_cut.csv
  $ tail -n +2 LanguagesDirectionality_cut.csv > LanguagesDirectionality_tail.csv
  $ cat Languages_cut.csv LanguagesDirectionality_tail.csv > Languages_all.csv
  $ sort Languages_all.csv > Languages_sorted.csv
  $ uniq -u Languages_sorted.csv
  $ uniq -d Languages_sorted.csv
  $ uniq -u Languages_sorted.csv > Languages_uniq.csv
  $ egrep -w -f Languages_uniq.csv LanguagesDirectionality.csv
  ```

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
