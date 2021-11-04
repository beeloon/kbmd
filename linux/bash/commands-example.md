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