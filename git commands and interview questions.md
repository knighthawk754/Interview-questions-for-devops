# GIT 

**what is version control system**

- software tools that help software teams manage changes to source code over time. Track history of the collection of files
- In other word it is used to maintain the version of the Source code 


## Localiszed and centralized 

- Localized version control system keeps local copies of the file 
- In the centralized control there is server and client. Where Server contains all version of the source code 


## Distributed version control system 

- In DVCS each user has a copies of a repository in local computer as well as in the remote server

- all versions of the git will be saved in the local repo in the .git folder 


# Commands 

- `git init`

- `Git status` : it will show current status of the repository
- `git add .` This will add the untracked files to staging directory (The `git add` command is used to add changes in your working directory to the staging area)
- `git commit -m "give any message"` A Git commit is like a snapshot of your project at a specific point in time. When you make a commit, Git saves the state of your project, including all tracked files, and assigns a unique identifier (a commit hash) to this snapshot. Each commit is uniquely identified by a SHA-1 hash

- `git log` or `git log --oneline` which will show the previous commits 
- `git show <commit ID>`
- The `git restore --staged <filename>` command removes the specified file(s) from the staging area without deleting the file(s) from the working directory
- To add your GitHub username and email to the git global config, use the following steps:
``` 
git config --global user.name "YOUR_USERNAME"
git config --global user.email "YOUR_EMAIL"
```
- The `git reset` command is used to undo changes by moving the current branch pointer to a specified commit and optionally modifying the index and working directory. example: ``` git reset 90994781ed235811e32221eb82e88799fb76ab85 ```
- The `git stash` command temporarily saves changes in your working directory that are not yet committed, allowing you to switch branches or work on something else without losing your progress.
- The `git stash pop` command applies the most recently stashed changes to your working directory and removes that stash from the stash list.
- The `git stash` clear command deletes all stashes in your stash list, permanently removing them.
- The `git remote -v ` shows the current list of remote origin
- `git push origin` Pushes your local branch to the remote repository named origin
- `git push origin -f`: Forcefully pushes your local branch to the remote repository named origin, overwriting any conflicts.


What is HEAD in git : It is just an pointer 

### Difference between Origin and upstream 
-In simple terms, "origin" is the default name for the remote repository you cloned from, while "upstream" is typically used to refer to the original repository from which your repository was forked.


## Branching
- `Git branch`: Git branches are important because they allow developers to work on different features, fixes, or experiments in isolation without affecting the main codebase.

- To create a new branch `git branch <branch_name>`
- To switch to a particular branch in your Git repository 
   - Check the list of branches to ensure the target branch exists
        `git branch -a`
    - Switch to the desired branch using the following command:
         `git checkout <branch_name>`	
		 
Note: wheever we are working in one feature or on bug on the application. Create a branch for that and create pull request to that branch. In Simple terms (One Branch == One pull request)

- `git fetch --all --prune` This command fetches updates from all remote repositories and prunes (removes) any branches that no longer exist on the remote.
- The command `git reset --hard upstream/main` is used to reset your current branch to match the main branch of the upstream remote repository, discarding all local changes.
- The command `git pull upstream main` is used to fetch and merge changes from the main branch of the upstream remote repository into your current branch. This is useful for keeping your local branch up to date with the latest changes from the original repository.
-  Git rebase is a command that allows you to integrate changes from one branch into another by moving or combining a sequence of commits to a new base commit.
- Git squash combines multiple commits into a single commit.

```
git rebase -i HEAD~<number_of_commits>
````
Replace <number_of_commits> with the number of commits you want to squash. In the interactive rebase screen, change pick to squash (or s) for the commits you want to squash into the previous one.

### Difference between pick and squash
 - `pick`: Use this command in an interactive rebase to keep a commit as it is. It's used to select commits that you want to keep unchanged.
- `squash`: Use this command in an interactive rebase to combine the current commit with the previous commit. The commit messages of both commits will be combined, allowing you to condense multiple commits into one

**The message "this branch is 4 commits behind the master" means that the branch in question is 4 commits behind the master branch on GitHub, which indicates that there are changes in the master branch that have not yet been merged or integrated into your branch**

**Merge the master branch into your branch (Safe method)**

- ``` git checkout your-branch ```
- ``` git merge master ```

------------------------------------------------------------------------------------------------------------------------------------------
## Whats is merge conflict
A merge conflict occurs when Git is unable to automatically resolve differences in code between two commits. This typically happens when changes are made to the same line of a file in different branches or when one branch modifies a file and another branch deletes it.
