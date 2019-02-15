# Hunting the bugs

## Maria Mckinley




![alt text](assets/Emperor_Gum_Moth.jpg "https://en.wikipedia.org/wiki/Moth#/media/File:Emperor_Gum_Moth.jpg")




### The Eniac women were among the first coders to discover that software never works right the first time — and that a programmer’s main work, really, is to find and fix the bugs.  ~ *New York Times Magazine*, "The Secret History of Women in Coding"




# Do NOT touch your code




# Write an integration test that FAILS




## Review: The stack
![alt text](assets/layer_cake.jpg "https://www.bettycrocker.com/recipes/rainbow-layer-cake-with-rainbow-chip-frosting/6404997b-a255-4942-afd6-b4e6696db70f")




The stack is a list of the things you have started, but not finished.

* make cake <!-- .element: class="fragment" data-fragment-index="3" -->
* make batter <!-- .element: class="fragment" data-fragment-index="2" -->
* add flour <!-- .element: class="fragment" data-fragment-index="1" -->




If you don't understand the stack, I highly recommend playing around on this website:

http://www.pythontutor.com/visualize.html#mode=edit

The live help feature is pretty cool.




# Start at the bottom of the stack trace




## The problem (exception) is always at the bottom
## for a simple stack,  the code that caused it is directly above it.




```
Traceback (most recent call last):
  File "bad_stack.py", line 17, in <module>
    create_exception()
  File "bad_stack.py", line 15, in create_exception
    print(hello)
NameError: name 'hello' is not defined
```



````python
14 def create_exception():
15     print(hello)

17 create_exception()
````




# Let's add to our stack




```python
def bad_function():
    print(okay)

def add_to_stack():
    bad_function()
```




```python
Traceback (most recent call last):
  File "bad_stack.py", line 11, in <module>
    add_to_stack()
  File "bad_stack.py", line 7, in add_to_stack
    bad_function()
  File "bad_stack.py", line 3, in bad_function
    print(okay)
NameError: name 'okay' is not defined
```




## Sometimes an error only becomes APPARENT during the line executed on the bottom




![alt text](assets/sunken-cake-veronica-tang_grande.jpg "https://www.angesdesucre.com/blogs/anges-de-sucre/why-wont-my-cake-rise")
##Sunken Cake




```python
def bad_function():
    return 0

def ten_divide_by_my_num():
    my_num = bad_function()
    return 10/my_num

def add_to_stack():
    print(ten_divide_by_my_num())
```




```python
Traceback (most recent call last):
  File "bad_stack.py", line 15, in <module>
    add_to_stack()
  File "bad_stack.py", line 11, in add_to_stack
    print(ten_divide_by_my_num())
  File "bad_stack.py", line 7, in ten_divide_by_my_num
    return 10/my_num
ZeroDivisionError: division by zero
```



## Pylint and Flake8




## Google
* Sanitize the terms: Nothing unique from your code
* Python 3
* Understand what you find




## Once upon a time, developers shot trouble without the benefit of a search engine
Use all the tools available to you




## Always suspect your own code first




## What if I just have a failing test?




# PDB




### Betty Snyder realized that if you wanted to debug a program that wasn’t running correctly, it would help to have a *break point,* a moment when you could stop a program midway through its run. To this day, break points are a key part of the debugging process. ~ *New York Times Magazine*, "The Secret History of Women in Coding"




# >>>WHOOSH>>>




# W




# Leave the breakpoint in, Use a similar test




# Use the stack, go back and forth between the tests.




## Change things
* New Test
* Fresh commit, then change things (use a version control system)
* What works, what doesn't?




# Take a break
![alt text](assets/break.jpg "Costa Rica 2016")




## Write down everything
* Exactly the call and result causing the problem
* Any related log messages
* Exactly what should have happened
* What you have tried so far, clues discovered




# Ask for help
![alt text](assets/batphone.jpg "https://www.millionaireplayboy.com/toys/batphone.php")




# Thank You
