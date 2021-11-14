### * wildcard (0 or more char)
```bash
# * wildcard matches on zero or more characters
# command to list only with png extention
ls *.png

# one way to list all the JPEG files
ls *.jpg *.jpeg`
# and here is another:
ls *.jp*g

```

### ? wildcard (1 char)
```bash
# ? wildcard represents a single character
# if the current directory contains files named 0001.jpg, 0002.jpg, 
# and so on through 0009.jpg, the following command lists them all
ls 000?.jpg
```

### [] wildcard (filtering)
```bash
# another way to use wildcards to filter output is to use [], 
# which denote groups of characters 
# following command lists all the files in the current directory 
# whose names contain a period immediately followed a lowercase J or P. 
ls *.[jp]*

# in Linux, file names and the commands that operate upon them are case-sensitive. 
# to match all file need to specify chars in upper and lower case
ls *.[jpJP]*
```

### [-] wildcard (ranges)
```bash
# expressions in square brackets can represent ranges of characters. 
# following command lists all the files in the current directory whose names begin with a lowercase letter:
ls [a-z]*

# by contrast, lists all the files in the current directory whose names begin with an uppercase letter:
ls [A-Z]*

# lists all the files in the current directory whose names begin with a lowercase or uppercase letter:
ls [a-zA-Z]*

# following commands lists all files when one or more numbers at the end\center\start of filename
ls [0-9]*
ls *[0-9]*
ls *[0-9]
```

### \ wildcard (escape)
```bash
# when need to use one of the wildcard characters as an ordinary character, you make it literal or "escape it" 
# by prefacing it with a backslash.
$ ls *\**
```
