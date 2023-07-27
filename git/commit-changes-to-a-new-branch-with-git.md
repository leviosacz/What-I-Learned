# Commit Changes to a New Branch with Git

To commit local changes to a new branch with git, we can use the following three steps:

## Create a new branch

```bash
git switch -c new-branch
```

This will leave our current branch unedited, create a new branch called new-branch, and we still have our uncommitted changes. It’s the parameter -c that tells git to create a new branch with a selected name.

We can use `git branch -a` command to verify that the new Git branch to be pushed to the remote GitHub repo was indeed created locally.

## Set upstream repos

```bash
git push –set-upstream origin new-branch
```

With a new branch created, the `–set-upstream` switch must be run the first time a push is performed. This step tells the new branch which remote repository to use every time it synchronizes its commit history.

## Add, Commit, and Push

```bash
git add .
git commit -m "First commit on new-branch"
git push origin
```

Once the remote GitHub repository is set as the upstream target for the new Git branch, push and pull operations can be performed normally with a simple `git push origin` command.