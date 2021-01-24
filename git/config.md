## git config
##### check configuration settings
```bash
git config --list 
```

##### view local and global setting
```bash
git config --list --show-origin
```

##### add/change name and mail in config file 
```bash
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
```

##### view user name
```bash
git config user.name
```

##### add/change default editor
```bash
git config --global core.editor code
```

##### add/change default branch name
```bash
git config --global init.defaultBranch main
```