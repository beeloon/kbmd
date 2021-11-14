### Count number of files and directories 
```bash
# without hidden files
ls | wc -l

# including hidden files
ls -A | wc -l

# including the subdirectories
tree -a

# only the files, not directories, in current directory and its subdirectories.
find . -type f | wc -l

# only the files, not directories and only in current directory, not subdirectories
find . -maxdepth 1 -type f | wc -l
```

### Math pattern in big file and output in less
```bash
grep ie /usr/share/dict/words | less

# Recursively find from current directory {word} in all files that starts with .
grep -r {word} .*
grep -r "PATH" .*

# find work site recursively, case insensitive, in /etc/apache2 dir
grep -ri site /etc/apache2
```

### Check if port is used by some app
```bash
netstat -nlp | grep 8080
```

### Get information about all processes running on the system
```bash
ps -A
```

### Kill process on port 5432 and run docker container (horai)
```bash
sudo kill $(sudo lsof -t -i:5432) && docker run --rm --name horai_coupon_db -p 5432:5432 -e POSTGRES_PASSWORD=horai -d postgres 2>/dev/null
```

### Show all commands in the history that matched {word}
```bash
history | grep install
```

### Use the last command in your new command
```bash
# will return sudo apt install cmatrix vim
apt install cmatrix
sudo !! vim
```

### History shortkeys
```bash
# Run last command
!!

# Run the most recent command that starts with blah
!blah

# Print out the command that !blah would run (also adds it as the latest command in the command history
!blah:p

# The last word of the previous command (same as OPTION+.)
!$

# Print out the word that !$ would substitute
!$:p

# The previous command except for the first word (e.g., if you type find some_file.txt /, then !* would give you some_file.txt /)
!*

# Print out what !* would substitute
!*:p
```

### Change {word} for previous command
```bash
# will change restart with status and run
sudo systemctl restart apache2
^restart^status
# sudo systemctl status apache2
```

### Run process in background
```bash
# will unzipping archive in background 
tar xjf archive.tar.bz2 &

# to proceed work of the process even if you close terminal, use nohup
nohup tar xjf archive.tar.bz2 &
```

### Clear console
```bash
clear && clear
```

### Reset terminal
```bash
# when your encoding is broke, you can use reset command
reset
```