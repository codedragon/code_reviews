# Introduction to GIT
### Git into Good Habits

## Maria Mckinley
## Assisted by Franco Mattos Neto




# Outline
* <span style="background-color: #E3A95B">Introduction to GIT</span>
* Demonstration of using GIT

Disclosure: This talk is about understanding how to use git, so I will not be going into
certain details, like installing git. I will have links for instructions and feel free
to ping me on slack later for help.




![alt text](assets/final_doc.gif "'Piled Higher and Deeper' by Jorge Cham www.phdcomics.com")




## Problems with the "system" in the cartoon:
* often not obvious which version contains which changes
* often not easy to "revert" changes
* often not clear who changed what
* often not clear how to combine changes from different versions




![alt text](assets/share_manuscript.png "One document, many authors")




## <span style="background-color: #E3A95B">Version control</span>
## is the practice of tracking and managing changes to software code.
## <span style="background-color: #E3A95B">Version control systems</span>
## are software tools that help software teams manage changes to source code over time.




* Git keeps track of history
* Serves as a backup
* Assists you to create a system for easier collaboration
* Can be used to enforce standards




## Some definitions
* Repo (Repository): a collection of files and folders that make a body of work
* Git:  a tool for saving history along with the body of work
* GitHub/GitLab:  a repository copy that everyone can reach and use




## Some important concepts
* All contributers have their own repo copy, including GitHub/GitLab
* Contributers are responsible to keep local copy aligned with central
* The more contributer's copies diverge, the more painful syncing




![alt text](assets/github_gitlab.png "Git repo, many authors")




## More Definitions
* Merge: Combine changes from two copies of a repo




## What's a commit?
* one or more changes made to a repo at one time
* a revision
* how the repo looks now that these changes have been made
* a snapshot of a repo at one moment




## Let's talk about the computer file system for a moment
![alt text](assets/color_coded_files.jpg "organized folders ©Elena Elisseeva | Dreamstime.com")




![alt text](assets/messy-file-folder.jpeg "Messy File Folders")






## Git puts everything it needs to keep track of changes in a hidden directory called
## .git in the root directory of each repository

## ~/.gitconfig




# Outline
* Introduction to GIT
* <span style="background-color: #E3A95B">Demonstration of using GIT</span>




## Installation: I like GitLab's instructions, but others are available
https://docs.gitlab.com/ee/topics/git/how_to_install_git/index.html
## Full, well laid out tutorial
https://docs.gitlab.com/ee/tutorials/make_your_first_git_commit.html




## Tools I chose for this Demo
* Command line
* Editor: emacs
* Git Central Repo: GitLab




# Let's create a repo
* command line: <font size= "10">`git init` </font> 
* https://gitlab.disney.com/projects/new
* https://docs.github.com/en/get-started/quickstart/create-a-repo




## How to set up ssh keys for authenticating - Highly recommended
### GitLab
https://docs.gitlab.com/ee/user/ssh.html
### Github
https://docs.github.com/en/authentication/connecting-to-github-with-ssh




## What's an origin?
* shorthand name for the address of the remote repo a project was cloned from
* default for further communication
* name is just a convention




## How do I see what is the origin?
`git remote -v`




## Workflow
* re-orient yourself to work
* see if others have made changes
* do your work




### Workflow continued
* proofread, decide on content for current change
* select what will be in the change
* add a descriptive note to your change
* put your changes in the common repo so everyone sees your changes




## Workflow
| Command | Description |
| ------- | --------- |
| <font size= "5">`git status` </font> | re-orient yourself to work |
| <font size= "5">`git pull`</font><br>or<br> <font size= "5">`git pull origin main`</font> | see if others have made changes <span style="background-color: #E3735B">needs network</span> |
|         | do work |




### Workflow continued
| Command | Description |
| ------- | --------- |
| <font size= "5">`git diff` and/or<br> `git status` </font> | tools to proofread, decide on content |
| <font size= "5">`git add` </font> | select what's included |
| <font size= "5">`git commit -m` </font> | add a descriptive note |
| <font size= "5">`git push` </font> | add changes to the common repo <span style="background-color: #E3735B">needs network</span> |




# Demo




## Anatomy of a status response
| Output | Description |
| ------ | --------- |
| <font size= "5">`On branch main`</font> | branch currently on |
| <font size= "5">`Your branch is up to date with 'origin/main'.`</font> | commits all pushed to branch 'address/branch'|
| <font size= "5">`Your branch is ahead of 'origin/main' by 1 commit.`</font> | commits not pushed to branch 'address/branch' |  
#### * up-to-date with the upstream status that was retrieved last time we "talked" to the origin




### Anatomy of a status response continued
| Output | Description |
| ------ | --------- |
| <font size= "5">`Changes not staged for commit:`</font> | files with changes that have not been tagged for commit |
| <font size= "5">`Changes to be committed:`</font> | files with changes that have been tagged for commit |
| <font size= "5">`Untracked files:`</font> | files not ever recorded in git |




## Workflow Condensed
| Before Work | After Work |
| ------- | --------- |
| <font size= "5">`git status` </font> | <font size= "5">`git diff` and/or<br> `git status` </font> |
| <font size= "5">`git pull`</font> | <font size= "5">`git add` </font> |
| do work | <font size= "5">`git commit -m` </font> |
|         | <font size= "5">`git push` </font> |




## Git Branching
![alt text](assets/git_branch.png "git branching")




### https://www.atlassian.com/git/tutorials/using-branches




## Other Useful Git Commands

| Command | Description |
| ------- | ----------- |
| <font size= "5">`git checkout filename`</font> | reverts filename to last commit |
| <font size= "5">`git branch`</font> | shows all local branchs, highlights current |
| <font size= "5">`git switch branchname`</font> | switch to a different branch named branchname |
| <font size= "5">`git switch -c branchname`</font> | switch to a new branch named branchname |




## More Useful Git Commands

| Command | Description |
| ------- | ----------- |
| <font size= "5">`git clone repo_address`</font> | create a directory containing a new repo from repo_address |
| <font size= "5">`git merge branchname`</font> | brings changes from branchname into current branch |




# Thank you
## A git pull a day keeps the conflicts away

### https://codedragon.github.io/beginning_git
### maria@mariakathryn.net
