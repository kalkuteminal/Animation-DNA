![](https://lh3.googleusercontent.com/-90kNXCym1kQ/VznLmU-hxOI/AAAAAAAAFno/0pT_n7X5Q90a7Fv0BCA-ky-NfB67H20jQCCo/s700/bannerDNA_tut_01.jpg)
# Animation DNA tutorials.
Section with software and Animation DNA pipeline techniques, tips and tricks.  
[Animation DNA quick start](01-Quick-start)  |  [Programming](#programming-with-pymel-for-artists)  |  [Arnold](#arnold-rendering-techniques)

## Programming with PyMel for artists
If you think that you have artistic brain and developing is beyond your possibilities, believe me, your just lazy. 

You dont need any unique knowledge or special brain structure. You just need willingness to code and necessity of practical application of developing(and you defiantly have it if you work in Maya).

Coding could be hard only at the beginning, but the more you will practice the easy it will be for you. And finally you will realize that coding is also an art

**A)** [Theory](#programming-theory)  
  [Intro](#introduction-to-artistic-developing )  |  [PyMel basics](#developing-foundation)  |  [Developing example](#step-by-step-example)  |  [Art of good code](#art-of-good-code)  
**B)** [Practice](#programming-practice)  
  [Attributes](#attributes)  |  [Objects](#objects)  |  [Files](#files)  |  [Lists](#lists)  |  [Strings](#string-formatting)  |  [Rendering](#rendering)  |  [Interfaces](#interfaces)  |  [FTrack](#ftrack-examples)

### Programming theory
[Intro](#introduction-to-artistic-developing )  |  [PyMel basics](#developing-foundation)  |  [Developing example](#step-by-step-example)  |  [Art of good code](#art-of-good-code)
#### Introduction to artistic developing 
From the beginner point of view programming in Maya allow us to execute particular action with many objects at once.
  
For example, double the intensity of all lights in scene.

Programs allow to automate a lot of process and shift human work to computer shoulders. Also, computer does nod make a mistakes, so result of execution of correct code will be stable and predictable. Every action that you can express as a chunk of code should be scripted. 

##### Starting point for all code
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

##### Running code from a file
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

##### Artistic way of writing code
Artistic way of writing code is [finding MEL commands and object attributes](#sample-developing) in Script Editor in conjunction with [asking google](#developing-with-google) how to do something in PyMel. 

#### Step by step example
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
To formulate procedure we will use [variable](#variables) named **"valueCurrent"** for data exchange — store source intensity value for multiplication operation. Result of multiplication will store in variable **"valueResult"**. You can give any name to variables but better use [nice and descriptive names](02-codex-dna#naming). The attribute we will operate is **"intensity"**.

```python
valueCurrent = object.intensity.get()
valueResult = valueCurrent*2
object.intensity.set(valueResult)
```

We need to use loop to apply procedure of multiplication of intencity to each element of list (list contain set of all lights in your scene)

```python
import pymel.core as pm
listOfLights = pm.ls(lights=True)

for object in listOfLights:
    valueCurrent = object.intensity.get()
    valueResult = valueCurrent*2
    object.intensity.set(valueResult)

```
When you code become more complex you will find useful creating "reports" of code execution. It could be done with **`print 'any data you need to see '`** command which write in scrip editor any data you need. Here we print massage inside quotes `print 'message'` and replace `{number}` with variable values in brackets `.format(value)`:

```python
import pymel.core as pm
listOfLights = pm.ls(lights=True)

for object in listOfLights:
    valueCurrent = object.intensity.get()
    valueResult = valueCurrent*2
    object.intensity.set(valueResult)
    print 'object: {0} intensity: {1} >> {2}'.format(object, valueCurrent, valueResult)
```
Reducing code

```python
import pymel.core as pm
listOfLights = pm.ls(lights=True)
for i in listOfLights:
    i.intensity.set(i.intensity.get()*2)
```

Creating a PyMel **function** from block of code with ability to change multiplication value:

```python
def litDouble(value):
    listOfLights = pm.ls(lights=True)
    for i in listOfLights:
        i.intensity.set(i.intensity.get()*value)
```

Running a function:
```python
litDouble(value):
```
If your will be able to build [interface](#interfaces) for this function you can consider you are PyMel developer. 

#### Art of good code
When you will pass first painful steps and get awkward blocks of more or less working code you will need to move forward in developing. There are some rules which you need to obey to make next step:
* Comment basic actions
* Give nice and descriptive names
* Clean up code from unnecessary data

##### Code characteristics
`code scope = correctness*3 + design*2 + style`

### Programming practice
Here you will find procedures for most common tasks in Maya.

[Attributes](#attributes)  |  [Objects](#objects)  |  [Files](#files)  |  [Lists](#lists)  |  [Strings](#string-formatting)  |  [Rendering](#rendering)  |  [Interfaces](#interfaces)  |  [FTrack](#ftrack-examples)

#### Attributes
##### Get objects by attribute
```python
listAtr = pm.ls('*.nameOfAttribute')
for i in listAtr: 
    object = i.node()
```

##### Add string attribute to selected objects
```python
def addString(attrName):
    sel = pm.ls( sl=1 )
    for i in sel:
        if not pm.attributeQuery( attrName, node = i, exists = True ):
            pm.addAttr(i, ln = attrName, nn = attrName, dt = 'string')
```

##### Add color attribute to selected objects
```python
def addColor(attrName):
    sel = pm.ls( sl=1 )
    for i in sel:
        pm.addAttr(i, longName = attrName, niceName = attrName , usedAsColor = True, attributeType = 'float3' )
        pm.addAttr(i, longName='R' +  str(attrName), attributeType='float', parent=attrName )
        pm.addAttr(i, longName='G' +  str(attrName), attributeType='float', parent=attrName )
        pm.addAttr(i, longName='B' +  str(attrName), attributeType='float', parent=attrName )
```

##### Set string attribute for selected objects
```python
def setString(attribute, value):
    sel = pm.ls(sl=1)
    for i in sel:
        i.attr(attribute).set(value)
```
##### Lock attribute of selected objects
```python
def attrLock(attribute):
    sel = pm.ls(sl=1)
    for i in sel:
        i.attr(attribute).lock()
```

#### Objects
##### Get shapes of selected objects
```python
listShapes =  pm.ls(dag=1,o=1,s=1,sl=1)
```
 
##### Create PyMel object by name
```python
object = pm.PyNode('nameOfNode')
```

##### Unlock and delete selected nodes
```python
def unlockAndDelete():
    sel = pm.ls( sl = True )
    for i in sel:
        i.unlock()
        pm.delete(i)
```

##### Select instances of selected objects
```python
def selectInstances():
    pm.select(pm.ls(ap = 1, dag = 1, sl = 1 ))
```

##### Create animated Arnold standin and set path
```python
def addStandin():
    standin = pm.createNode('aiStandIn', name = 'STANDIN')
    standin.dso.set('D:/DNA/PROD/3D/cache/standin.####.ass')
    standin.useFrameExtension.set(1)
    pm.expression(ae = True, s = '{0}.frameNumber = frame'.format(str(standin)) )

```

##### Triger bounding box display of selected objects
```python
def boundingBox():
    pm.pickWalk(d ='down')
    sel = pm.ls(sl = 1, shapes = 1, selection = 1)
    if (sel[0].overrideEnabled.get() == 0):
        for i in sel:
            i.overrideEnabled.set(1) 
            i.overrideLevelOfDetail.set(1)
    else:
        for i in sel:
            i.overrideEnabled.set(0) 
            i.overrideLevelOfDetail.set(0)
```
#### Files
##### Basic Maya scene file manipulations 
```python
pm.sceneName() # Get name of current scene
pm.importFile(fullPath) # Import file
pm.exportSelected(fullPath) # Export selected to a file
```
##### list files in directory
```python
import glob
listExisted = glob.glob('D:/DNA/images/*.jpg')
```

##### Create reference
```python
pm.createReference(fullPath, sharedNodes =('shadingNetworks', 'displayLayers', 'renderLayersByName') , ns = nameSpace )
```
##### Get full path of reference by namespace
```python
fullPathRef = pm.FileReference(namespace = 'nameSpace')
```
##### Replace reference
```python
fullPathRef.replaceWith(fullPathRefNew)
```

##### Export alembic
```python
from maya.mel import eval
eval('AbcExport -j " -framerange {2} {3} -uvWrite -root {0} -file {1}"'.format(groupName, pathABC, frameStart, frameEnd))
```
##### Import alembic
```python
from maya.mel import eval
eval(' AbcImport -ct  "{0}" "{1}" '.format(groupName, pathABC))
```

#### Lists
##### Create list by object name 
```python
list = pm.ls('nodeName') # With exact name
list = pm.ls('prefix_*') # With exact part
list = pm.ls('*:nodeName') # With namespaces
```

##### Cut last element from a list 
```python
list = ['A', 'B', 'C','D','E']
listLast = list.pop(-1)
```
##### Dictionary
```python
dataShotDic = {'characters' : [ ], 'props' : [] , 'environment' : [] , 'EDA' : [] , 'endFrame' : []} 
dataShotDic['characters'].append( <assetName> )
```

#### String formatting
##### Replace string with variables
```python
'variable A = {0}, variable B = {1}'.format(variable_A, variable_B) 
```
##### Replace number with padding
```python
'{0:3d}'.format(1) # result: 001
```

##### Divide string 
```python
string = 'D:/projects/DNA/3D/scenes'
split = string.split('/')
# Result: ['D:', 'projects', 'DNA', '3D', 'scenes']
```
#### Rendering
##### Set current render to Arnold 
```python
def setArnold(*args):
    if( pm.getAttr( 'defaultRenderGlobals.currentRenderer' ) != 'arnold' ):
        pm.setAttr('defaultRenderGlobals.currentRenderer', 'arnold')
```

##### Create Arnold AOV
```python
import mtoa.aovs as aovs
def addAOV(aovName):
    aov = aovs.AOVInterface().addAOV(aovName)
    return aov
```

##### Arnold export ass 
```python
# use `s = True` for selected
pm.arnoldExportAss( f = "D:/fileName.ass",  startFrame = 0, endFrame = 1 )
```

##### Asign material for selected **object shape**
```python
def matAsign(material):
    sel = pm.ls(sl=1)
    for i in sel:
        pm.sets(material, forceElement = i)
```
##### Get shading group and shader of **object shape**
```python
shadingGroup = pm.listConnections(objectShape, type='shadingEngine')
shader = pm.ls(mc.listConnections(shadingGroup), materials = 1)
```

##### Get image files of material
```python
imageFiles = pm.listHistory(shadingGroup, type='file')
```
##### Select shading groups of selected objects
```python
def selSG():
    list =  pm.ls(dag=1,o=1,s=1,sl=1) 
    shadingGrps = pm.listConnections(list,type='shadingEngine')
    pm.select(clear = True)
    SGS = pm.select(shadingGrps, ne = 1)
```

##### Create shader, image file and shading group. Make shader connections. 
```python
shader = pm.shadingNode ('lambert', asShader = True, name = 'MATERIAL') 
imageFile = pm.shadingNode ('file', asTexture = True, n = 'TEXTURE' )
SG = pm.sets (renderable = True, noSurfaceShader = True, empty = True, name = shader + 'SG')
imageFile.outColor >> shader.color
shader.outColor >> SG.surfaceShader
```

##### Render settings for Arnold
```python
# create an objects from render settings nodes
rgArnold = pm.PyNode('defaultArnoldDriver')
rgArnoldRO =  pm.PyNode('defaultArnoldRenderOptions')
rgCommon = pm.PyNode('defaultRenderGlobals')
rgRes = pm.PyNode('defaultResolution')

rgCommon.imageFilePrefix.set('D:/fileName') # Set image file path and name

rgArnold.aiTranslator.set('exr') # Set image format to EXR

rgArnoldRO.AASamples.set(12) # Set antialiasing samples

# Set resolution
rgRes.width.set(1998)
rgRes.height.set(1080)
```

#### Interfaces
##### Window with text field and button.
Pressing a button prints value of text field.
```python
def printValue(input):
    print 'Value in text field: {0}'.format(input.getText())
    
def baseUI(): 
    if pm.window('BASE', exists = 1):
        pm.deleteUI('BASE')
    baseWin = pm.window('BASE', t = 'Base Window', w = 280, h = 100)
    with baseWin:
        
        mainLayout = pm.columnLayout()
                    
        aLayout = pm.rowColumnLayout(nc = 2, parent = mainLayout)   
        stringField = pm.textField(tx = 'TEXT', w= 90, h = 40) 
        buttonPrint = pm.button(l = 'PRINT FIELD VALUE', w = 190)
        buttonPrint.setCommand(pm.Callback (printValue, stringField))
       
    baseWin.show()  
baseUI()
```

##### Confirm dialog
A good option to catch events and create variations of next steps.  
For example: File exists > overrdide or save next verion.
```python
confirm = pm.confirmDialog ( title = 'Title', message = 'Message', button=['OK', 'CANCEL'], cancelButton= 'CANCEL' )
if confirm == 'OK':
    print 'Pressed OK'    
else:
    sys.exit('Canceled!')
```

#### FTrack examples
See [FTrack setup](02-codex-dna#management-with-ftrack) and [glossary of codes](04-Glossary#codes) sections in documentation. Used API is 3.3.1

##### Setup path to API
```python
import os
os.environ['PYTHONPATH'] = 'C:/FTrack_API'
```
##### Login to FTRack
```python
import os
os.environ['FTRACK_SERVER'] = 'https://<userAdress>.ftrackapp.com'
os.environ['FTRACK_APIKEY'] = '<API_key>'
os.environ['LOGNAME'] = '<userName>'
```

##### Get project data
```python
import ftrack
projectFTrack = ftrack.getProject(<codeProject>)
```

##### Get asset data
```python
import ftrack
dataAsset = projectFTrack.getAssetBuilds().find('name', <assetName>)
dataAssetMeta = dataAsset.getMeta() # Get asset metadata
```

##### Get shot data
```python
import ftrack
dataShot = ftrack.getShotFromPath([<codeProject>,<codePart>,<codeSequence>,<codeShot>])
listShotLinks = dataShot.getPredecessors() # Get linked assets
frameEnd = dataShot.getFrameEnd() # Get end frame
shotMetaData = dataShot.getMeta() # Get shot metadata
```

##### Get data of assets linked to a shot
```python
for i in listShotLinks :
    assetName = i.getName()
    assetCategory = i.getType().getName() # Environments, props, characters 
```

##### Add metadata to an asset
```python
import ftrack
assetData = projectFTrack.getAssetBuilds().find('name', <assetName>)
assetData.setMeta( <key>, <value> ) 
```

##### Add metadata to a shot
```python
import ftrack
shotData = ftrack.getShotFromPath([<codeProject>,<codePart>,<codeSequence>,<codeShot>]) 
shotData.setMeta( <key>, <value> )
```

## Arnold rendering techniques
#### Setup per object attributes
We can use [tokens](https://support.solidangle.com/display/AFMUG/Tokens) to set individual values for the same attribute on different objects. Tokens in general can be useful if you want to get some information from the shape of objects during rendering process, e.g. set individual texture placement attributes with the same place2dTexure node, set unique color for each object etc. 

Grate example of using tokens is  [Multitexture material](#multitexture-material)

![](http://4.bp.blogspot.com/-8kVvlGXNhvA/UydifSkz2xI/AAAAAAAAEgU/ILczrfAPS1c/s1600/shapeShading.gif)


#### Multitexture material
You can reduce amount of shaders in scene and speed up look development with one material and individual textures on each object. With such setup, object shapes share the same material but has their own textures. 

![](http://3.bp.blogspot.com/-a6Z3LOGF1k8/Uvz7CiVdKFI/AAAAAAAAEZo/o2JYAj8AJ3s/s1600/aiMultitexture.gif)
Method:
- Create string attribute on object shape with the name `mtoa_constant_<attrName>` 
- Enter attribute token `< attr:<attrName> >` in Image Name field of file node with **full absolute path** to texture.  
For example: `D:/DNA/3D/sourceimages/<attr:mColor>`  
It become relative immediatley (`sourceimages/<attr:mColor>`) but if you enter relative path from the beginning it would not work.
- Enter desirable texture name in `mtoa_constant_<attrName>` attribute of each object shape.

You can create and set Arnold custom attributes on object shapes with [Attribute Manager](03-Tools#attribute-manager)

#### Object and material AOVs
You can create special path with selection mask of objects or shaders for compositing software.

![](https://3.bp.blogspot.com/-VEowRHSseXY/UwH9OIKi3mI/AAAAAAAAEag/kIHH-SeIzys/s1600/aiIDs.gif)

##### Material AOV
To create AOV for any shader we use **aiWriteColor** node.

##### Object AOV
To create AOV for any object we create custom color attribute on each object and corresponding AOVs in render settings.

Create AOVs automatically with [Render Manager](03-tools#render-manager)