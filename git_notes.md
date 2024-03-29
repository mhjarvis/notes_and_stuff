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

Merge conflicts can occur if, after branching, commits or changes are made (for example) to the master (main) branch and the branching branch. When these are merged, they are attempting to merge to the same file and git is uncertain which of the changes to keep. This results in four choices one could make:

1. Pick the changes introduced in the ```master``` branch;
2. Pick the changes in the new branch;
3. Pick both of the changes;
4. Ignore both and write something new altogether;

<h1 align=center>Deleting Branches</h1>

You are able to delete branches from git. Make sure you are not on the branch you are attempting to delete and use the ```-d``` or the ```--delete``` flag:

    git branch -d secondary_branch          // deletes the 'secondary_branch'

In the event that you delete a branch you don't mean to, you can undo so by:

    git branch -v                           // verbous shows the reference code (e.g. 68b3a70)
    git branch secondary_branch 68b3a70     // restores this delted branch

If you want to delete a branch that is not merged, you will get a warning and will need to force delete the branch:

    git branch -D secondary_branch          // force delete

<h1 align=center>Git Log</h1>

To visualize your commit history, Git provides the ```log``` command. It provides the user with the metadata stored during individual commits.

    git log                                     // lists all commits in the current branch, in descending order

    git log --abbrev-commit                     // truncate the commit ID to the identifying part
    git log --pretty=oneline                    // remove author/date to oneline
    git log --pretty=oneline abbrev-commit      // combine args

    git log --oneline                           // shortened version of above
    
To see all commits throught the repository we can use the ```--all``` flag:

    git log --all                                                  // display all commits
    git log --all --graph                                          // display all commits as a graph
    git log --all --graph --pretty=oneline --abbrev-commit         // clean/abbreviated version

<h1 align=center>Git Diff</h1>

The command ```git diff``` can be used to find the difference between all kinds of things in Git. When files are compared, they will be compared a => b, where file 'a' is the old file (the file in the index), and where 'b' is the new file (in the working directory).

The prefix of '-' in output refers to the old file while a prefix of + refers to the new file.

    git diff <filename>                     // basic command
    git diff --word-diff <filename>         //shows how individual words differ rather than how lines differ

```git diff``` compares what is currently in the 'working directory' and the 'index'. Once a file is added to the index, these two will be the same, and the only difference will lie in the 'index' and 'object database' (which will be identical once you commit).

If you want to compare items after adding them to the repository, you can still do so using the ```--chached``` flag. Here we are comparing the previously commited version with the index.

    git diff --cached <filename>            // show the difference between staged file
    git diff --staged <filename>            // does the same thing as --chached

The ```git diff``` command can also be used to compare two different branches. The lastest commits (the tips of the branch) on each branch are then compared.

    git diff branch-a branch-b

<h1 align=center>Undoing with Git Restore</h1>

