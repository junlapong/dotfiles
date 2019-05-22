# my dot files

## .bash_profile

```bash
export PATH="/usr/local/sbin:$PATH"
export CLICOLOR=1
export GREP_OPTIONS='--color=auto' GREP_COLOR='1;32'

git_branch () { git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/\1/'; }

TIME='\033[01;33m\]\t \033[01;32m\]'
HOST='\033[01;36m\]\H'; HOST='@'$HOST
LOCATION=' \033[02;34m\]\W'
BRANCH=' \033[02;36m\]$(git_branch)\[\033[00m\]\n\$ '

#PS1="\u@\H \W$ "
PS1=$TIME$USER$HOST$LOCATION$BRANCH
#PS2='\[\033[01;36m\]>'

source ~/.bashrc
```

## .bashrc

```bash
if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi

# Git
alias ga="git add"
alias gc="git commit"
alias gd="git diff"
alias gp="git push"
alias gpl="git pull"
alias gst="git status"

# Go development
export GOPATH="${HOME}/.go"
export GOROOT="$(brew --prefix golang)/libexec"
export PATH="$PATH:${GOPATH}/bin:${GOROOT}/bin"
#test -d "${GOPATH}" || mkdir "${GOPATH}"

# NVM
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```

## .tmux.conf

```bash
# Pane Splitting
unbind %
unbind '"'
bind | split-window -h
bind - split-window -v

# Toggle sending keystrokes to all panes in a window
bind x setw synchronize-panes

# Make mouse useful in copy mode
set -g mouse on

# Scroll History
set -g history-limit 30000

# Set ability to capture on start and restore on exit window data when running an application
setw -g alternate-screen on

# Lower escape timing from 500ms to 50ms for quicker response to scroll-buffer access.
set -s escape-time 50
```

## .vimrc

```bash
syntax on
```

## .zshrc

```bash
# If you come from bash you might have to change your $PATH.
# export PATH=$HOME/bin:/usr/local/bin:$PATH

export TERM="xterm-256color"

# Path to your oh-my-zsh installation.
export ZSH=/Users/junlapong/.oh-my-zsh

# Set name of the theme to load. Optionally, if you set this to "random"
# it'll load a random theme each time that oh-my-zsh is loaded.
# See https://github.com/robbyrussell/oh-my-zsh/wiki/Themes

#ZSH_THEME="robbyrussell"
ZSH_THEME="powerlevel9k/powerlevel9k"

#POWERLEVEL9K_MODE='awesome-patched'
# Disable dir/git icons
POWERLEVEL9K_HOME_ICON=''
POWERLEVEL9K_HOME_SUB_ICON=''
POWERLEVEL9K_FOLDER_ICON=''
#DISABLE_AUTO_TITLE="true"

POWERLEVEL9K_VCS_GIT_ICON=''
POWERLEVEL9K_VCS_STAGED_ICON='\u00b1'
POWERLEVEL9K_VCS_UNTRACKED_ICON='\u25CF'
POWERLEVEL9K_VCS_UNSTAGED_ICON='\u00b1'
POWERLEVEL9K_VCS_INCOMING_CHANGES_ICON='\u2193'
POWERLEVEL9K_VCS_OUTGOING_CHANGES_ICON='\u2191'
POWERLEVEL9K_VCS_MODIFIED_BACKGROUND='yellow'
POWERLEVEL9K_VCS_UNTRACKED_BACKGROUND='yellow'

POWERLEVEL9K_LEFT_PROMPT_ELEMENTS=(time root_indicator dir vcs)
POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS=(status rbenv)
POWERLEVEL9K_SHORTEN_DIR_LENGTH=1

plugins=(git zsh-autosuggestions)
source $ZSH/oh-my-zsh.sh

# User configuration

#source ~/.bash_profile
source ~/.bashrc
source /usr/local/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
```