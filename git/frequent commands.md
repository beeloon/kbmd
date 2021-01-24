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

# 39