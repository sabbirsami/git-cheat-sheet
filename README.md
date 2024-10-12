
# Git Cheat Sheet

## Setup
Set the name and email that will be attached to your commits and tags:
```bash
$ git config --global user.name "your-username"
$ git config --global user.email "youremail@gmail.com"
```

---

## Start a Project
Create a local repo (initialize the current directory as a git repo):
```bash
$ git init <directory>
```

Download a remote repo:
```bash
$ git clone <url>
```

---

## Make a Change
Add a file to staging:
```bash
$ git add <file>
```

Stage all files:
```bash
$ git add .
```

Commit all staged files to git:
```bash
$ git commit -m "commit message"
```

Add changes to tracked files to staging:
```bash
$ git commit -am "commit message"
```

---

## Remove node_module / .env file from GitHub
To remove a file from your GitHub repository, follow these steps:

1. **Remove the file from your local repository** using the `git rm` command:
    ```bash
    git rm <file_path>
    ```

2. **Commit the changes** to your local repository:
    ```bash
    git commit -m "Removed <file_path>"
    ```

3. **Push the changes** to your remote GitHub repository:
    ```bash
    git push origin <branch_name>
    ```

If you want to remove the file from version control but keep it in your local file system, use:
```bash
git rm --cached <file_path>
```


## Retrieve a File from a Previous Commit

To retrieve a file from a previous commit in your Git repository, follow these steps:

1. **Find the commit hash** that contains the version of the file you want. Use:
    ```bash
    git log --oneline
    ```

2. **Checkout the file from the specific commit** using:
    ```bash
    git checkout <commit_hash> -- <file_path>
    ```

    This command retrieves the version of the file from the specific commit and places it in your working directory.

3. **Optionally, commit the changes** if you want to keep the retrieved version:
    ```bash
    git add <file_path>
    git commit -m "Reverted <file_path> to version from <commit_hash>"
    git push origin <branch_name>
    ```

---
---

## Change the Remote Repository URL

To change the remote repository URL in your Git repository, follow these steps:

1. **View the current remote URL** (optional):
    ```bash
    git remote -v
    ```

2. **Change the remote URL** using the `set-url` command:
    ```bash
    git remote set-url origin <new_url>
    ```

3. **Verify the change** (optional):
    ```bash
    git remote -v
    ```

---

## Basic Concepts
- `master`: Default development branch
- `origin`: Default remote name
- `HEAD`: Current branch
- `HEAD^`: Parent of HEAD
- `HEAD~4`: 4th commit back from HEAD

---

## Branches
List all local branches (add `-r` flag to show all remote branches, `-a` to show all branches):
```bash
$ git branch
```

Create a new branch:
```bash
$ git branch <new-branch>
```

Switch to a branch and update the working directory:
```bash
$ git checkout <branch>
```

Create a new branch and switch to it:
```bash
$ git checkout -b <new-branch>
```

Delete a merged branch:
```bash
$ git branch -d <branch>
```

Delete a branch, whether merged or not:
```bash
$ git branch -D <branch>
```

Add a tag to current commit (use `-a` to tag new releases):
```bash
$ git tag <tag-name>
```

---

## Merging
Merge a branch into a branch B (add `--no-ff` to avoid fast-forward merge):
```bash
$ git merge <branch>
```

Merge and rebase all commits at once (single commit):
```bash
$ git merge --squash <branch>
```

---

## Rebasing
Rebase feature branch onto main to incorporate new changes made to main (prevents unnecessary merge commits into feature, keeping history linear):
```bash
$ git checkout feature
$ git rebase main
```

Iteratively clean up a branch's commits before rebasing onto main:
```bash
$ git rebase -i main
```

Iteratively rebase the last 3 commits in the current branch:
```bash
$ git rebase -i Head~3
```

---

## Undoing Things
Move (and/or rename) a file and stage it:
```bash
$ git mv <existing-path> <new-path>
```

Remove a file from the working directory and from staging area, then stage the deletion:
```bash
$ git rm <file>
```

Reset a file or a commit:
- Reset a file from staging area only:
  ```bash
  $ git reset <file>
  ```
- Reset the index and working directory to a specific commit (read-only):
  ```bash
  $ git reset --hard <commit_ID>
  ```

Revert a commit by creating a new commit:
```bash
$ git revert <commit_ID>
```

Restore file to a specific commit (leaves staging alone):
```bash
$ git checkout <commit_ID> <file>
```

---

## Review your Repo
List new or modified files not yet committed:
```bash
$ git status
```

List commit history, with respective IDs:
```bash
$ git log --oneline
```

Show changes to unstaged files (to changes of staged files, add `--cached` option):
```bash
$ git diff
```

Show changes between two commits:
```bash
$ git diff commit1_ID commit2_ID
```

---

## Stashing
Store modified and staged changes (to include untracked files, add `-u` flag. For untracked & ignored files, add `-a`):
```bash
$ git stash
```

As above, but add a comment:
```bash
$ git stash save "comment"
```

Partial stash (stash just single file):
```bash
$ git stash push -p
```

List all stashes:
```bash
$ git stash list
```

Apply stash:
```bash
$ git stash apply stash@{1}
```

Delete stash at index 1 (omit stash@{n} to delete the last stash):
```bash
$ git stash drop stash@{1}
```

Clear all stashes:
```bash
$ git stash clear
```

---

## Synchronizing
Add a remote repo:
```bash
$ git remote add <alias> <url>
```

View all remote connections (add `-v` to view full URLs):
```bash
$ git remote
```

Remove a connection:
```bash
$ git remote remove <alias>
```

Rename a connection:
```bash
$ git remote rename <old> <new>
```

Fetch all branches from remote repo (no merge):
```bash
$ git fetch <alias>
```

Fetch a specific branch:
```bash
$ git fetch <alias> <branch>
```

Merge fetched changes into current branch:
```bash
$ git pull
```

Push all branches to remote repo:
```bash
$ git push <alias> <branch>
```

---

This cheat sheet summarizes the most common Git commands and operations. For more detailed information, refer to the official Git documentation.

---


<p align="center">
  <a href="https://sabbir-mohammad-sami.vercel.app"><strong>Portfolio &rarr;</strong></a>  <a href="https://discord.com/users/993823123122171934"><strong>Discord &rarr;</strong></a>
</p>

