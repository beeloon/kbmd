## Clone repo from remote source
```bash
git clone https://github.com/test.git
git clone https://github.com/test.git TEST_REPO
```

## Checking the status of files
```bash
git status

# short status
git status -s 
```

##  Tracking new files
```bash
git add .
git add README
git add frontend/*.json
```

## Viewing Staged and Unstaged Changes
```bash
git diff 

# see staged files that will go into your next commit
git diff --staged 
```

## Committing Changes
```bash
# will open the default terminal for passing commit msg
git commit

# commit with message
git commit -m "Story 182: fix benchmarks for speed"

# skip staging (git add) and commit all files permanently
git commit -a -m 'Add new benchmarks'
```

## Removing Files
```bash
# remove file from staging
# use git rm cause it will remove it from git tracked files
git rm README.md
```

## Moving Files
```bash
git mv file_from file_to

# will be equivalent to:
mv README.md README
git rm README.md
git add README
```

## Viewing the Commit History
```bash
# view all history
git log

# will show history of last 3 commits
git log -3

# will show the difference introduced in each commit (full --patch)
git log -p

# will show abbreviated stats for each commit
git log --stat

# will show formatted output, values: [oneline, short, full, fuller]
git log --pretty=oneline

# will format according to specifier table (look at './git log --pretty specifiers.md')
# output example: 9e41dc9 - Bohdan Bilyk, 3 weeks ago : initial commit
git log --pretty=format:"%h - %an, %ar : %s"

# will show formatted branch and merge history output like graph
git log --pretty=format:"%h %s" --graph
```
## Limiting Log Output

# 44