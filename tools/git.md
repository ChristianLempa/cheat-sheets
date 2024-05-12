# Git Cheat-Sheet

## Repository Management

| Command | Description |
| --- | --- |
| `git init` | Initialize a new Git repository |
| `git clone <url>` | Clone a remote repository |
| `git status` | Show the working tree status |
| `git add <file>` | Add a file to the staging area |
| `git commit -m <message>` | Commit changes to the repository |
| `git push` | Push changes to the remote repository |
| `git pull` | Pull changes from the remote repository |
| `git fetch` | Fetch changes from the remote repository |
| `git merge <branch>` | Merge a branch into the current branch |
| `git branch` | List all branches |
| `git branch <branch>` | Create a new branch |
| `git checkout <branch>` | Switch to a branch |
| `git checkout -b <branch>` | Create and switch to a new branch |
| `git branch -d <branch>` | Delete a branch |
| `git log` | Show commit logs |
| `git diff` | Show changes between commits |
| `git blame <file>` | Show who changed each line in a file |
| `git reflog` | Show a log of changes to HEAD |
| `git reset --hard <commit>` | Reset the repository to a commit |
| `git revert <commit>` | Revert a commit |
| `git stash` | Stash changes in the working directory |
| `git stash pop` | Apply stashed changes to the working directory |
| `git tag <tag>` | Create a tag for a commit |

## Configuration

| Command | Description |
| --- | --- |
| `git config --global user.name <user>` | Set the user name for Git |
| `git config --global user.email <email>` | Set the user email for Git |
| `git config --global core.editor <editor>` | Set the default text editor for Git |
| `git config --global color.ui auto` | Enable colored output for Git |

## Remote Repositories

| Command | Description |
| --- | --- |
| `git remote add <repository> <url>` | Add a remote repository |
| `git remote -v` | List remote repositories |
| `git remote show <repository>` | Show information about a remote repository |
| `git remote rename <repository> <new_repository>` | Rename a remote repository |
| `git remote remove <repository>` | Remove a remote repository |
