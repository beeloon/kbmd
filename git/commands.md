# Git basics

## Getting a Git Repository
```bash
git clone https://github.com/test.git
git clone https://github.com/test.git TEST_REPO
```

## Recording Changes to the Repository
### Checking the status of files
```bash
git status

# short status
git status -s 
```

###  Tracking new files
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

### Committing Changes
```bash
# will open the default terminal for passing commit msg
git commit

# commit with message
git commit -m "Story 182: fix benchmarks for speed"

# skip staging (git add) and commit all files permanently
git commit -a -m 'Add new benchmarks'
```

### Removing Files
```bash
# remove file from staging
# use git rm cause it will remove it from git tracked files
git rm README.md
```

### Moving Files
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

### Limiting Log Output
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

### Unstaging a Staged File
```bash
# will unstage file 
git reset HEAD <file>
```

### Unmodifying a Modified File
```bash
# will revert file back to what it looked like in last commit
git checkout -- <file>
```

### Undoing things with git restore (from version 2.25)
```bash
# Unstaging a Staged File with git restore
git restore --staged <file>

# Unmodifying a Modified File with git restore
git restore <file>
```

## Working with remotes
### Showing Your Remotes
```bash
# show which remote servers were configured 
git remote

# show URLs that Git has stored for the shortname to be used
# when reading and writing to that remote
git remote -v
```

### Adding Remote Repositories
```bash
# add new remote git repo with remote add <shortname> <url>
git remote add pb https://github.com/paulboone/ticgit
```

### Fetching and Pulling from Remotes
```bash
# fetch all source from remote repo
git fetch 
git fetch <remote>

# fetch all source from remote repo and merge it
git pull 
git pull <remote>
```

### Pushing to Your Remotes
```bash
# push all changes in local repo to 
# remote repo origin in the master branch
git push origin master
```

### Inspecting a Remote
```bash
# show info about remote origin repo
git remote show origin
```

### Renaming and Removing Remotes
```bash
# will rename remote origin repo to o
git remote rename origin o

# these commands will remove remote repo link from local repo
git remote remove <remote>
git remote remove origin
git remote rm origin
```

## Tagging
```bash
# listing the existing tags
git tag

# list tags by pattern, if you want just list all yor[-l == --list]
git tag -l "v1.8.5*"
```

### Creating tags
#### Annotated Tags
```bash
# create annotated tag, where 
# -m specifies a message
# -a for creating annotated tag
git tag -a v1.4 -m 'my version 1.4'

# to see info about your tag enter
git show v1.4
```

#### Lightweight Tags
```bash
# to create light tag no need to pass another options
git tag v1.4-lw
```

### Tagging Later
```bash
# if you forget to add the tag to specific commit
# in the example 9fceb02 is the checksum of commit 
git tag -a v1.2 9fceb02
```

### Sharing tags
```bash
# certain tag
git push origin v1.5

# all your tags
git push origin --tags

# push all your annotated tags
git push origin --follow-tags
```

### Deleting Tags
```bash
# delete on local machine
git tag -d v1.4-lw

# for remote delete use one of the following command 
git push origin :refs/tags/<tagname>
git push origin --delete <tagname>
```

### Checking out Tags
```bash
git checkout v2.0.0
```

## Git Aliases

```bash
# to create new alias, you need add field to alias 
# object in global config file with command you need to be alias 
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status


# create more complex command
git config --global alias.unstage 'reset HEAD --'

# show last commit 
git config --global alias.last 'log -1 HEAD'
```

# Git branching
## Branches in nutshell
### Creating a New Branch
```bash
# if you want to create branch use git branch command 
git branch <branchname>
```

### Switching Branches
```bash
# to switch between branches use following commands\
git checkout <branchname>

# command will create and instantly switch to another branch
git checkout -b <branchname>

# from version 2.23 you can use switch command instead of checkout
git switch <branchname>

# use switch to instantly create and switch with branches
# -c flag stands for create, it full version is --create 
git switch -c <branchname>

# there commands will return to your previosly checked out branch
git checkout - 
git switch - 


# to see how history of your commits looks like with braches
# you can log commits with graph view like this
git log --oneline --decorate --graph --all
```

### Deleting Branches
```bash
# use following command to delete branch
git branch -d <branchname>

# for removing remote branch use
git push origin --delete <branchname>
```

### Basic Merging and Conflicts
```bash
# basic merge command
git merge <branchname> 

# use following command if you want use a graphical tool
# to resolve merging conflicts
git mergetool
```

## Branch Management
```bash
# list all of your branches
# * indecates your current branch
git branch

# if you want to see all local and remote branches use --all flag
git branch --all


# if you want to see the last commit on each branch use -v flag
git branch -v

# following command indicate branches that you have
# or not have merged in the branch you are currently in
git branch --merge
git branch --no-merge
# branch name is oprional, but you can always provide additional argument
git branch --merge <branchname>

# you can't delete not merged branch with -d flag
# but if you're sure about deletean branch and lose your work use -D
git branch -D <branchname>
```

### Changing a branch name
```bash
# locally change branch name
git branch --move <bad-branch-name> <corrected-branch-name>

# change name for remote branch
git push --set-upstream origin <corrected-branch-name>
git push origin --delete <bad-branch-name>
```

### Changing the master branch name
```bash
# Changing the name of a branch like master/main/mainline/default will break the
# integrations, services, helper utilities and build/release scripts that your repository
# uses. Before you do this, make sure you consult with your collaborators. Also make
# sure you do a thorough search through your repo and update any references to the
# old branch name in your code or scripts.
git branch --move master <branchname>

git push --set-upstream origin main

git push origin --delete master
```

## Branching Workflows
# 89
