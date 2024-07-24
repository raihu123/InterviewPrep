### This is a Quick guide for Git

Most things here will be commands Mainly ordered by most commonly used by me. 

#### When working with branches and commits
- `git checkout <branch-name>` (switch branches)
- `git branch <branch-name>`(create a new branch at the current commit)
- `git branch` (Shows all the current branches in local maching chache)
  - Typical branch is standard I follow is `<feature-name>-<jira-ticket-id>`
- `git commit -m "<your-message-here>"` (commit your staged content as a new commit snapshot)
  - exmaple : `git commit -m "-- Changed x, y, and z in file-name.java"`
  - sometimes it better to use `git commit -a`
- `git push <alias> <branch>` exmaple : `git push origin xyz`
- `git merge <name-of-the-branch>` (merge a remote branch into your current branch to bring it up to date)
- `git pull <alias> <branch>`

#### General but commonly used
- `git status` (Shows what is in stagged or what is not)
- `git fetch` (fetches all the current brach in git remote)
- `git log`

#### Stashing
- `git stash` *I use this mainly for switching branches without staging changes*
- `git stash list`
- `git stash pop`(write working from top of stash stack)
- `git stash drop`

#### Initializing a git repo
- Create a blank repo in your Git Remote Repo
- `git init` (Initializes the git Simply creates the `.git` folder)
- `git remote add <alias(typically use origin)>`<url>` (add a git URL as an alias)
or clonig
-  `git clone <url>`

#### Not commonly Used by me
- `git reset <file>` (unstage a file while retaining the changes in working directory)
- `git rebase <branch>` It merges but by rewritting history TODO: Need a compartive example between rebase and merge

### Git submodule


