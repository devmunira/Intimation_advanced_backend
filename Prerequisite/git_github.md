# Git & GitHub

Git is a version control system that tracks your code updates and saves them.

## Version Control System

There are two types of Version Control Systems:

- **CVCS (Central Version Control System):**  
  Repositories are stored in a central location that can be accessed by multiple people over the internet. Only one repository exists in the central place.

- **DVCS (Distributed Version Control System):**  
  Repositories are stored in a central location and can be accessed by multiple people over the internet. In addition, multiple people can have local copies of the repository on their machines.

## Areas of Code

1. **Working Area**
2. **Staging Area**
3. **Commit Area**

### Commands to Move Code Between Areas

- Move from **Working Area** to **Staging Area**:  
  `git add`
- Move from **Staging Area** to **Commit Area**:  
  `git commit`

- Move from **Staging Area** to **Working Area**:  
  `git checkout`

- Move from **Commit Area** to **Staging Area**:  
  `git reset`

## Git Commands

```bash
git init                      # Initialize a Git repository
git add <file_name>           # Add specific file to staging area
git add .                     # Add all untracked files to staging area
git commit -m "message"       # Add a message to a commit
git log                       # View commit history
git log --oneline             # View commit history in one line
git status                    # Show the status of working and staging areas

git reset <commit_hash>       # Reset to a specific commit
git reset <commit_hash> --soft # Keep working and staging area data
git reset <commit_hash> --mixed # Move staging data to working area
git reset <commit_hash> --hard # Remove all changes and revert to a specific commit

git checkout <file_name>      # Discard changes in the working area
git checkout -b <branch_name> # Create and switch to a new branch
git branch                    # Show all branches
git branch <branch_name>      # Create a new branch
git switch <branch_name>      # Switch to a specific branch
git merge <feature_branch>    # Merge a branch into the current branch
git cherry-pick <commit_hash> # Merge a specific commit from another branch

git config -l                 # View all Git configurations
git config user.name "<name>" --global # Set global user name
git config user.name "<name>"          # Set user name for a specific repository

git remote -v                 # View remote repository URLs
git remote remove origin      # Remove remote origin
git remote add origin <url>   # Add a remote origin

ssh-keygen                    # Generate SSH keys
ssh -T git@github.com         # Test SSH authentication

git stash list

git stash save "stash commit"

git stash pop //pop restore and delete the stash

git stash apply <stash_id> //apply just restore not delete from stash history.

```

### Keywords

- `origin // This is alias of full central repo links (Short Alias)`

- `upstream // Upstream is central repository means github`

- `downstream // Downstream is local repository means your local machine repository`

- `pull // download code from github to local machine`

- `push // upload code from local machine to github central repo`

### Authentication

- Token/ Https Based Auth:
  - Create a Token from Settings
  - `git remote set-url https://<user_name>:<password><repo_url>`
- SSH / Key Based Authentication:

```

git remote -v // see the central repo url

git remote remove origin // remove origin from local repo

git remote add origin <ssh_url> // add new ssh github url to local repo

ssh-keygen //generate ssh key in local machine

add public ssh key on your github account

ssh -T git@github.com // check your authentication

```

### Merge

1. **Fast Forward Merge:** Merge branch is clean tree and feature merge have some extra commits. No Need any commit message.

2. **Three way Merge:** Merge branch have some changes commits and feature merge have some extra commits. Need to add a new commit message.

#### Git Merge Strategy

1. **Octopus Strategy:** Multiple Branch are merge into one branch.
   ` git -s octopus <feature_branch_1> <feature_branch_2>`

2. **Merge Squash:** If feature branch have multiple commits and we directly merge this branch to another branch all commit history will be add on that branch it will load the commit history. To solve this problem we can squashed all previous commits into one commit and merge branch.

```

git merge --squash <feature_branch>
git commit -m "squashed all feature branch commit into one commit and merge"

```

### Rebase

Rebase do the same thing as merge but it's change the commit history as linear approach and it's change the base branch. Rebase command only use private branch that is not shared with github. It's do with private feature branch.

`git rebase <branch_name>`

`git rebase -i <branch_name>`
