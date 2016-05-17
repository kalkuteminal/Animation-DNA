![](https://lh3.googleusercontent.com/-90kNXCym1kQ/VznLmU-hxOI/AAAAAAAAFno/0pT_n7X5Q90a7Fv0BCA-ky-NfB67H20jQCCo/s700/bannerDNA_tut_01.jpg)
# Programming with PyMel for artists
If you think that you have artistic brain and developing is beyond your possibilities, believe me, your just lazy. 

You dont need any extra knowledge, like math or physics. You just need willingness to code and necessity of practical application of developing(and you defiantly have it if you work in Maya).

Coding could be hard only at the beginning, but the more you will practice the easy it will be for you. And finilyy you will realize that coding is also an art

A) [Theory](#programming-theory)  
B) [Examples](#programming-practice)

## Programming theory
### Introduction to artistic developing 
From the beginner point of view programming in Maya allow us to execute particular action with many objects at once.
  
For example, double the intensity of all lights in scene.

Programs allow to automate a lot of process and shift human work to computer shoulders. Also, computer does nod make a mistakes, so result of execution of correct code will be stable and predictable. Every action that you can express as a chunk of code should be scripted. 

#### Starting point for all code
All you need to write first block of code is open Python tab of Maya Script Editor and enter:  
`import pymel.core as pm`  
This is what all your code will always start from. After that line you will place [procedures](#vocabulary-of-artistic-developer) which will solve particular tasks. 

As an original example lets write a procedure which will print: **Hello World!**
```python
import pymel.core as pm
print 'Hello World!'
```
To run code you can:
- press **ExecuteAll** button of script editor
- drag your code with MMB to a shelf and press the button that will appear
- save code in a file and execute it in Maya from file

#### Running code from a file
If you need to run python code from a file: 
- save your code as **`*.py`** file in a desired place (C:/hello.py)
- let Maya know this place by running in script editor: `sys.path.append('C:/')`
- import code `import hello`

The best option to setup path for your scripts and run them in Maya is using [wrapper](02-codex-dna#running-maya-and-nuke-with-wrappers). In this tutorials we will run code from Script Editor only. 

#### Developing foundation
##### Lists and loops
Lists and loops are bases of coding. Loops allow us to do something (command) with a set of objects (list). So we have two major tasks in developing:
- creating and editing lists
- writing procedures (set of commands)  

Loop allow to apply **procedure** to a **list**:
```python
import pymel.core as pm
for eachObject in listOfObjects:
    command
```
##### Variables
When you create a list, you need to keep this list somewhere to use it later. Your store objects or data in **variables**. In this code **list** is a variable: **`list = [object_A, object_B, object_C]`** which contain set of 3 objects.

##### Coding algorithm.
Performing majority of projects goes from rough form in the beginning to refined result at the end. From general to specific. Writing code usually will flow vice versa: 
- you find a command that will do your action
- you find a way to perform a particular command to a concrete object 
- you find a way to generalize code: obey command to work with input list of necessary objects in all possible cases   

##### Developing with google
Probably, all basic task you need to solve somebody already solved. Now days you can start to write your code just by asking google a proper questions. Proper question is a grate part of answer and this mean you have to find correct question to get necessary answer but google is smart and auto complete will help you even with that. 

Sure, you have be familiar with python syntax and basic Maya commands and writing first block of working code may take days but the more you will practice the faster you will code.

##### Sample developing
When you need to apply some action to an object or list, this basically mean that you need to find a proper **command** that will execute necessary action.

Maya has awesome feature which allow to start writing code without any preliminary preparation. Anything your do in interface is written as Maya Embed Language (MEL) code in Script Editor. The name of MEL command usually the same as name of PyMel command, so often finding a command is an easy task.

Inspecting MEL messages is also a way to find an **attribute** to deal with. 

##### Vocabulary of artistic developer
**OBJECT** — anything you need to deal with in your code (Maya scene, light, shape attribute etc).  
**LIST** — set of objects.  
**COMMAND** — action that you need to apply to object.  
**PROCEDURE** — is a set of commands.  
**VARIABLE** — container for data.

**Artistic way of writing code** is [finding MEL commands and object attributes](#sample-developing) in Script Editor in conjunction with [asking google](#developing-with-google) how to do something in PyMel. 

### Step by step example
Lets try to double intensity of all lights in the scene.  
[Search for](#developing-with-google): select all lights pymel. Go to the first link, at the bottom of the page in example section you will find a command which contain "light": **pm.ls( geometry=True, lights=True, cameras=True )**   

**`pm.ls`** is a command which allow to create [lists](#developing-foundation). This is **command #1** your will deal with. Best friend for creating lists! 

To store list of lights in a variable:  
```python
import pymel.core as pm
listOfLights = pm.ls(lights=True)
```

Now we just need to [find a way](#sample-developing) to double light intensity with PyMel using [coding algorithm](#coding-algorithm). 

Select any light in scene, change intensity value and look into history window of Script Editor where you should find result of you action in MEL language:  
**`setAttr "spotLightShape1.intensity" 2;`**  
It tells you: i set intensity attribute of spotLight to 2.

You have several syntax options to set attributes in PyMel. We can "translate" MEL above into python:  
```python
import pymel.core as pm
pm.setAttr('spotLightShape1.intensity', 2)
```
So you have list of objects, you know attribute to work with, you know the command. Now you need to formulate a task (double the intensity) as a PyMel procedure.

Double mean multiply by 2. E.g. you need to get intensity value of each light, multiply by 2 and finally set intensity value with a result of multiplication.

Find intensity value possible with **`getAttr`** command:
```python
import pymel.core as pm
pm.getAttr('spotLightShape1.intensity')
```

All this chunk of codes works separately with a particular object spotLightShape1. We need to join them and [generalize](#coding-algorithm) to get working program for any scene. Another way to get or set attributes is:

```python
object.attribute.get()
object.attribute.set(value)
```
To formulate procedure we will use [variable](#variables) named "valueCurrent" for data exchange — store source intensity value for multiplication operation. Result of multiplication will store in variable "valueResult". You can give any name to variables but better use [nice and descriptive names](02-codex-dna#naming).

```python
valueCurrent = object.attribute.get()
valueResult = valueCurrent*2
object.attribute.set(valueResult)
```

We need to use loop to apply procedure of multiplication of intencity to each element of list (list contain set of all lights in your scene)

## Programming practice
### Attributes
### Objects
### Materials