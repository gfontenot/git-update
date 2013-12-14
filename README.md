# git-update #

Smarter git-pull. Inspired by, and mostly cribbed from, [git-smart](https://github.com/geelen/git-smart/blob/master/lib/commands/smart-pull.rb). But, you know, in shell. Because.

## Usage ##

git-update will perform the following actions when pulling:

 - Stash local changes if they exist, popping the stash after the pull is
   complete
 - Perform a fast-forward merge if the local branch hasn't moved on
 - Perform a rebase -p on top of the remote branch if there are new local
   changes
 - Display a paged git log of the pulled changes

The git log uses a custom log format that you can define inside your
gitconfig. For example, here's mine:

```
[pretty]
  custom = %C(yellow)%h%Cblue%d%Creset %s - %C(white)%an %Cgreen(%cr)%Creset
```

This prints the log like so:

    <SHA> <Commit Message> - <Author> (<Relative Date>)
