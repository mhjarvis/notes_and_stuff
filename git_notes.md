<h1 align=center>Git Commit</h1>

    git init                        // initialize a new Git repository

<h1 align=center>Branches</h1>
The default branch for a repository is ```master```. It can be renamed, even permanently, but the default is ```master```.

The ```branch``` command can be used to create a new branch, list all branches in a repository, and delete branches.

    git branch a_new_branch         // create a new branch
    git branch                      // list all branches in the current directory

    git switch a_new_branch         // switch to the new branch
    
```git switch``` can both create and switch to the new branch in one go. This is achieved using the -c (--create) command.

    git switch -c my-first-branch

