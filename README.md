# ZSH (~/.zshrc)
```
export VISUAL=vim
export EDITOR=vim
export PATH=$PATH:$HOME/bin:$HOME/.local/bin
setopt SHARE_HISTORY
setopt HIST_EXPIRE_DUPS_FIRST
setopt HIST_IGNORE_DUPS
setopt HIST_IGNORE_ALL_DUPS
setopt HIST_FIND_NO_DUPS
setopt HIST_IGNORE_SPACE
setopt HIST_SAVE_NO_DUPS
setopt HIST_VERIFY
export HISTSIZE=100
export SAVEHIST=100

autoload -U colors
colors

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
set tabstop=4
set list
set listchars=tab:\ \ ┊
syntax enable
```

Also available at `~/.myvimrc` in an exam, so memorize `syntax enable`

# SSH (~/.ssh)
Generate keys with `ssh-keygen`

Public key should be at `~/.ssh/id_rsa.pub`

# GIT (~/src/repo/.git)

Upload an existing project to a remote repository.
Inside your project's root folder:

```
git init
git remote add origin <url>
git add -A
git commit -m "<message>"
git push --set-upstream origin master
```

Start a new project from a remote repository:

`git clone <url> <new_folder>`

Go into the \<new_folder\>, do your thing, then:
`git add <files>`, `git commit -m "<message>"` and `git push`

# Norminette

Follow the installation [guide](https://github.com/42School/norminette)

You need to have python's [pip](https://pip.pypa.io/en/stable/installation/)

And don't forget to update your $**PATH**

Use `~/.zshrc` to have it every session

## Git stuff:

### ~/src/repo/.gitignore
```
.*
*.out
```

Depending on the project you could add to the list: `main.c`, `*.sh`, `*.pdf`...

### force git stuff:
`git add -f main.c` to force adding a file even if it's on the ignore rules

`git commit -a -m "<message>"` will add and commit ANY modified files that have already been added to the repository

`git rm -f <wrong_file>` could be __\<folder\>__ with __-rf__

`git checkout master -f <file>` could be the entire repo without __\<file\>__
 
`git remote set-url origin <url>` changes an existing remote repository url
 
Completely messed up a local repo and want to start over?

Could try `rm -rf .git` in the root repository folder

### check stuff:
`git status` pay attention to the messages
 
`git log` check that your __HEAD__ is in the same commit as __origin/master__

`git ls-files` list of commited files
 
`git diff-tree --no-commit-id --name-only -r <commit-hash>` list of files staged at a specific commit
