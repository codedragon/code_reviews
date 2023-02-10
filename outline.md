An opinionated intro to git guide

1. Why GIT - what problems does it solve
   1. cartoon, revision history
   2. multiple people working on one project
   3. enforce standards
2. Install/configure GIT
   Git from the command line, once you understand everything in this talk, feel free to use the gui :)
   default editor
   1. an aside about directories/folders 
      Still kind of feels like the messy folders in folders, files are misnamed.
   2. git vs repo vs github/gitlab
3. Working by myself
   1. New repo, first steps: create a repo, follow directions, take notes for new repo
   2. git structure: git clone will create a directory in the directory your terminal is currently showing
   3. .git folder "hidden"
      1. configuration, keeps track of repo history
      2. you can safely move an entire repo around on your computer 
   4. workflow
      1. git status: check to see what you were working on, forgot about
      	 1. break down git status, show what it looks like with no changes, some changes, explain commit right off
      2. git pull: (see what others have been doing or what you did on a different machine)
      3. do some work
      4. git diff: decide if everything you have done should be included in the same bundle of work.
      (the revision your prof asked for)
      	 1. imagine scenario where you are making the easy changes, then you start on the hard changes, and
	    decide you better save what you already have before going too far. Or you finish the hard part, and
	    decide it would be better to keep it separate from the other changes.
	 2. gitignore
      5. git add: to make a bundle of work (just include the pages of the manuscript you made changes to)
      6. git commit: to verify that bundle of work
      (put a note on it: Sorry it took me so long to write that proof you asked for.)
      7. git push: send it up to a central repository (mail that manuscript)
4. Working with others
   1. How different
   2. Get existing repo
   3. Branches
   4. workflow
5. Security
   1. git saves everything, so don't even temporarily save passwords, tokens, sensitive data


