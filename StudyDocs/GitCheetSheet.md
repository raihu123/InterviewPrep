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

#### When reverting/working with a previous commit
- `git revert <commit-hash>` If you want to undo changes without losing history. (then add changes to staging and then commit)
or
- `git reset <commit-hash>` If you want to discard changes and possibly rewrite history.
  - `git reset --soft <commit-hash>` Moves the branch pointer to a previous commit but keeps changes in the staging area and working directory.
  - `git reset --mixed <commit-hash>` Moves the branch pointer and resets the index, but keeps changes in the working directory.
  - `git reset --hard <commit-hash>` To reset the branch to a specific commit and discard all changes made after that commit
or
- `git checkout <commit-hash>` If you just want to view or temporarily work with a previous commit.

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
- `git submodule update --init --recursive`
- `git submodule add <url> <repo-name>`
- `git commit -m "submodule added"`
- sometimes it does not create the modules properly might need to add `.gitmodules` file
- `touch .gitmodules`
 ```text
[submodule "JavaPractice"]
path = JavaPractice
url = https://github.com/raihu123/JavaPractice.git
```

### Git Ignore file
- `touch .gitignore`
```cli
logs/
*.notes
pattern*/
```

 ### Merge vs Rebase in Git: Easy Understanding

**Merge:**
- **Combines** the history of two branches.
- Creates a **merge commit**.
- Keeps the branch history intact.

**Example:**
```sh
# Start on feature branch
git checkout feature

# Merge changes from main branch into feature
git merge main
```
- Result: The feature branch now has a merge commit that combines changes from both branches.

**Rebase:**
- **Reapplies** your changes on top of another branch.
- **Rewrites** commit history.
- Creates a **linear history**.

**Example:**
```sh
# Start on feature branch
git checkout feature

# Rebase feature branch onto main
git rebase main
```
- Result: The feature branch commits are moved to the top of the main branch history, creating a straight line of commits.

### Visual Example:
**Before Merge/Rebase:**
```
main:    A---B---C
            \
feature:     D---E
```

**After Merge:**
```
main:    A---B---C
            \     \
feature:     D---E---M (M = merge commit)
```

**After Rebase:**
```
main:    A---B---C---D'---E' (D' and E' are rebased commits)
```

### Summary:
- **Merge**: Keeps history, creates a merge commit.
- **Rebase**: Linear history, no merge commit, rewrites commits.

