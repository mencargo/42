# SSH (~/.ssh)
Generate keys with `ssh-keygen` with optional `-t <algorithm> -b <size>`, default is __\<rsa\>__

Public key should be at `~/.ssh/id_rsa.pub`

# GIT (repo/.git)

`git init` initializes a local repository (creates a .git folder with initial config)

`git remote add origin <url>` set's a remote repository url

`git push --set-upstream origin master` will push your staged files to the remote repo

If the repository has already been created remotely, you can just clone it, and it will already have all basic config for a push:

`git clone <url> <new_folder>`

`git commit -a -m "message"` will add and commit ANY modified files that have already been added to the repository

### .gitignore
Useful stuff to ignore in most excercises, use with caution!
```
.*
*.out
*.pdf
```

In most excercises you could include `main.c` and/or `*.sh`

### force stuff:
`git add -f main.c` an excercise that asks for a whole program

`git rm -f <wrong_file>` could be __\<folder\>__ with __-rf__

`git checkout master -f <file>` could be the entire repo without __\<file\>__
 
 `git remote set-url origin <url>` changes an existing remote repository url
 
 Completely messed up a local repo and want to start over? Could try `rm -rf .git` in the root repository folder

### check stuff:
`git status` pay attention to the messages
 
`git log` check that your __HEAD__ is in the same commit as __origin/master__

`git ls-files` list of commited files
 
`git diff-tree --no-commit-id --name-only -r <commit-hash>` list of files staged at a specific commit
 
 
# ZSH (~/.zshrc)
```
export VISUAL=vim
export EDITOR=vim
export PATH=$PATH:$HOME/bin:$HOME/
setopt SHARE_HISTORY             # Share history between all sessions.
setopt HIST_EXPIRE_DUPS_FIRST    # Expire a duplicate event first when trimming history.
setopt HIST_IGNORE_DUPS          # Do not record an event that was just recorded again.
setopt HIST_IGNORE_ALL_DUPS      # Delete an old recorded event if a new event is a duplicate.
setopt HIST_FIND_NO_DUPS         # Do not display a previously found event.
setopt HIST_IGNORE_SPACE         # Do not record an event starting with a space.
setopt HIST_SAVE_NO_DUPS         # Do not write a duplicate event to the history file.
setopt HIST_VERIFY               # Do not execute immediately upon history expansion.
export HISTSIZE=100              # Maximum events for internal history
export SAVEHIST=100              # Maximum events in history file

autoload -U colors
colors

# Load completions for Ruby, Git, etc.
autoload -U compinit
compinit

alias cc="gcc -Wall -Werror -Wextra *.c && ./a.out"
alias norm="norminette -R CheckForbiddenSourceHeader ."
```

# VIM (~/.vimrc)
```
set history=500
set autoread
set ruler
set incsearch
set showmatch
set number
set foldcolumn=1
set list
set listchars=tab:\ \ ┊
syntax	enable
```

Also available at `~/.myvimrc` in exam
