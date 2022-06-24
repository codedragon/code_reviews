# Hunting the bugs
### An opionated guide

## Maria Mckinley




![alt text](assets/eniac4.png "U.S. Army Photo")




### The Eniac women were among the first coders to discover that software never works right the first time - and that a programmer's main work, really, is to find and fix the bugs.
### *New York Times Magazine*
### "The Secret History of Women in Coding"




# Hunting Bugs
* <span style="background-color: #e6d300">Background Information: bugs and stacks</span>
* Basic Steps for Trouble Shooting
* Tools for Easier Bug Hunting




# What is a bug?




![alt text](assets/first_computer_bug.jpg "First debugging")




## A bug is a general term used to describe any unexpected problem with hardware or software.




## Understanding the stack
![alt text](assets/layer_cake.jpg "https://www.bettycrocker.com/recipes/rainbow-layer-cake-with-rainbow-chip-frosting/6404997b-a255-4942-afd6-b4e6696db70f")




## The stack is a list of the things you have started, but not finished.

* make cake <!-- .element: class="fragment" data-fragment-index="3" -->
* make batter <!-- .element: class="fragment" data-fragment-index="2" -->
* add flour <!-- .element: class="fragment" data-fragment-index="1" -->




## I highly recommend playing on this website to get a better grasp of the stack:

## http://www.pythontutor.com

### The live help feature is pretty cool.




# Stack Trace
## (aka Traceback)
## The stack at the moment something goes wrong




```python
Traceback (most recent call last):
  File "bakecake.py" line 20, in <module>
    make_cake()
  File "bakecake.py" line 15, in make_cake
    make_batter()
  File "bakecake.py" line 13, in make_batter
    add_flour(flour)
IngredientError: flour is empty
```




```python
Traceback (most recent call last):

    make_cake()

    make_batter()

    add_flour(flour)
IngredientError: flour is empty
```




# Start at the bottom of the stack trace




## The problem (exception) is always at the bottom
## and the code that caused it is often directly above it.




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
1  def bad_function():
2      print(okay)
3
4  def add_to_stack():
5      bad_function()
6
7  add_to_stack()
```




```python
Traceback (most recent call last):
  File "bad_stack.py", line 7, in <module>
    add_to_stack()
  File "bad_stack.py", line 5, in add_to_stack
    bad_function()
  File "bad_stack.py", line 2, in bad_function
    print(okay)
NameError: name 'okay' is not defined
```




# An error may only become APPARENT as the line on the bottom is executed




![alt text](assets/layer_cake.jpg "https://www.bettycrocker.com/recipes/rainbow-layer-cake-with-rainbow-chip-frosting/6404997b-a255-4942-afd6-b4e6696db70f")




![alt text](assets/sunken-cake-veronica-tang_grande.jpg "https://www.angesdesucre.com/blogs/anges-de-sucre/why-wont-my-cake-rise")
##Sunken Cake




```python
Traceback (most recent call last):
  File "stack2.py", line 11, in <module>
    add_to_stack()
  File "stack2.py", line 9, in add_to_stack
    print(divide_by_ten(my_num))
  File "stack2.py", line 5, in divide_by_ten
    return num/10
TypeError: unsupported operand type(s)
             for /: 'str' and 'int'
```




```python
1  def bad_function(num):
2      return str(num)
3
4  def divide_by_ten(num):
5      return num/10
6
7  def add_to_stack():
8      my_num = bad_function(4)
9      print(divide_by_ten(my_num))
10
11 add_to_stack()
```




```python
1  def bad_function(num: int) -> str:
2      return str(num)
3
4  def divide_by_ten(num: int) -> int:
5      return num/10
6
7  def add_to_stack()  -> None:
8      my_num = bad_function(4)
9      print(divide_by_ten(my_num))
10
11 add_to_stack()
```
Type Hints for the Win




# What about this stacktrace




```python
Traceback (most recent call last):
  File "bad_function.py", line 3, in bad_function
    print("Hi" + greeting)
TypeError: can only concatenate str (not "int") to str

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "bad_function.py", line 10, in <module>
    add_to_stack(2)
  File "bad_function.py", line 8, in add_to_stack
    bad_function(okay)
  File "bad_function.py", line 5, in bad_function
    print(greeting + "does not work")
TypeError: unsupported operand type(s) for +: 'int' and 'str'
```




```python
1 def bad_function(greeting):
2     try:
3         print("Hi" + greeting)
4     except Exception:
5         print(greeting + "does not work")
6
7 def add_to_stack(okay):
8     bad_function(okay)

