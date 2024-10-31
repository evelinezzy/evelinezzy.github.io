---
layout: default
title: "Command-Line Course"
---

# Introduction to Cmdline Course:
![Meme](assets/images/cmdimg.png)
<p>This is a course on how to solve fundamental problems in texual analysis in the command-line environment. The course is delivered online, with weekly lecture videos and materials.</p>
<p>Participants will be given 1 week to complete each assignment. The assignment will be available on the Friday before the Tuesday session, and will be due on the Friday after.</p>

# Week 1: Introduction to Command Line Environments
## Summary
<p>This week, we'll begin by installing our command-line environments, which are the foundation for everything we'll be doing throughout the course. And know how to get content from web, rename and remove file, quit applications.</p>
<p>Reflection: This weeks I learned some basics. The setting up part was a little troublesome for me. I cannot work as the owner under my user name. This issue is solved mainly by using sudo and sometimes change the ownership.</p>
## Code
In Ubuntu in Windows:

| Command Explanation   |                                    | Commands                           |
|-----------------------|-------------------------------------------------------------------------|
| System Information    | list of files in this path         | `ls`                               |
|                       | tell which path is this            | `pwd`                              |
|                       | tell which user am I               | `whoami`                           |
|                       | get content from website           | `wget`                             |
|-----------------------|-------------------------------------------------------------------------|
| File Operations       | move file from one path to another | `mv [filename] [destination_path]` |
|                       | diplay file 			     | `cat`                              |
|                       | read file                          | `less`                             |
|                       | copy file to path                  | `cp [filename] [destination_path]` |
|                       | remove file or empty directory     | `rm`                               |
|                       | make new directory                 | `mkdir`                            |
|                       | change directory                   | `cd ..` `cd [path]`                |
|-----------------------|-------------------------------------------------------------------------|
| Keyboard Shortcuts    | quit                               | `q`                                |
|                       | exit                               | `Esc`                              |
|                       | end                                | `Ctrl-c`                           |
|                       | end                                | `Ctrl-d`                           |
|                       | cut selected text and copy         | `Ctrl-x`                           |
|                       | copy selectedd text                | `Ctrl-c`                           |
|-----------------------|-------------------------------------------------------------------------|
| Download Example      | `wget https://imgs.xkcd.com/comics/operating_systems.png`               |
| Editing Example       | `nano operating_systems.png`                                            |

# Week 2: Navigating a UNIX System
## Summary
<p>This week we will learn more about the UNIX system. We'll see how to copy, move and remove directories.In the second part of this week, we'll learn about processes and process management. The third part of this week deals with working on a remote server using the programs ssh and scp.</p>
<p>Reflection: I am glad to learn about the processing part. Sometimes the terminal keeps running and I use kill to end some process.</p>
## Code
- **Handling directories**
  - cp -R: copy directories and their contents. 
  - rm -R: removes all files and subdirectories within the specified directory.
  - rmdir: remove empty directories.
  - which: locates the executable path.
- **Processing**
  - top: displays the currently running processes.
  - fg: brings a job (started in the background) back to the foreground.
  - CTRL+Z: temporarily suspends a currently running process in the terminal.
  - ps: lists currently running processes.
  - kill: terminate a process with its id.
- **Working on remote servers**
  - ssh: connect to a remote server over the Secure Shell (SSH) protocol.
  - scp: copy files or directories between the local and remote systems using the SSH protocol.

# Week 3: Basic Corpus Processing
## Summary
<p>This week is about using text processing tools in UNIX.</p>
<p>Reflection: The chapter helped me to use combined and more complex mixture of commands.</p>

## Code
<p>An example of combined usage: egrep -i "^a" katinka_rabe.word_list.txt | wc -l. It means that to count how many words with a lowercase "a" or uppercase "A" occur in  katinka_rabe.word_list.txt.</p>
- **Converting char. encodings**
  - file: determines the file type by inspecting its contents rather than relying on file extensions.
  - dos2unix: convert files with Windows-style line endings to unix style.
  - iconv: convert text file encodings.
- **Generating a word list**
  - tr '...' '...': translates characters. 
  - sort: sort lines in a file alphabetically or numerically.
  - unique: filters out or counts duplicate lines.
- **regex(Regular Expression)**
  - ^ : match the starting position within the string.
  - . : match any single character.
  - ? : zero or one occurrences of the preceding element. For example, colou?r matches both "color" and "colour".
  - * : zero or more occurrences of the preceding element. For example, ab*c matches "ac", "abc", "abbc", "abbbc", and so on.
  - + : one or more occurrences of the preceding element. For example, ab+c matches "abc", "abbc", "abbbc", and so on, but not "ac".
  - '[a-z]' : match all lower case letters from 'a' to 'z'.
