### Count number of files and directories 
without hidden files
```
ls | wc -l
```

including hidden files
```
ls -A | wc -l
```

including the subdirectories
```
tree -a
```

only the files, not directories, in current directory and its subdirectories.
```
find . -type f | wc -l
```

only the files, not directories and only in current directory, not subdirectories
```
find . -maxdepth 1 -type f | wc -l
```

#### Math pattern in big file and output in less
```
grep ie /usr/share/dict/words | less
```

#### Check if port is used by some app
netstat -nlp | grep 8080