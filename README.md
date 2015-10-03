# git-update #

Smarter git-pull. Inspired by, and mostly cribbed from, [git-smart]. But, you
know, in shell. Because.

[git-smart]: https://github.com/geelen/git-smart/blob/master/lib/commands/smart-pull.rb

## Installation ##

git-update can easily be installed with homebrew:

```
brew tap gfontenot/formulae
brew install git-update
```

## Usage ##

git-update will perform the following actions when pulling:

 - Stash local changes if they exist, popping the stash after the pull is
   complete
 - Perform a fast-forward merge if the local branch hasn't moved on
 - Perform a `rebase -p` on top of the remote branch if there are new local
   changes
 - Display a paged git log of the pulled changes

The git log will use a custom log format if you've defined `pretty.update` in
your gitconfig. If you haven't set a custom format, it will use the following:

```
%C(yellow)%h%Cblue%d%Creset %s - %C(white)%an %Cgreen(%cr)%Creset
```

This outputs a log formatted like so:

![](https://files.app.net/24s27H0jx.png)

This prints the log like so:

    <SHA> <Commit Message> - <Author> (<Relative Date>)
