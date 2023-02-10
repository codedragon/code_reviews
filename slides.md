# Introduction to GIT
### An opionated guide

## Maria Mckinley
## Assisted by Franco Mattos Neto




#Outline
* Introduction to GIT
* Demonstration of using GIT

Disclosure: This talk is about understanding how to use git, so I will not be going into
certain details, like installing git. I will have links for instructions and feel free
to ping me on slack later for help.




![alt text](assets/final_doc.gif "'Piled Higher and Deeper' by Jorge Cham www.phdcomics.com")




![alt text](assets/share_manuscript.png "One document, many authors")




##Git keeps track of history
##Serves as a backup
###(as long as you push your changes to at least one other machine)
##Can be used to enforce standards




##Some definitions
* Repo: repository, a collection of files and folders that make a body of work
* Git:  a tool for saving history along with the body of work
* GitHub/GitLab:  a central repository copy that everyone can reach and use




##Some important concepts
* All contributers have their own repo copy, including GitHub/GitLab
* Contributers are responsible to keep local copy aligned with central
* The more contributer's copies diverge, the more painful syncing




![alt text](assets/github_gitlab.png "Git repo, many authors")




##Let's talk about the file system for a moment
![alt text](assets/color_coded_files.jpg "organized folders ©Elena Elisseeva | Dreamstime.com")




![alt text](assets/messy-file-folder.jpeg "Messy File Folders")






Git puts everything it needs to keep track of changes in a hidden directory called
.git in the root directory of each repository




#Installation: I like GitLab's instructions, but others are available
https://docs.gitlab.com/ee/topics/git/how_to_install_git/index.html
#Full, well laid out tutorial
https://docs.gitlab.com/ee/tutorials/make_your_first_git_commit.html




##Choices I made for this Demo
* Command line
* Editor: emacs
* Git Central Repo: Gitlab




#Let's create a repo
command line: git init 
https://gitlab.disney.com/projects/new




##How to set up ssh keys for authenticating - Highly recommended
###Gitlab
####https://docs.gitlab.com/ee/user/ssh.html
###Github
####https://docs.github.com/en/authentication/connecting-to-github-with-ssh




##What's a commit?
* one or more changes made to a repo
* a revision
* how the repo looks now that these changes have been made
* a snapshot of your repo at a moment in time




### https://codedragon.github.io/beginning_git
### maria@mariakathryn.net
