---
title: Git Productivity Tips
slug: git-productivity-tips
date_published: 2017-10-26T13:12:00.000Z
date_updated: 2021-02-22T17:18:10.000Z
tags: Productivity
excerpt: Git definitely has a learning curve if you're new to programming. I've collected some quick tips to help you become more productive, sooner.
---

For someone just starting to learn how to code, throwing Git in to the mix can cause a lot of extra confusion and strain. Git is an essential tool for developers though and one that most developers only reach a baseline level of proficiency with. It makes sense: Git can sometimes feel cumbersome to work with in a way that feels like a hindrance to your productivity. The following are a few tips to help make it easier to become productive in Git:

## Commit often

Think of making a commit as crossing of an item on your to do list. Each item should be discrete and reasonably sized. “Build the app” is not a good item for your to do list and neither is it a good commit. “Restyle the page header” is more appropriate in size.

This will be for your own sanity and as a favor for those you work with. If you find out later that a commit introduced a bug, it’ll be relatively easy to track down which commit it was. If each commit represents a distinct task, it will be easy to find where in particular the bug was introduced. If your commit is to the tune of [“draw the rest of the owl”](https://imgur.com/rCr9A), then you could be sifting through changes for a while before you find the bug.

I also believe that committing more often makes you more productive by forcing you to focus on each specific task one at a time until it’s complete, though I don’t have data or evidence to back this up.

## Create a commit template

If you’re committing more often, then you’ll need to write a message to accompany each commit. You can make writing a good commit message easier by using a template. Doing so is really easy, just define a `~/.gitmessage.txt` at the root of your user and configure Git to use it with:

    git config  — global commit.template ~/.gitmessage.txt

What should go in your commit template? You want your commit messages to be succinct and descriptive. For that, I recommend a prompt that will help start your commit messages:

    # If applied, this commit will...

A little research will uncover a couple of common commit templates, but the above is the simplest and most appropriate for a beginner. You want to write your commits in an imperative style and provide a one sentence description of what each commit is contributing to the codebase. Answering the above prompt will help you do so.

## Alias commands

When I started trying to get in to the habit of committing more often, one of the barriers was how long it took to make a single commit. The first step to making it easier was to alias common git commands (like staging and committing) to just a few characters.

Aliasing commands in Git is very easy to do. If you run the following in your terminal, then you will create an alias for `checkout`. Going forward, you’ll just have to type `co`.

    git config — global alias.co checkout

All of your aliases will be stored in your `~/.gitconfig`. My `.gitconfig` has the following aliases, which you can use as a starting point:

    s = status
    a = add
    c = commit
    co = checkout
    b = branch
    pl = pull
    psh = push
    m = merge

Coupled with [auto-completion](https://git-scm.com/book/en/v1/Git-Basics-Tips-and-Tricks), aliases make git commands shorter and easier to write. Staging changes is as simple at `git a .` and I can follow it up with `git c` to commit my work.

The above aliases will suit most users well, but if you want to take this one step further you can alias common git commands in your `.bash_profile`. I also use these aliases:

    alias g='git'
    alias stash='git add . && git stash'
    alias gam='git add . && git commit'
    alias gs='git status'
    alias gb='git branch'
    alias gl='git log — pretty=format:”%h — %an, %ar : %s” -15'
    alias gr='git remote -v'

The aliases I use most frequently are `gam`, `gs` and `gl`. They make common actions in Git very quick to execute but I still have to switch from my editor to the terminal to run them. So, as an additional approach, consider using an editor integration.

## Use an editor integration

The last tip I’ll offer is to use an editor integration for Git. Atom and VSCode ship with Git integrations by default and you can download and set one up for both [Vim](https://github.com/tpope/vim-fugitive) and [Sublime Text](https://github.com/kemayo/sublime-text-git). Once your editor integration is installed and configured, you’ll be able to work with Git without ever having to leave the comfort of your editor.

Additionally, most editor integrations also come with a set of short commands that you can learn. Memorizing the short commands will make regular commits second nature and as easy as hitting a few keys.

## Conclusion

I use a combination of the above when working on a project. Most commits I’ll make from my editor, because I can work through my to do list making changes and committing them all from within Vim. If I need to switch branches and merge or push my work, then I’ll switch back to the terminal to do so because it usually means I’m finishing up what ever I’m working on and will be switching to something else.

I highly recommend working towards becoming productive in Git to all junior and aspiring developers. If you’re working towards your first job, it will help during the interview process to already have good habits for working with Git; if you are in your first job as a developer, being fluent with Git will make you a more productive member of the team.

If you found this helpful, please consider sharing it. If you have other ideas or suggestions on becoming more productive with Git, please add them as comments below.
