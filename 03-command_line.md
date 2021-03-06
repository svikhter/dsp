# Learn command line

Please follow and complete the free online [Bash Scripting Tutorial](https://ryanstutorials.net/bash-scripting-tutorial/) or [Codecademy's Learn the Command Line](https://www.codecademy.com/learn/learn-the-command-line). These are helpful tutorials. You should be able to go through these in a couple of hours.

**Note:** Bash is not installed on a PC. Rather, PC users must install Cygwin. Once Cygwin has been installed, the command line interface witll _emulate_ bash. You can find all information regarding Cygwin [here](https://www.cygwin.com/).

---

### Q1.  Cheat Sheet of Commands  

Here's a list of items with which you should be familiar:  
* show current working directory path
* creating a directory
* deleting a directory
* creating a file using `touch` command
* deleting a file
* renaming a file
* listing hidden files
* copying a file from one directory to another

Make a cheat sheet for yourself: a list of at least **ten** commands and what they do.  (Use the 8 items above and add a couple of your own.)  

> > **pwd**  - print working directory)   
    **cd mydir**  - change directory .    
    **cd** .. - up one level .   
    **mkdir**  - create directory .   
    **mkdir -p** .   
    **rmdir mydir**  -remove directory .   
    **touch myfile.txt**  - creates file, doesn't open the file .   
    **touch myfile1.txt myfile2.txt**  - creates multiple files .   
    **cat > myfile1.txt**  - creates file, opens for editing .   
    **cat myfile1.txt** -  view the content of the file .   
    **> myfile3.txt** -  creates file using standard redirect symbol,  doesn't open it, can only create one file at the time, and if preceeded by a commend, then redirects the output of the command to the file).
    **rm myfile1.txt** - removes the file .   
    **rmdir mydir** - removes directory .   
    **mv myfile1.txt myfile2.txt**  - renames the file, kindof moves to the new "name" .   
    **mv myfile1.txt /dir1/dir2 /dira/dirb** - moves the file to another directory .   
    **cp**  - copies the file .   
    **cp -r /dir1 /dir2** -  copies the entire directory structure to a new directory .   
    **ln**  - creates a link .   
    **ln - s /dir1/Downloads /dir1/Desktop**  - creates a symbolic link    
    **chmod**  - changes permissions .   
    **chmod +x myscript.sh**  - adds execute permissions to the script .   
    **chmod -x myscript.sh** - removes execute permissions to the script) .   
    **man <command>** - shows manual pages(the "help") .   
    **man -k <item>**  - manual pages where item is found, navigate to next by pressing **n** .   
    **cal**  - shows calendar .   
    **ls**  - directory content .   
    **ls -l**  - directory listing .   
    **ls -a** -  directory listing including hidden files .   
    **awk** - this command provides scripting language for text processing 
      *Here is how it is used:  
      $ options program file  
      Options:    
      -F <filesepartor> - file separator  (default is space/tab) 
      -f <file> - the file that contains awk script     
      -v var=value - varioable assignment   
      It assignes variables to each data field in file:  
         $0 for the whole line.  
         $1 for the first field.  
         $2 for the second field.  
         $n for the nth field.  
      Example: prints first word in each line:  
      $ awk '{print $1}' myfile*
   
   
   
      
   
   
    
    
 

---

### Q2.  List Files in Unix   

What do the following commands do:  
`ls`  
`ls -a`  
`ls -l`  
`ls -lh`  
`ls -lah`  
`ls -t`  
`ls -Glp`  

> > ls (directory listing) .   
**ls** - a (directory listing including hidden files) .   
**ls** -l (directory listing, in long format) .   
**ls** -lh (dir listing, long format, when -h is used with -l use unit suffixes for file size) .   
**ls** -lah (dir listing, long format, include hidden files, use unit suffixes) .   
**ls** -t (dir listing sorted by time modified, most recent first) .   
**ls** - Glp (dir listing, colorized output, long format, writes a slash after each filename if its a dir) .   


---

### Q3.  More List Files in Unix  

Explore these other [ls options](http://www.techonthenet.com/unix/basic/ls.php) and pick 5 of your favorites:

> > ls -t (most recent files) .   
ls -C (multi-column output) .   
ls -S (sort files by size) .   
ls -q (printing of non graphic characters in file name as ?) .   
ls -w (raw printing of non printable characters) .   
ls -v (unedited printing of non graphic characters) .   

---

### Q4.  Xargs   

What does `xargs` do? Give an example of how to use it.

> > xargs is a command that converts input into an argument to a command.    
It is useful when we need to apply a command to multiple filepaths, to search,or manipulate with multiple files. 

An simple example (both commands create empty file).          
touch myfile1.txt .   
echo myfile2.txt | xargs touch .   




 

