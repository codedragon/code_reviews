# Code Reviews
### The Art and the Science

## Maria Mckinley
## Staff Software Engineer and SRE at Disney




# Outline
* Mental Models
* The trials of code reviews
* But, why?
* About Failure
* Making Code Reviews better




# Outline
* <span style="background-color: #E3A95B">Mental Models</span>
* The trials of code reviews
* But, why?
* About Failure
* Making Code Reviews better




## Mental Model of a Tree by a Scientist
![Mental Model of Tree by Scientist](assets/PartsOfTree.jpeg "parts of tree by scientist")




## Mental Model of a Tree by a Child
![Mental Model of Tree by Child](assets/TreeByChild.JPG "xmas tree with presents drawn by 'child'") 




## According to Gitlab:
## A code review is a peer review of code that helps developers ensure or improve the
## code quality before they merge and ship it.




## A better mental model:
## A code review is a way for a team to share knowledge, learn together and
## assess the quality of the code they are shipping before they ship it.




## Emphasize team growth and learning over code quality.
## Code quality follows from team quality




## Lots of research backs up the importance of teamwork on software development
### Leave it as an exercise for the audience, good place to start:
### https://www.atlassian.com/blog/teamwork/the-importance-of-teamwork




## I want to convince you that code reviews can be the pathway to a better team




# Outline
* Mental Models
* <span style="background-color: #E3A95B">The trials of code reviews</span>
* But, why?
* About Failure
* Making Code Reviews better




## What makes code reviews hard?




## Wait, am I paid to think?




<!-- .slide: data-background-image="assets/newspaper.jpg"
     	     background-size="150% auto"
	     background-repeat="no-repeat"-->
# Developer failed!
## fear of failure
## fear of bad news




<!-- .slide: data-background-image="assets/newspaper.jpg"
     	     background-size="contain"
	     background-repeat="no-repeat"-->
# Developer gets in an argument!
# fear of conflict
# actual conflict, squables




<!-- .slide: data-background-image="assets/newspaper.jpg"
     	     background-size="contain"
	     background-repeat="no-repeat"-->
# Developer runs out of time!
## fear of losing
## fear of deadlines




![alt text](assets/frazz.gif "FRAZZ © Jef Mallett. Dist. By ANDREWS MCMEEL SYNDICATION. Reprinted with permission. All rights reserved.")




## Why? Blindspots
* fixed mindset vs growth mindset 
* expectation we are done learning when we leave school
* not taught how to productively disagree
* image of code guru producing entire operating systems in basement





## Let's talk about the computer file system for a moment












## Git puts everything it needs to keep track of changes in a hidden directory called
## .git in the root directory of each repository

## ~/.gitconfig








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
