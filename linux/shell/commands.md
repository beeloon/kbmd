## man
an interface to the system reference manuals
```bash
man mkdir
```

## cat
concatenate files and print on the standard output.

```bash
# to see an input stream, enter cat (with no filenames) and press enter. 
# Press ctrl + D on an empty line to terminate cat and return to the shell prompt.
cat

# display the content of the /etc/passwd
cat /etc/passwd

# output the contents of one or more files
cat file1 file2
```

## ls
list directory contents

show all files in long hunamreadable format:
- long -l
- all files -a
- humanreadable -h
```bash
ls --all --human-readable -l [FILE] 

# short form
ls -lah [FILE]
```

## clear
clear the terminal screen
```bash
clear

# clear all previous terminal output
clear & clear
```

## exit
cause normal process termination
```bash
exit
```

## cp
OpenSSH secure file copy
```bash
# copy from server $path1 to client @path2
scp -P {port} {user}@{host}: $path1 $path2

# copy from client $path1 to server @path2
scp -P {port} $path1 {user}@{host}: $path2
```

## scp
```bash
# copy files and directories
cp file1 file2

```

## mv
move(rename) files 
```bash
mv file1 file2

# move a number of files to a different directory
mv file1 ... fileN dir
```

## touch
create file / change file timestamps
```bash
touch file
```

## rm
remove files or directories
```bash
rm file

# remove directories
#   - recursive remove -r
#   - force remove -f 
rm -rf dir
```

## echo
display a line of text
```bash
echo Hello world
```

## cd
change directory
```bash
cd dir

# move to /home directory
cd 

# move one level below
cd ..

# move to previos directory
cd -
```

## mkdir
create new directory
```bash
mkdir dir
```

## rmdir
delete directory
```bash
rmdir
```

## grep
pringt lines that matches patterns
```bash
# two most important options:
#   - case-insensitive matches [-i]
#   - all lines that don't match pattern [-v]

# two important things to remember about RegExp:
#   - .\* matches any number of characters (like the * in wildcards).
#   - . matches one arbitrary character.
grep pattern file

# print the lines in /etc/passwd file that contains word "root"
grep root /etc/passwd

# check every file in /etc directory for word "root"
grep root /etc/*

# find word root in Desktop dir and recursively in all inner dirs
grep -r root Desktop

# list all processes and then find every line with word root and count how many lines found 
ps aux | grep -c root

```

## less
output file when command’s output is long and scrolls off the top of the screen
```bash
less /usr/share/dict/words
```

## pwd
print name of current/working directory
```bash
pwd
```

## diff
compare files line by line
```bash
# r - recursively
# q - don't show the difference, and only define if they're different or not
diff [-q|-r] path1 path2
```

## file
determine file type
```bash
file test.txt
```

## find and locate
search for files in a directory hierarchy
```bash
# find "Desktop" in $HOME directory and list file in ls -dils format on standard output
find ~/ -name "Desktop" -ls

# find test.txt in dir /docs 
find /docs -name test.txt

# find all txt files in root dir
find ~/ -name "*.txt"
```

## head and tail
output the first/last part of files
```bash
# output first 5/last 5 lines in /usr/share/dict/words file 
head -2 /usr/share/dict/words
tail -2 /usr/share/dict/words
```

## sort
sort lines of text files
```bash
# two useful options:
#   - sort in numberical order, if file's lines starts with numbers [-n]
#   - reverse the order of the sort [-r] 
sort file
```

## passwd
change user password
```bash
passwd username
```

## wc
print newline, word, and byte counts for each file
```bash
# count amount of lines
wc -l file.txt

# count amount of words
wc -w file.txt

# count amount of characters
wc -c file.txt
```

## ps
report a snapshot of the current processes.
```bash
ps

# list all running processes
ps -e

# shows the names of all the running processes, their process identification numbers (PIDs), 
# the PIDs of their parents (PPIDs), when they began (STIME), what terminal, if any, they're attached to (TTY), 
# how much CPU time they've racked up (TIME), and their full path names
ps -ef

# the same as ps
ps aux
```

