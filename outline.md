An opinionated intro to git guide

Outline

1. Introduction
   1. cartoon, revision history
   2. Why GIT - what problems does it solve
      1. problems with system in cartoon
      2. multiple people working on one project
         or one person, many computers
      3. Version Control
      4. purpose
   3. Definitions
      1. Repo vs Git vs GitHub
   4. Concepts
      1. many people, one shared repo address
      2. Merge
      3. Commit
      4. .git folder
      	 1. an aside about directories/folders
            Still kind of feels like the messy folders in folders, files are misnamed.
      	 2. git structure: git clone will create a directory in the directory your terminal is currently showing
	 3. configuration, keeps track of repo history
	 4. you can safely move an entire repo around on your computer 
2. Demo
   1. link to Install GIT
   2. tools
      1. Git from the command line, once you understand everything in this talk, feel free to use the gui :)
      2. default editor
   3. create a repo
      1. demo gitlab
	 1. readme important
      2. ssh keys
      3. what's an origin?
      4. demo it
   4. Workflow
      1. Without git commands
      2. With git commands
      3. demo it
      	 1. `git status`: check to see what you were working on, forgot about
	    1. slide
	 2. `git pull`:
      	    1. see what others have been doing or what you did on a different machine
	    2. Needs network, Disney vpn
            3. shorthand for `git pull origin main`
      	 3. do some work
	 4. proofread/decide on content
      	    1. `git diff`: decide if everything you have done should be included in the same bundle of work.
      	       (the revision your prof asked for)
	       1. Security: git saves everything, so don't even temporarily save passwords, tokens, sensitive data
      	    2. imagine scenario where you are making the easy changes, then you start on the hard changes, and
	    decide you better save what you already have before going too far. Or you finish the hard part, and
	    decide it would be better to keep it separate from the other changes.
	    3. git status
	       1. break down git status, show what it looks like with no changes, some changes
	    4. .gitignore
      	 5. `git add`: to make a bundle of work (just include the pages of the manuscript you made changes to)
      	 6. `git commit -m "my commit message"`: to verify that bundle of work, will dump in editor without `-m "my commit message"`
      (put a note on it: Sorry it took me so long to write that proof you asked for.)
      	 7. `git push`: send it up to a central repository (mail that manuscript) Needs network
4. Working with others
   1. How different
   2. Get existing repo
   3. Branches (Main not Master)
   4. workflow
5. Security
   