- **Finding noun phrases**
  - egrep: able to use regex patterns to capture phrases. egrep '[A-Z][a-z]+ [A-Z][a-z]+' might match capitalized noun phrases like "New York".
- **Formatted text files**
  - cut: extracts specific fields or columns from a file. Example: cut -d',' -f1 myfile.csv extracts the first field in a CSV file.
  - sort: sorts lines in a file alphabetically or numerically. 
  - unique: filters or counts duplicates.

# Week 4: Advanced Corpus Processing
## Summary
<p>This week we will learn more about text processing using UNIX commands.</p>
<p>Reflection: I learned more lines for dealing with the text.</p>

## Code
- sed with -n, -E, //d, //p, s//g: 
  - -n: Suppresses automatic printing.
  - -E: Enables extended regex for more complex patterns.
  - //d: Deletes lines matching the pattern.
  - //p: Prints lines matching the pattern.
  - s///g: Substitutes text globally within each line. Example: sed -E 's/foo/bar/g' replaces "foo" with "bar".

# Week 5: Scripting and Configuration Files
## Summary
<p>This week we are putting together our commands in tidy "scripts" instead of typing them one by one</p>
<p>Reflection: I personally feel this chapter is most difficult among all... For the bash commands are different and more complex than in Ubuntu shell.</p>
## Code
<p>chmod u+x: give execute permission to file owners.</p>
<p>Some examples:</p>
|#!/bin/bash                                                                                    <br />
|# Check to see if no argument was provided by checking if the first character is zero length.  <br />
|if [ -z "$1" ];                                                                                <br />
|then                                                                                           <br />
|    echo "Please provide an Adjective as an argument."                                           <br />
|    exit 1                                                                                       <br />
|fi                                                                                             <br />
|                                                                                               <br />
|adjective=$1                                                                                   <br />
|                                                                                               <br />
|# Add 'er' to the Adjective                                                                    <br />
|echo "${adjective}er"                                                                          <br />
<br />
|archive.gz: foo bar                                                                            <br />
|    gzip $@ $^                                                                                <br />
|#This creates a gzip Archive (archive.gz) containing both fooand bar.                          <br />
|#Here, $@refers to the output file (archive.gz), and $^includes both dependencies(fooand bar). <br />

# Week 6: Installing and Running Programs
## Summary
<p>The first theme of this week is about installing programs.</p>
<p>Reflection: A relative easier chapter. And I had also already come across some related problems in Week 1 so I was familiar with this week. </p>
## Code
- **Becoming the root user**
  - su: Switches to another user (often root) if you have the password. Example: su switches to root.
  - sudo: Runs commands with superuser privileges temporarily. Example: sudo apt-get update.
  - passwd: Changes a user’s password.
  - whoami: Displays the current logged-in user.
- **Install software**
  - ![Install bash](assets/images/cmdimg2.png)
- **Write a makefile**
  - make al: Executes all tasks or targets defined in the makefile (often for building projects).
  - make clean: Removes temporary or compiled files, often used to reset the project’s state.

# Week 7: Version Control
## Summary
<p>This week we will be learning about version control. Version control is an integral part of developing projects.</p>
<p>Reflection: First time working with GitHub. I learned the necessity of working on local path and after confirming changes I make can I add, commit and push the files to master/main. </p>
## Code
- **git command**
  - git config --global user.name "Hande Celikkanat":  Sets the global username for Git commits.
  - git config --global user.email "hande.celikkanat@helsinki.fi": Sets the global email for Git commits.
  - git Clone https://github.com/USERNAME/cmdline-course.git: Clones a remote repository to the local machine.
  - git add .../.../filename: Stages all changes in the current directory.
  - git commit -m "some comment on the change": Commits staged changes with a message describing the changes.
  - git push origin master: Pushes committed changes to the master branch on the remote repository.
- **Commands in a makefile**
-  An example:

   | results/%.parsed.txt: results/%.sent.txt                                                                 <br />
   | # A target (file to be created) with a pattern that depends on an existing file with a similar pattern.<br />
   |    python3 src/parse.py $< $@                                                                       <br />
   | # `$<` is the first dependency, and `$@` is the target file.                                             <br />

# Week 8: Final Assignment
## Summary
<p>The final assignment for this course consists of building your own website and publishing it on Github pages.</p>
<p>Reflection: The assignment consists of four parts: creating a template repository; editing index.md; creating overleaf cv; creating a markdown file `cmdline_course.md`</p>
<p>I made a mistake in editing index.md in branch cmdline_coure so I did not see the change in my github website. I figured that out and problem solved.</p>

#THE END!