## kill (killall)
The kill command sends a signal to specified processes or process groups, causing them to act according to the signal. When the signal is not specified, it defaults to -15 (-TERM).
The most commonly used signals are:

1 (HUP) - Reload a process.
9 (KILL) - Kill a process.
15 (TERM) - Gracefully stop a process.

```bash
# will gracefully stop process 
kill <process pid>

# will immediately kill process
kill -9 <process pid>

# will stop/kill all process with <name>
killall <name>
killall -9 node
```

## chmod
change file mode bits

chmod can be used with [numeric permissions](https://www.cyberciti.biz/faq/unix-linux-bsd-chmod-numeric-permissions-notation-command/) mode

```bash
# make file executable
chmod +x sample.txt

# Read by owner only 
chmod 400 sample.txt 

# Read by group only
chmod 040 sample.txt 

# Read by anyone
chmod 004 sample.txt 

# Write by owner only
chmod 200 sample.txt 

# Write by group only
chmod 020 sample.txt 

# Write by anyone
chmod 002 sample.txt 

# Execute by owner only
chmod 100 sample.txt 

# Execute by group only
chmod 010 sample.txt 

# Execute by anyone
chmod 001 sample.txt 

# Allow read permission to owner and group and anyone.
chmod 444 sample.txt

# Allow everyone to read, write, and execute file.
chmod 777 sample.txt
```

## history
The history command show a list of used commands with their id

```bash
history
!2

# if you want to run command from the end of the list
# you can also use negative numbers
!-5 

# we can use command symbols to run the last command
# that match these symbols
!find
!git

# If you want to check which command will be used
# before runneng it, you  can specify :p option
# it stands for 'print', and show the whole command text
!git:p

# If you want to use arguments of certain command
# for another command you can use this with !*
# eg. will replace !5157* to arguments that was used
# with command which id 5157 in history (eg. kill -9 node)
kill !5157*
# the same example, without command history id
# !* will return arguments of the last command you have used
killall -9 node
kill !*
# or check how command will look with arguments from
# another command
kill !*:p
# you can also specify certain argument by it index
# eg. will return => cat file2.txt
cp file1.txt file2.txt
cat !:2
# or you can specify range or arguments
# eg. will return 2,3,4 arguments => -f -h -F
ls -a -f -h -F
!:2-4

# to pick last argument of some command use !$
# for first argument use !^
# eg. return last argument of ls that was matched to last ls command in history
!ls:$

# eg. return all arguments from 2 to the last one
ls !ls:2-$
```

## && (AND)
Run a sequence of commands  
```bash
# will got to api/coupon dir and then run start script
cd api/coupon && npm start

# if one of the command in sequence will throw an error
# next commands in sequence will not run
# eg. throw an error when making a directory and won't run cd command
mkdir /root/mydir && cd /root/mydir
```

## || (OR)
Run the first command that will not throw an error 
```bash
# will not create new dir, but will try to go to /root/mydir dir 
mkdir /root/mydir || cd /root/mydir
```

## unzip 
list, test and extract compressed files in a ZIP archive
```bash
# will unzip ARCHIVE.zip 
unzip [ARCHIVE.zip]
```

## gzip
gzip, gunzip, zcat - compress or expand files
```bash
# will unzip ARCHIVE.zip and then delete ARCHIVE.zip
gzip [ARCHIVE.zip]
```

## zip
package and compress (archive) files
```bash
# archive n file to ARCHIZE.zip
zip [ARCHIVE.zip] file1, file2, ..., fileN
```

## gzip
gzip, gunzip, zcat - compress or expand files
```bash
# will archive [FILE] to FILE.gz archive and delete original [FILE]
gzip [FILE]
```

## du
estimate file space usage
```bash
# -h - human readable form
# -d - print the total for a directory (or file, with --all) only if it is N  or  fewer  levels  below  the  command  line  argument; --max-depth=0 is the same as --summarize
du [-d|-h] path
```

## df
report file system disk space usage
```bash
# -h - human readable form
df [-h]
```