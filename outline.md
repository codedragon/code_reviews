Made it to where I need graphics for code flow, more or less

* Intro An opinionated troubleshooting guide
some opinionated best practices thrown in for free

2 story lines, one bug report from outside user
one my real life bug from last week

1. basic steps for troubleshooting:
   1. verify bug
      1. logs (psa)
      2. make sure you can reproduce bug
         1. user error: maybe the documentation is the problem
         2. can't fix what you can't see
   2. write a test that fails
      1. why testing is important
      	 1. ensures everyone knows what the code is suppose to be doing
         2. ensures the code works
         3. faster development
         4. ensures bugs do not come back
      2. why before writing code?
         1. make sure you can reproduce the bug
         2. make sure you actually fix the bug
   3. Fix the bug

2. Dig into the code
   1. Understanding the code
      if code is difficult for you to understand, it probably is for others
      what happens when you run across code you don't understand
      1.https://pythontutor.com/visualize.html#mode=edit
      2. break the code down to its essence, if you can. likely place for my story
      3. as you break the code down to its essence, you are finding the spots to mock for a unit test, this is for free :)
      4. places where data changes are places to test	 
      5. how code is organized
      tree
      but one in which the roots split and reconnect
      we think of it as linear, a script, a recipe, but with software it is more like each step often sends you off to a new recipe, one that you will need to return from, but may well visit several more recipes first.
      3. understanding the stack
      4. what is the stacktrace
   2. the scientific method
      1. By Efbrazil - Own work, CC BY-SA 4.0, https://commons.wikimedia.org/w/index.php?curid=102392470
      2. my version of the image
      3. simplify things
            so ask yourself, from tree, which connections can you sever to simplify the problem?
	    how do I isolate the problem?
      2. psa: leave notes when you figure out a bit of code that was confusing
   3. error messages, more than just the stacktrace
      1. read the message
      2. messages have improved! :)
   3. the debugger
      1. print
      2. the stack again

3. more tools
   1. Change things - one at a time, scientific method
   2. Pylint and other code checkers
   3. type hints are useful for understanding code, and preventing errors, consider using them.
   4. Search Engines
   5. Write everything down
   6. Take a break
   7. Ask for help
      1. checklist for writing that question.
      2. places to ask

* Conclusion

May have to ask Jordan...

My story in slack messages, lol
starts inside an fastapi app, inside a docker container, using memcache
simplify, realize I can lose the docker container, memcache, and even fastapi
Once I try everything I can think of, and have read website
go to link to underlying library
discover I am loading the variables with that library,
but they aren't making it into the Settings object
