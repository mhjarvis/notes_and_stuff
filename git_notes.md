<h1 align=center>Git Commit</h1>

    git init                        // initialize a new Git repository
    git add <filename>              // git makes copy of file and puts it in the index

    git commit -m '...'             // git takes contents of staging area and stores
                                    // those in the object database

    git status                      // check the status of the files in your directory

<h1 align=center>Branches</h1>
The default branch for a repository is ```master```. It can be renamed, even permanently, but the default is ```master```.

The ```branch``` command can be used to create a new branch, list all branches in a repository, and delete branches.

    git branch a_new_branch         // create a new branch
    git branch                      // list all branches in the current directory
    git branch -v                   // list commit IDs on each branch

    git switch a_new_branch         // switch to the new branch
    
```git switch``` can both create and switch to the new branch in one go. This is achieved using the -c (--create) command.

    git switch -c my-first-branch

** Every time you switch branches, Git rewrites your working directory to look like it did when you made the most recent commit on the branch you just switched to. Thus, refresh your editor or reopen the project after switching branches.

<h1 align=center>Merging</h1>

The ```git merge``` command allows you to combine the work done in different branches.

    git merge the_new_branch        // will merge branch into the active branch
                                    // upon merging, the master branch will 
                                    // 'catch up' to the merged branch

    git branch -v                   // both branches will have the same commit ID
                                    // they point to the same branch