add_to_stack(2)
```




## Some best practices with exceptions
* Don't except Exception
  (if REALLY necessary log, and READ logs)
* Minimal code in Try block, ONLY what you expect might fail
* Be careful with Except block, avoid Traceback hell




# Error Messages Have Improved! :) Python 3.10
https://realpython.com/lessons/better-error-messages/




# Hunting Bugs
* Background Information: bugs and stacks
* <span style="background-color: #e6d300">Basic Steps for Trouble Shooting</span>
* Tools for Easier Bug Hunting




## Basic Steps for Trouble Shooting
* <span style="background-color: #e6d300">Verify the bug</span>
* Write things down
* Write a test that fails
* Understand the problem space
* Fix the bug so the test passes
* Verify the bug is gone




# Reproduce the bug, if possible
## Might mean reaching out to the person who wrote the bug report
## Might mean checking the logs




# PSA
## periodically check your logs
* where you think they are
* logging what you think they should log
https://blog.guilatrova.dev/how-to-log-in-python-like-a-pro/




![alt text](assets/farside.jpg "Far Side Cartoon")
## User Error? <!-- .element: class="fragment" data-fragment-index="1" -->
### Maybe documentation is the problem <!-- .element: class="fragment" data-fragment-index="2" -->
### Maybe the interface is the problem <!-- .element: class="fragment" data-fragment-index="3" -->




## Basic Steps for Trouble Shooting
* Verify the bug
* <span style="background-color: #e6d300">Write things down</span>
* Write a test that fails
* Understand the problem space
* Fix the bug so the test passes
* Verify the bug is gone




# Write down everything
* Exactly the call causing the problem
* Exactly what should have happened
* Exactly what did happen
* Any related log messages




## Basic Steps for Trouble Shooting
* Verify the bug
* Write things down
* <span style="background-color: #e6d300">Write a test that fails</span>
* Understand the problem space
* Fix the bug so the test passes
* Verify the bug is gone




# Do NOT touch your code




# Write an integration test that FAILS




# Why test?
![alt text](assets/software_bugs_news.png "Software Bugs in the News")




## https://www.karllhughes.com/posts/testing-matters
## https://www.obeythetestinggoat.com/




# Why before?
### (Test Driven Bughunting?)




## New branch for your bug hunting
## then change things
## (use a version control system)




## Basic Steps for Trouble Shooting
* Verify the bug
* Write things down
* Write a test that fails
* <span style="background-color: #e6d300">Understand the problem space</span>
* Fix the bug so the test passes
* Verify the bug is gone




# Understand the problem within the context of the code
## When did you look at the code last?




<img src="assets/simple_program.png" alt="Simple Software Program" width="550"/>




# what code flow more often looks like:
<img src="assets/potpie.jpg" alt="chicken pot pie" width="500"/>




# Try to understand the big picture
## how the system is suppose to work
## think about how data flows and changes




# Understand History
## what has changed since the last time things worked
## example: bits of code, upgraded libraries
## time (daylight savings, timezones, format)




## Basic Steps for Trouble Shooting
* Verify the bug
* Write things down
* Write a test that fails
* Understand the problem
* <span style="background-color: #e6d300">Fix the bug so the test passes</span>
* Verify the bug is gone




# To fix the bug, we must find it




<img src="assets/The_Scientific_Method.svg" alt="scientific method" width="550"/>
#### By Efbrazil - Own work, CC BY-SA 4.0, https://commons.wikimedia.org/w/index.php?curid=10239247




<img src="assets/The_Bughunting_Method.svg" alt="bughunting method" width="550"/>




## Tips to "Fix the bug so the test passes"
* Change things: one thing at a time
* Question assumptions
* Reduce code to its essence
* document everything
* take a break
* ask for help




# Change things: one thing at a time
* different browser
* different computer
* use curl instead of browser




# Question Assumptions
* "check the plug"
* defaults
* follow the data




# Reduce the code to its essence




```python 
from pydantic import BaseSettings

class Settings(BaseSettings):
    test = 'okay'

    class Config:
        env_file = '.env'
        env_file_encoding = 'utf-8'

```




```python
from pydantic import BaseSettings
from dotenv import dotenv_values

class Settings(BaseSettings):
    test = 'okay'
    class Config:
        env_file = '.env'
        env_file_encoding = 'utf-8'

settings = Settings()
print(dotenv_values())
print(settings.dict())
```




```python
python3 test_silly.py
OrderedDict([('FASTAPI_ENV', 'development'),
  ('test_var2', 'hello')])
{'test': 'okay'}
```




```python 
from pydantic import BaseSettings

class Settings(BaseSettings):
    FASTAPI_ENV: str
    test_var2: str

    class Config:
        env_file = '.env'
        env_file_encoding = 'utf-8'

