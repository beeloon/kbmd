# Input/Output operators

STDERR STDOUT STDIN

## < 
for redirecting input to a source other than the keyboard

## > 
for redirecting output to destination other than the screen

## >> 
for doing the same, but appending rather than overwriting

## | 
for piping output from one command to the input of another

```bash
# list everything in the current directory and capture the output in a file named listing.txt.
ls > listing.txt

# if listing.txt already exists, it gets overwritten. 
# if you use the >> operator instead, the output from ls is appended to what's already in listing.txt
ls >> listing.txt
```

```bash
# pipe operator redirects the output of the first command to the input of the second command. 
# Let's say you use cat to display the contents of a large file, but the content scrolls by too quickly for you to read. 
# You can make the output more manageable by piping the results to another command such as more. 
# following command lists all the currently running processes
# but once the screen is full, the output pauses until you select Enter to show the next line:
ps -ef | more

# you can also pipe output to head to see just the first several lines:
ps -ef | head

# suppose you want to filter the output to include only the lines that contain the word "daemon." 
# for that you can use output of ps command as an input for grep command 
ps -ef | grep daemon
```

```bash
# you can also use files as input
# by default, standard input comes from the keyboard, but it too can be redirected. 
# to get input from a file instead of the keyboard, use the < operator. One common sysadmin task is to sort the contents of a file. 
# as the name suggests, sort sorts text in alphabetical order:
sort < file.txt

# to save the sorted results to a new file, you can redirect input and output:
sort < file.txt > sorted_file.txt

# you can use I/O operators to chain Linux commands as needed. Consider the following command:
cat file.txt | fmt | pr | lpr
```