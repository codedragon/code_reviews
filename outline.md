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
         1. break the code down to its essence, if you can.
	 2. type hints are useful for this, consider using them.
	 3. as you break the code down to its essence,
	 you are finding the spots to mock for a unit test, this is for free :)
	 4. places where data changes are places to test
      2. how code is organized
      tree
      but one in which the roots split and reconnect
      3. understanding the stack
      4. what is the stacktrace
   2. the scientific method
      1. By Efbrazil - Own work, CC BY-SA 4.0, https://commons.wikimedia.org/w/index.php?curid=102392470
      2. my version of the image
      3. simplify things
   3. error messages, more than just the stacktrace
      1. read the message
      2. messages have improved! :)
   3. the debugger
      1. print
      2. the stack again

3. more tools
   1. Change things - one at a time, scientific method
   2. Pylint and other code checkers
   3. Search Engines
   4. Write everything down
   5. Take a break
   6. Ask for help
      1. checklist for writing that question.
      2. places to ask

* Conclusion