```




# Documenting and Comments
## Be kind to your teammates and future self




![alt text](assets/bug_joke.jpg "bughunting meme")




# Take a break
![alt text](assets/07-50-Ways-to-Take-a-Break-Illus-Info-07.jpeg "Karen Horneffer-Ginter, http://www.fullcupthirstyspirit.com/posters.php")




# Get some sleep
![alt text](assets/cat_sleeping.jpg "Lilo")




# Write down everything
* Exactly the call and result causing the problem
* Exactly what should have happened
* Any related log messages
* What you have tried and learned




# Ask for help
![alt text](assets/batphone.jpg "https://www.millionaireplayboy.com/toys/batphone.php")




## Don't be afraid to share your code
## Pair coding (or ensemble coding)
## for the win




## Tips to "Fix the bug so the test passes"
* Change one thing at a time
* Question assumptions
* Reduce code to its essence
* document everything
* take a break
* ask for help




## Basic Steps for Trouble Shooting
* Verify the bug
* Write things down
* Write a test that fails
* Understand the problem
* Fix the bug so the test passes
* <span style="background-color: #e6d300">Verify the bug is gone</span>




# Verify the bug is gone
If at all possible, have the person who reported the bug redo what they were attempting to do when the bug became evident.




# Hunting Bugs
* Background Information: bugs and stacks
* Basic Steps for Trouble Shooting
* <span style="background-color: #e6d300">Tools for Easier Bug Hunting</span>




## Tools for Easier Bug Hunting
* debugger
* tests
* cicd: (formatter, linter, tests)
* search engine




### Betty Snyder realized that if you wanted to debug a program that wasn't running correctly, it would help to have a *break point,* a moment when you could stop a program midway through its run. To this day, break points are a key part of the debugging process.
### *New York Times Magazine*
### "The Secret History of Women in Coding"




# PDB
* ### Python
* ### De-
* ### Bugger




# But print works
* Can be slow <!-- .element: class="fragment" data-fragment-index="1" -->
* forget what you are printing <!-- .element: class="fragment" data-fragment-index="2" -->
* how did I get here? <!-- .element: class="fragment" data-fragment-index="3" -->




# W
## where




```python
(Pdb) w
  /Users/maria/stack2.py(15)<module>()
-> add_to_stack()
  /Users/maria/stack2.py(13)add_to_stack()
-> print(divide_by_ten(my_num))
> /Users/maria/stack2.py(8)divide_by_ten()
-> return num/10
```
```python
Traceback (most recent call last):
  File "stack2.py", line 15, in <module>
    add_to_stack()
  File "stack2.py", line 13, in add_to_stack
    print(divide_by_ten(my_num))
  File "stack2.py", line 8, in divide_by_ten
    return num/10
```




# Move up an down the stack in the debugger




# Put a break point in code you believe your test should pass through




## import pdb; pdb.set_trace()




# Run your test




# All goes well, enter the pdb
## dir(some_variable)




# >>>WHOOSH>>>




# Leave the breakpoint in, Use a similar test




```python
(Pdb) w
  ~/python/bad_stack.py(15)<module>()
-> add_more_to_stack()
  ~/python/bad_stack.py(13)add_more_to_stack()
-> add_to_stack()
  ~/python/bad_stack.py(10)add_to_stack()
-> print(divide_by_ten(my_num))
> ~/python/bad_stack.py(6)divide_by_ten()
-> return num/10
(Pdb)
```




```python
1  def bad_function(num):
2      return str(num)
3
4  def divide_by_ten(num):
       import pdb; pdb.set_trace()
5      return num/10
6
7  def add_to_stack():
8      my_num = bad_function(4)
9      print(divide_by_ten(my_num))
10
11 add_to_stack()
```




```python
(Pdb) w
  ~/python/bad_stack.py(15)<module>()
-> add_more_to_stack()
  ~/python/bad_stack.py(13)add_more_to_stack()
-> add_to_stack()
  ~/python/bad_stack.py(10)add_to_stack()
-> print(divide_by_ten(my_num))
> ~/python/bad_stack.py(6)divide_by_ten()
-> return num/10
(Pdb)
```




```python
1  def bad_function(num):
2      return str(num)
3
4  def divide_by_ten(num):
5      return num/10
6
7  def add_to_stack():
8      my_num = bad_function(4)
       import pdb; pdb.set_trace()
9      print(divide_by_ten(my_num))
10
11 add_to_stack()
```




# Use the stack, go back and forth between the tests.




# Breakpoints in your own code are most useful




# Always suspect your own code first
## occasionally we find an error in an imported library
## but statistically speaking very rare...




## Tools for Easier Bug Hunting
* debugger
* tests
* cicd: (formatter, linter, tests)
* search engine




# Tests
* Make a New Test
* New Data (parameterize)




# Black, Pylint (Flake8), Mypy
## Put them in your cicd pipeline!




# Favorite Search Engine
* Sanitize the terms: Nothing unique
* Switch up your terms
* Understand what you find
* Even the professionals do it
#### https://localghost.dev/2019/09/everything-i-googled-in-a-week-as-a-professional-software-engineer/




## Basic Steps for Trouble Shooting
* Verify the bug
* Write things down
* Write a test that fails
* Understand the problem
* <span style="background-color: #e6d300">Fix the bug so the test passes</span>
* Verify the bug is gone




## Tips to "Fix the bug so the test passes"
* Change one thing at a time
* Question assumptions
* Reduce code to its essence
* document everything
* take a break
* ask for help




## Thank You
## May you win, not the bug
![bug_wins](https://media.giphy.com/media/qKbDKxfgWGWv6/giphy.gif "https://media.giphy.com/media/qKbDKxfgWGWv6/giphy.gif")
### https://codedragon.github.io/bughunting




## To learn how the real monty pythonistas bug hunt
https://www.youtube.com/watch?v=BHBbJAIcnBI
### https://codedragon.github.io/bughunting
### maria@mariakathryn.net
