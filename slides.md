# Hunting the bugs

## Maria Mckinley




# You have a stack trace, now what?




# Write a test!




## Review: The stack 
![alt text](assets/stack_pancakes.jpg "https://thestayathomechef.com/pancake-recipe/")


The stack is a list of the things you have started, but not finished.

* make cake
* make buttercream
* make syrup
* add sugar

If you don't understand the stack, I highly recommend playing around on this website:

http://www.pythontutor.com/visualize.html#mode=edit

The live help feature is pretty cool.




## In a simple stacktrace, the problem is usally at the bottom, and the code that caused it directly above it.

```
python3 except_excercise.py
  File "except_excercise.py", line 2
    from __future__ import braces
    ^
SyntaxError: not a chance
```

