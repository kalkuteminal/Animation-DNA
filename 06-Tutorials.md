![](https://lh3.googleusercontent.com/-90kNXCym1kQ/VznLmU-hxOI/AAAAAAAAFno/0pT_n7X5Q90a7Fv0BCA-ky-NfB67H20jQCCo/s700/bannerDNA_tut_01.jpg)
# Tutorials

## Programming with PyMel for artists
### Getting started  
From the beginner point of view programming in Maya allow us to:
- execute particular actions with many object at once.  
For example, double the intensity of all selected lights.
- execute number of the same actions with a different objects.  
For example, export/import character animation for each shot.

Programs allow to automate a lot of process and shift human work to computer shoulders. Also, computer does nod make a mistakes, so result of execution of correct code will be stable and predictable. Every action that you can express as a chunk of code should be scripted. 

#### Step one
All you need to write first block of code is open Python tab of Maya Script Editor and enter:  
`import pymel.core as pm`  
This is what all your code will always start from. After that line you will place procedures which will to solve particular tasks. 

As an original example lets write a procedure which will print: **Hello World!**
```python
import pymel.core as pm
print 'Hello World!'
```
To run code you can:
- press **ExecuteAll** button of script editor
- drag your code with MMB to a shelf and press the button that will appear

#### Step two: lists and loops.
Lists and loops are bases of coding. Loops allow us to do something (command) with a set of objects (list). So we have two major tasks in developing:
- creating and editing lists
- writing procedures (set of commands)  


Loop allow to apply **procedure** to a **list**:
```python
for eachObject in listOfObjects:
    run command
```

#### Running code from a file
If you need to run python code from a file: 
- save your code as **`*.py`** file in a desired place (C:/hello.py)
- let Maya know this place by running in script editor: `sys.path.append('C:/')`
- import code `import hello`

The best option to setup path for your scripts and run them in Maya is using [wrapper](02-codex-dna#running-maya-and-nuke-with-wrappers). In this tutorials we will run code from Script Editor only. 

#### Coding with google
Probably, all basic task you need to solve somebody already did. Now days you can start to write your code by asking google proper questions. Sure, you have be familiar with python syntax and basic Maya commands and writing first block of working code may take days but the more you will practice the faster you will code.

Lets try to double intensity of all lights in the scene. Search for: select all lights pymel. At the bottom of first page in example section you will find a command which contain "light":  
**`pm.ls( geometry=True, lights=True, cameras=True )`**