# Git Autocomplete and Prompt:
This document explains how to add git auto-completion and show your current branch on your bash/terminal. 

## Autocomplete:
This enables git to autocomplete branch, origin names etc. for you when you press `<tab>`. Follow the following steps to enable this:
- place the auto-complete helper bash file `.git-completion.bash` in your home directory
- we need to load this file (source this file) every time a bash environment is loaded. To do this, add the following lines to your `.bashrc` file in your linux home directory or `.bash_profile` file in your OSX home directory.
```
# adding the git autocompletion file
if [ -f ~/.git-completion.bash ]; then
   source ~/.git-completion.bash
fi
```
- run `source ~/.bashrc` on linux or `source ~/.bash_profile` on OSX.
- try by going to an existing git project and do `git checkout m<tab>`, you should see `master` suggested for autocompletion!

## Git Prompt
This enables you to see your current git branch, rebase status, merging status etc. on your bash prompt. Follow the following steps to enable this:
- place the prompt helper bash file `.git-prompt.sh` in your home directory
- we need to load this file (source this file) every time a bash environment is loaded. To do this, add the following lines to your `.bashrc` file in your linux home directory or `.bash_profile` file in your OSX home directory. **NOTE:**
A `PS1` environment variable is used to determine the details that are going to be placed on your bash prompt. e.g. a default `PS1` might look like `'\u@\h$ '`. We need to modify this PS1 to call __git_ps1 as command-substitution: `$(__git_ps1 " (%s)")`. Depending 
on how you structure your `PS1`, a sample final `PS1` might end up looking like `'\u@\h $(__git_ps1 "(%s)")$ '`.
```
# adding the git-prompt.sh file for showing current branch
if [ -f ~/.git-prompt.sh ]; then
   source ~/.git-prompt.sh
   export PS1='\u@\h $(__git_ps1 "(%s)")$ '
fi
```
- run `source ~/.bashrc` on linux or `source ~/.bash_profile` on OSX.
- try by going to an existing git project you should see your branch listed on your bash prompt!