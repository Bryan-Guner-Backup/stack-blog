---
title: Git Cheatsheet
weight: 0
excerpt: Why is looking at runtime not a reliable method of calculating time complexity?
seo:
    title: 'Git Cheatsheet'
    description: 'A Quick Guide to Git Cheatsheet'
    robots: []
    extra: []
template: docs
---

# Git-Tricks

Refs

---

### Awesome GitHub Commands Reference Sheet (Quick Reference)

    HEAD^       # 1 commit before head
    HEAD^^      # 2 commits before head
    HEAD~5      # 5 commits before head

### Branches

    # create a new branch
      git checkout -b $branchname
      git push origin $branchname --set-upstream

    # get a remote branch
      git fetch origin
      git checkout --track origin/$branchname

    # delete local remote-tracking branches (lol)
      git remote prune origin

    # list merged branches
      git branch -a --merged

    # delete remote branch
      git push origin :$branchname

    # go back to previous branch
      git checkout -

### Collaboration

    # Rebase your changes on top of the remote master
      git pull --rebase upstream master

    # Squash multiple commits into one for a cleaner git log
    # (on the following screen change the word pick to either 'f' or 's')
      git rebase -i $commit_ref

### Submodules

    # Import .gitmodules
      git submodule init

    # Clone missing submodules, and checkout commits
      git submodule update --init --recursive

    # Update remote URLs in .gitmodules
    # (Use when you changed remotes in submodules)
      git submodule sync

### Diff

### Diff with stats

    git diff --stat
    app/a.txt    | 2 +-
    app/b.txt    | 8 ++----
    2 files changed, 10 insertions(+), 84 deletions(-)

### Just filenames

    git diff --summary

### Log options

    --oneline
      e11e9f9 Commit message here

    --decorate
      shows "(origin/master)"

    --graph
      shows graph lines

    --date=relative
      "2 hours ago"

### Misc

### Cherry pick

    git rebase 76acada^

    # get current sha1 (?)
      git show-ref HEAD -s

    # show single commit info
      git log -1 f5a960b5

    # Go back up to root directory
      cd "$(git rev-parse --show-top-level)"

### Short log

    $ git shortlog
     $ git shortlog HEAD~20..    # last 20 commits

     James Dean (1):
         Commit here
         Commit there

     Frank Sinatra (5):
         Another commit
         This other commit

### Bisect

    git bisect start HEAD HEAD~6
    git bisect run npm test
    git checkout refs/bisect/bad   # this is where it screwed up
    git bisect reset

### Manual bisection

    git bisect start
    git bisect good   # current version is good

    git checkout HEAD~8
    npm test          # see if it's good
    git bisect bad    # current version is bad

    git bisect reset  # abort

### Searching

    git log --grep="fixes things"  # search in commit messages
    git log -S"window.alert"       # search in code
    git log -G"foo.*"              # search in code (regex)

### GPG Signing

    git config set user.signingkey <GPG KEY ID>       # Sets GPG key to use for signing

    git commit -m "Implement feature Y" --gpg-sign    # Or -S, GPG signs commit

    git config set commit.gpgsign true                # Sign commits by default
    git commit -m "Implement feature Y" --no-gpg-sign # Do not sign
    ---

### Refs

    HEAD^       # 1 commit before head
    HEAD^^      # 2 commits before head
    HEAD~5      # 5 commits before head

### Branches

    # create a new branch
      git checkout -b $branchname
      git push origin $branchname --set-upstream

    # get a remote branch
      git fetch origin
      git checkout --track origin/$branchname

    # delete local remote-tracking branches (lol)
      git remote prune origin

    # list merged branches
      git branch -a --merged

    # delete remote branch
      git push origin :$branchname

    # go back to previous branch
      git checkout -

### Collaboration

    # Rebase your changes on top of the remote master
      git pull --rebase upstream master

    # Squash multiple commits into one for a cleaner git log
    # (on the following screen change the word pick to either 'f' or 's')
      git rebase -i $commit_ref

### Submodules

    # Import .gitmodules
      git submodule init

    # Clone missing submodules, and checkout commits
      git submodule update --init --recursive

    # Update remote URLs in .gitmodules
    # (Use when you changed remotes in submodules)
      git submodule sync

### Diff

### Diff with stats

    git diff --stat
    app/a.txt    | 2 +-
    app/b.txt    | 8 ++----
    2 files changed, 10 insertions(+), 84 deletions(-)

### Just filenames

    git diff --summary

### Log options

    --oneline
      e11e9f9 Commit message here

    --decorate
      shows "(origin/master)"

    --graph
      shows graph lines

    --date=relative
      "2 hours ago"

### Miscellaneous

#### Cherry pick

    git rebase 76acada^

    # get current sha1 (?)
      git show-ref HEAD -s

    # show single commit info
      git log -1 f5a960b5

    # Go back up to root directory
      cd "$(git rev-parse --show-top-level)"

### Short log

    $ git shortlog
     $ git shortlog HEAD~20..    # last 20 commits

     James Dean (1):
         Commit here
         Commit there

     Frank Sinatra (5):
         Another commit
         This other commit

### Bisect

    git bisect start HEAD HEAD~6
    git bisect run npm test
    git checkout refs/bisect/bad   # this is where it screwed up
    git bisect reset

### Manual bisection

    git bisect start
    git bisect good   # current version is good

    git checkout HEAD~8
    npm test          # see if it's good
    git bisect bad    # current version is bad

    git bisect reset  # abort

### Searching

    git log --grep="fixes things"  # search in commit messages
    git log -S"window.alert"       # search in code
    git log -G"foo.*"              # search in code (regex)

### GPG Signing

    git config set user.signingkey <GPG KEY ID>       # Sets GPG key to use for signing

    git commit -m "Implement feature Y" --gpg-sign    # Or -S, GPG signs commit

    git config set commit.gpgsign true                # Sign commits by default
    git commit -m "Implement feature Y" --no-gpg-sign # Do not sign

<figure><img src="https://cdn-images-1.medium.com/max/800/1*yyaUC-O43Gs1qAVkdHrMdw.png" class="graf-image" /></figure>#### If you found this guide helpful feel free to checkout my github/gists where I host similar content:

<a href="https://gist.github.com/bgoonz" class="markup--anchor markup--p-anchor">bgoonz's gists · GitHub</a>

<a href="https://github.com/bgoonz" class="markup--anchor markup--mixtapeEmbed-anchor" title="https://github.com/bgoonz"><strong>bgoonz — Overview</strong>
<br/>

<em>Web Developer, Electrical Engineer JavaScript | CSS | Bootstrap | Python | React | Node.js | Express | Sequelize…</em>github.com</a><a href="https://github.com/bgoonz" class="js-mixtapeImage mixtapeImage u-ignoreBlock"></a>

Or Checkout my personal Resource Site:

<a href="https://bgoonzblog20master.gatsbyjs.io/docs/sitemap" class="markup--anchor markup--mixtapeEmbed-anchor" title="https://bgoonzblog20master.gatsbyjs.io/docs/sitemap"><strong>a/A-Student-Resources</strong>
<br/>

<em>Edit description</em>goofy-euclid-1cd736.netlify.app</a><a href="https://bgoonzblog20master.gatsbyjs.io/docs/sitemap" class="js-mixtapeImage mixtapeImage u-ignoreBlock"></a>

By <a href="https://medium.com/@bryanguner" class="p-author h-card">Bryan Guner</a> on [March 6, 2021](https://medium.com/p/57e8d0292285).

<a href="https://medium.com/@bryanguner/git-tricks-57e8d0292285" class="p-canonical">Canonical link</a>

August 6, 2021.
