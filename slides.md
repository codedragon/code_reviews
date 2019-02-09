# Hunting the bugs

## Maria Mckinley




![alt text](assets/Emperor_Gum_Moth.jpg "https://en.wikipedia.org/wiki/Moth#/media/File:Emperor_Gum_Moth.jpg")




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




## In a simple stack trace, the problem is usally at the bottom, and the code that caused it directly above it.




```
python3 except_excercise.py
  File "except_excercise.py", line 2
    from __future__ import braces
    ^
SyntaxError: not a chance
```
