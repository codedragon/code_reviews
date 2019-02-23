# Hunting the bugs

## Maria Mckinley




![alt text](assets/Emperor_Gum_Moth.jpg "https://en.wikipedia.org/wiki/Moth#/media/File:Emperor_Gum_Moth.jpg")



<!-- .slide: data-background="#F5DAA3" -->
### The Eniac women were among the first coders to discover that software never works right the first time - and that a programmer's main work, really, is to find and fix the bugs.
### *New York Times Magazine*
### "The Secret History of Women in Coding"




# Hunting Bugs
* scenario
* strategies
* along the way learn about the stack and pdb




# Scenario




# PSA
## periodically check your logs
* where you think they are
* logging what you think they should log




# Do NOT touch your code




# Write an integration test that FAILS




## Review: The stack
![alt text](assets/layer_cake.jpg "https://www.bettycrocker.com/recipes/rainbow-layer-cake-with-rainbow-chip-frosting/6404997b-a255-4942-afd6-b4e6696db70f")




## The stack is a list of the things you have started, but not finished.

* make cake <!-- .element: class="fragment" data-fragment-index="3" -->
* make batter <!-- .element: class="fragment" data-fragment-index="2" -->
* add flour <!-- .element: class="fragment" data-fragment-index="1" -->




If you don't understand the stack, I highly recommend playing around on this website:

http://www.pythontutor.com/visualize.html#mode=edit

The live help feature is pretty cool.




# Stack Trace




# Start at the bottom of the stack trace




## The problem (exception) is always at the bottom
## for a simple stack,  the code that caused it is directly above it.




```python
Traceback (most recent call last):
  File "bad_stack.py", line 4, in <module>
    bad_function()
  File "bad_stack.py", line 2, in bad_function
    print(hello)
NameError: name 'hello' is not defined
```




````python
1 def bad_function():
2     print(hello)
3
4 bad_function()
````




# Let's add to our stack




```python
2  def bad_function():
3      print(okay)
4
5  def add_to_stack():
6      bad_function()
7
8  add_to_stack()
```




```python
Traceback (most recent call last):
  File "bad_stack.py", line 8, in <module>
    add_to_stack()
  File "bad_stack.py", line 6, in add_to_stack
    bad_function()
  File "bad_stack.py", line 3, in bad_function
    print(okay)
NameError: name 'okay' is not defined
```




# Sometimes an error only becomes APPARENT during the line executed on the bottom




![alt text](assets/sunken-cake-veronica-tang_grande.jpg "https://www.angesdesucre.com/blogs/anges-de-sucre/why-wont-my-cake-rise")
##Sunken Cake




```python
Traceback (most recent call last):
  File "stack.py", line 14, in <module>
    add_to_stack()
  File "stack.py", line 12, in add_to_stack
    print(divide_by_ten(my_num))
  File "stack.py", line 8, in divide_by_ten
    return num/10
TypeError: unsupported operand type(s)
             for /: 'str' and 'int'
```




```python
1  def bad_function(num):
2      return str(num)
3
4  def do_something_useless(num):
5      return bad_function(num)
6
7  def divide_by_ten(num):
8      return num/10
9
10 def add_to_stack():
11     my_num = do_something_useless(4)
12     print(divide_by_ten(my_num))
13
14 add_to_stack()
```




# What if I just have a failing test?




<!-- .slide: data-background="#F5DAA3" -->
### Betty Snyder realized that if you wanted to debug a program that wasn't running correctly, it would help to have a *break point,* a moment when you could stop a program midway through its run. To this day, break points are a key part of the debugging process.
### *New York Times Magazine*
### "The Secret History of Women in Coding"




# **P**ython
# **D**e-
# **B**ugger




# But print works




```python
1  def bad_function(num):
2      return str(num)
3
4  def do_something_useless(num):
5      return bad_function(num)
6
7  def divide_by_ten(num):
8      return num/10
9
10 def add_to_stack():
11     my_num = do_something_useless(4)
12     print(divide_by_ten(my_num))
13
14 add_to_stack()
```




```python
python3 stack2.py
> /Users/mckim055/personal/stack2.py(12)add_to_stack()
-> my_num = do_something_useless(4)
(Pdb)
(Pdb) s <!-- .element: class="fragment" data-fragment-index="1" -->
--Call-- <!-- .element: class="fragment" data-fragment-index="1" -->
> /Users/mckim055/personal/stack2.py(4)do_something_useless() <!-- .element: class="fragment" data-fragment-index="1" -->
-> def do_something_useless(num): <!-- .element: class="fragment" data-fragment-index="1" -->
(Pdb) <!-- .element: class="fragment" data-fragment-index="1" -->
(Pdb) n <!-- .element: class="fragment" data-fragment-index="2" -->
> /Users/mckim055/personal/stack2.py(5)do_something_useless() <!-- .element: class="fragment" data-fragment-index="2" --> <!-- .element: class="fragment" data-fragment-index="2" -->
-> return bad_function(num) <!-- .element: class="fragment" data-fragment-index="2" -->
(Pdb) <!-- .element: class="fragment" data-fragment-index="2" -->
(Pdb) s <!-- .element: class="fragment" data-fragment-index="3" -->
--Call-- <!-- .element: class="fragment" data-fragment-index="3" -->
> /Users/mckim055/personal/stack2.py(1)bad_function() <!-- .element: class="fragment" data-fragment-index="3" -->
-> def bad_function(num): <!-- .element: class="fragment" data-fragment-index="3" -->
(Pdb) <!-- .element: class="fragment" data-fragment-index="3" -->
(Pdb) n <!-- .element: class="fragment" data-fragment-index="4" -->
> /Users/mckim055/personal/stack2.py(2)bad_function() <!-- .element: class="fragment" data-fragment-index="4" -->
-> return str(num) <!-- .element: class="fragment" data-fragment-index="4" -->
```




# >>>WHOOSH>>>




# W




# Leave the breakpoint in, Use a similar test




# Use the stack, go back and forth between the tests.




# Always suspect your own code first




# Change things
* New Test
* Fresh commit, then change things (use a version control system)
* What works, what doesn't?




# Pylint and Flake8




# GOOGLE
* Sanitize the terms: Nothing unique from your code
* Python 3
* Understand what you find




## Once upon a time, developers shot trouble without the benefit of a search engine
## Use all the tools available to you




![alt text](assets/bug_joke.jpg "bughunting meme")




# Take a break
![alt text](assets/break.jpg "Costa Rica 2016")




# Write down everything
* Exactly the call and result causing the problem
* Any related log messages
* Exactly what should have happened
* What you have tried so far, clues discovered




# Ask for help
![alt text](assets/batphone.jpg "https://www.millionaireplayboy.com/toys/batphone.php")




# Thank You
## https://codedragon.github.io/bughunting
![bug_wins](https://media.giphy.com/media/qKbDKxfgWGWv6/giphy.gif "https://media.giphy.com/media/qKbDKxfgWGWv6/giphy.gif")
