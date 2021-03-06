# 42 cheat sheet

The basics to start swimmig, written as a reference guide with some useful stuff for the code pool

# ZSH (~/.zshrc)

```
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

export VISUAL=vim
export EDITOR=vim
export PATH=$PATH:$HOME/bin:$HOME/.local/bin

alias francinette=$HOME/francinette/tester.sh
alias paco=$HOME/francinette/tester.sh
alias cc="gcc -Wall -Werror -Wextra *.c && ./a.out"
```

# BASH (~/.bashrc)

```
# Simple git prompt
COLOR_GIT_CLEAN='\[\033[1;30m\]'
COLOR_GIT_MODIFIED='\[\033[0;33m\]'
COLOR_GIT_STAGED='\[\033[0;36m\]'
COLOR_RESET='\[\033[0m\]'

function git_prompt() {
  if git rev-parse --is-inside-work-tree > /dev/null 2>&1; then
    branch_name=$(git symbolic-ref -q HEAD)
    branch_name=${branch_name##refs/heads/}
    branch_name=${branch_name:-HEAD}
    echo -n " → "
    if [[ $(git status 2> /dev/null | tail -n1) = *"nothing to commit"* ]]; then
      echo -n "$COLOR_GIT_CLEAN$branch_name$COLOR_RESET"
    elif [[ $(git status 2> /dev/null | head -n5) = *"Changes to be committed"* ]]; then
      echo -n "$COLOR_GIT_STAGED$branch_name$COLOR_RESET"
    else
      echo -n "$COLOR_GIT_MODIFIED$branch_name*$COLOR_RESET"
    fi
  fi
}

function prompt() {
  PS1="\u@\h [\w$(git_prompt)] \$ "
}

PROMPT_COMMAND=prompt

export VISUAL=vim
export EDITOR=vim
export PATH=$PATH:$HOME/bin:$HOME/.local/bin

alias francinette=$HOME/francinette/tester.sh
alias paco=$HOME/francinette/tester.sh
alias cc="gcc -Wall -Werror -Wextra *.c && ./a.out"
```

# VIM (~/.vimrc)

```
set history=500
set autoread
set autoindent
set smartindent
set tabstop=4
set shiftwidth=4
set ruler
set incsearch
set showmatch
set number
set foldcolumn=1
set list
set listchars=tab:\ \ ›,nbsp:·,trail:·
set laststatus=2
syntax enable
highlight SpecialKey ctermfg=darkgray guifg=darkgray
let g:user42 = '42login'
let g:mail42 = '42login@student.42xxxx'
```

Also available at `~/.myvimrc` in an exam, so memorize `syntax enable`

# SSH (~/.ssh)

Generate keys with `ssh-keygen`, the public key should be at `~/.ssh/id_rsa.pub`

# GIT (~/src/repo/.git)

Upload an existing project to a remote repository, go inside your project's root folder and:

```
git init
git remote add origin <url>
git add <files>
git commit -m "<message>"
git push --set-upstream origin master
```

Start a new project from a remote repository just `git clone <url> <new_folder>`

Go into the `<new_folder>`, do your thing, then `git add <files>`, `git commit -m "<message>"` and `git push`

# Norminette

Follow the installation [guide](https://github.com/42School/norminette)

You need to have python's [pip](https://pip.pypa.io/en/stable/installation/)

And don't forget to update your $**PATH**

Use `~/.zshrc` to have it every session

To add the header [plugin](https://github.com/42Paris/42header) for VIM, basically copy the [stdheader.vim](https://raw.githubusercontent.com/42Paris/42header/master/plugin/stdheader.vim) file to `~/.vim/plugin/stdheader.vim`, like:

```
mkdir -p ~/.vim/plugin
curl -o ~/.vim/plugin/stdheader.vim https://raw.githubusercontent.com/42Paris/42header/master/plugin/stdheader.vim
```

And add the following lines to your `~/.vimrc` (with your 42 login user and email):

```
let g:user42 = '42login'
let g:mail42 = '42login@student.42xxxx'
```

Note: You may need to install libbsd and compile with -lbsd flag to use bsb functions like strlcat and such...

## Git stuff:

### ~/src/repo/.gitignore
```
.*
*.out
*.o
*.a
```

Depending on the project you could add to the list: `main.c`, `*.sh`, `*.pdf`...

Check the [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf) from GitHub.

### Add stuff:

`git add -f .gitignore` to force adding a file even if it's on the ignore rules

`git add --all` add all files from all paths within your repository (follows ignore rules)

`git add .` add all files from the current folder (also follows ignore rules)

`git commit -a -m "<message>"` will add and commit ANY modified files that have already been added to the repository

### Remove stuff:

`git rm -rf <wrong_file/folder>` careful, it's a single command to remove, stage, commit and push

Completely revert lastest commit:
```
git reset --hard HEAD^
git push origin -f
```

`git checkout master -f <file>` revert changes to match the current commit, could be the entire repo without `<file>`

`git remote set-url origin <url>` changes an existing remote repository `<url>`

Completely messed up a local repo and want to start over?

Could try `rm -rf .git` in the root repository folder

### Check stuff:

`git status` pay attention to the messages
 
`git log` check that your __HEAD__ is in the same commit as __origin/master__

`git ls-files` list of staged files (not necessarily pushed!)

`git diff <file>` see the current changes, checks all files if you don't specify some

`git diff-tree --no-commit-id --name-only -r <commit-hash>` list of files staged at a specific commit

`git checkout <commit hash>` go to a specific commit (get the hash from the git log)

`git checkout master` go to the latest commit
