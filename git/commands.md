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

# Show 5 records in oneline style with author pwebb and that were commited before Sat Aug 30
git log --oneline -5 --author pwebb --before "Sat Aug 30 2014"
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
# git reset works great for local branches
git reset HEAD^ <file>

# in order to reverse changes locally and remotely we can use git revert
# for that case we will recieve additional commit in the history
# and then can push it to remote branch, saving the overall history
git revert HEAD
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

### Relative refs (switching git objects)
```bash
# When you run git branch <branch>, how does Git know the SHA-1 of the last commit? The answer is the HEAD file.
# Usually the HEAD file is a symbolic reference to the branch you’re currently on. By symbolic reference, means that unlike a normal reference, it contains a pointer to another reference.
# However in some rare cases the HEAD file may contain the SHA-1 value of a git object. This happens when you checkout a tag, commit, or remote branch, which puts your repository in "detached HEAD" state.

# Moving upwards one commit at a time with ^
# main^ is equivalent to "the first parent of main"
# main^^ is the grandparent (second-generation ancestor) of main
git checkout main^

# We can do the same thing with HEAD link
git checkout HEAD^

# Move HEAD link back for 4 commits
git checkout HEAD~4

# Moving upwards a number of times with ~<num>
git checkout main ~<num>

# Branch forcing
# You can directly reassign a branch to a commit with the -f option.
# So here we reassign our main branch back to 3 commits in the commit graph
git branch -f main HEAD~3
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
# Flow: you have two branches main and hotfix
# and want to merge changes from hotfix to main
# Type command git megre hotfix, when you're currenty location is main branch
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
# --set-upstream sets the default remote branch for the current local branch
# when set-upstream added, user don't nee specify remote branch every time
# and push changes only with git push command
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

## Remote branches
```bash
# to see a full list of remote references use followin commands
git ls-remote <remote>
git remote show <remote>
```

### Origin is not special
```bash
# Just like the branch name “master” does not have any special meaning in Git,
# neither does “origin”. While “master” is the default name for a starting branch
# when you run git init which is the only reason it’s widely used, “origin” is the
# default name for a remote when you run git clone. If you run git clone -o booyah
# instead, then you will have booyah/master as your default remote branch
git clone
git clone -o booyah
```

### Pushing
```bash
# Your local branches aren’t automatically synchronized to the remotes 
# you write to — you have to explicitly push the branches you want to share
# for example if you have local branch serverfix, and want to add/update it 
# to remote branches, use command like git push <remote> <branch>
git push origin serverfix
```

### Tracking branches
```bash
# [Important] When you do a fetch that brings down new remote-tracking branches,
# you don’t automatically have local, editable copies of them. In other words, in this case, you don’t
# have a new serverfix branch — you have only an origin/serverfix pointer that you can’t modify.
git fetch origin

# To merge this work into your current working branch, you can run git merge origin/serverfix. If
# you want your own serverfix branch that you can work on, you can base it off your remote-
# tracking branch:
git checkout -b serverfix origin/serverfix

# Or do the same thing but with git --track flag
git checkout --track origin/serverfix

# If you already have a local branch and want to set it to a remote branch you just pulled down, or
# want to change the upstream branch you’re tracking, you can use the -u or --set-upstream-to
# option to git branch to explicitly set it at any time
git branch -u origin/serverfix

# To see what tracking branches you have set up, you can use the -vv option to git branch
git branch -vv

# If you want totally up to date ahead and behind numbers, you’ll need to fetch from
# all your remotes right before running this. You could do that like this:
git fetch --all; git branch -vv
```

### Deleting Remote Branches
```bash
git push origin --delete <branchname>
```

## Rebasing
```bash
# With the rebase command, you can take all the changes that were 
# committed on one branch and replay them on a different branch.
# for example, you would check out the <branch>, and then rebase it onto the master:
# Flow: you have two branches main and hotfix
# and want to rebase changes from hotfix to main
# Type command git rebase main, when you're currenty location is hotfix branch git checkout <branch>
git rebase master
```

## Cherry pick
```bash
# cherry-pick straightforward way to copy a series of commits to your current location (HEAD).

# You need to switch to the branch you want to cherry pick commits
# For example git switch main 
git cherry-pick <commit-hash> 

# or several commits
git cherry-pick <commit-hash1> <commit-hash2> <...>

# if you want to change commit message for commit that you want to copy, use command like
git cherry-pick <commit-hash> -edit

# if you dont want to add cherry picked commit to commit history you can add --no-commit option
# with this option all changes that was in cherry picked commit will be added to your working directory 
git cherry-pick <commit-hash> --no-commit
```

# Git on the Server
