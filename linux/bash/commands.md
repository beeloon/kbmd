#### shell globbing (wildcards)
. - current directory
\* - match any number or arbitrary characters
? - match one arbitrary character

#### man
an interface to the system reference manuals
```bash
man mkdir
```

#### cat
concatenate files and print on the standard output.

to see an input stream, enter cat (with no filenames) and press enter. Press ctrl + D on an empty line to terminate cat and return to the shell prompt.
```bash
cat
```

display the content of the /etc/passwd
```bash
cat /etc/passwd
```

output the contents of one or more files
```bash
cat file1 file2
```

#### ls
list directory contents

show all files in long hunamreadable format:
- long -l
- all files -a
- humanreadable -h
```bash
ls -lah
```

#### cp
copy files and directories
```bash
cp file1 file2
```

to copy a number of files to a directory (folder) named dir , try this instead:
```
cp file1 ... fileN dir
```

#### mv
move(rename) files 
```bash
mv file1 file2
```

move a number of files to a different directory
```bash
mv file1 ... fileN dir
```

#### touch
create file / change file timestamps
```bash
touch file
```

#### rm
remove files 
```bash
rm file
```

remove directories
- recursive remove -r
- force remove -f
```bash
rm -rf dir
```

#### echo
display a line of text

```bash
echo Hello world
```

#### cd
change directory
```bash
cd dir
```

move to /home directory
```bash
cd 
```

move to previos directory
```bash
cd ..
```

#### mkdir
create new directory
```bash
mkdir dir
```

#### rmdir
delete directory
```bash
rmdir
```

#### grep
pringt lines that matches patterns
```bash
grep pattern file
```

print the lines in /etc/passwd file that contains word text
```bash
grep root /etc/passwd
```

check every file in /etc directory
```bash
grep root /etc/*
```

two most important options:
- case-insensitive matches [-i]
- all lines that don't match pattern [-v]

two important things to remember about RegExp:
- .\* matches any number of characters (like the * in wildcards).
- . matches one arbitrary character.

#### less
output file when command’s output is long and scrolls off the top of the screen
```bash
less /usr/share/dict/words
```

#### pwd
print name of current/working directory
```bash
pwd
```

#### diff
compare files line by line
```bash
diff file1 file2
```

#### file
determine file type
```bash
file test.txt
```

#### find and locate
search for files in a directory hierarchy

find "Desktop" in $HOME directory and list file in ls -dils format on standard output
```bash
find ~/ -name "Desktop" -ls
```

#### head and tail
output the first/last part of files

output first 5/last 5 lines in /usr/share/dict/words file 
```bash
head -2 /usr/share/dict/words
tail -2 /usr/share/dict/words
```

#### sort
sort lines of text files
```bash
sort file
```

two useful options:
- sort in numberical order, if file's lines starts with numbers [-n]
- reverse the order of the sort [-r] 

#### passwd
change user password
```bash
passwd username
```

#### wc
print newline, word, and byte counts for each file