# Git basics
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
```bash
# will show history of last 3 commits
git log -3

# This command works with lots of formats — you can specify 
# a specific date like "2008-01-15", or a
# relative date such as "2 years 1 day 3 minutes ago"
git log --since=2.weeks
git log --after=2.weeks


# will show logs bt author
git log --author="Bohdan"

# will show logs that contain keyword matched in grep
git log --grep="initial commit"

# takes a string and shows only those commits 
# that changed the number of occurrences of that
# if you wanted to find the last commit that 
# added or removed a reference to a specific function string
git log -S function_name

# will show only the files in specified directory/file
git log -- path/to/file


# Here's limiting log example
git log --pretty="%h - %s" --author='Junio C Hamano' --since="2008-10-01" \
--before="2008-11-01" --no-merges -- t/
```

## Undoing Things
```bash
# Only amend commits that are still local and have not been pushed somewhere.
# Example, if you commit and then realize you forgot to stage the changes
# in a file you wanted to add to this commit, you can do something like this:
git commit -m 'Initial commit'
git add forgotten_file
git commit --amend
```

## Unstaging a Staged File
```bash
# will unstage file 
git reset HEAD <file>
```

## Unmodifying a Modified File
```bash
# will revert file back to what it looked like in last commit
git checkout -- <file>
```

## Undoing things with git restore (from version 2.25)
```bash
# Unstaging a Staged File with git restore
git restore --staged <file>

# Unmodifying a Modified File with git restore
git restore <file>
```

## Showing Your Remotes
```bash
# show which remote servers were configured 
git remote

# show URLs that Git has stored for the shortname to be used
# when reading and writing to that remote
git remote -v
```

## Adding Remote Repositories
```bash
# add new remote git repo with remote add <shortname> <url>
git remote add pb https://github.com/paulboone/ticgit
```

## Fetching and Pulling from Remotes
```bash
# fetch all source from remote repo
git fetch 
git fetch <remote>

# fetch all source from remote repo and merge it
git pull 
git pull <remote>
```

## Pushing to Your Remotes
```bash
# push all changes in local repo to 
# remote repo origin in the master branch
git push origin master
```

## Inspecting a Remote
```bash
# show info about remote origin repo
git remote show origin
```

## Renaming and Removing Remotes
```bash
# will rename remote origin repo to o
git remote rename origin o

# these commands will remove remote repo link from local repo
git remote remove <remote>
git remote remove origin
git remote rm origin
```

# 62