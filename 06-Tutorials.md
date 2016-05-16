![](https://lh3.googleusercontent.com/-90kNXCym1kQ/VznLmU-hxOI/AAAAAAAAFno/0pT_n7X5Q90a7Fv0BCA-ky-NfB67H20jQCCo/s700/bannerDNA_tut_01.jpg)
# Tutorials

## Getting started with PyMel
### Beginning of developing
#### Step one
All you need to write first block of code is open Python tab of Maya Script Editor and enter:  
`import pymel.core as pm`
This is what all your code will start from. After that line you will place procedures which will to solve particular tasks. 

As an original example lets write a procedure which will print: **Hello World!**
```python
import pymel.core as pm
print 'Hello World!'
```
To run code you can:
- press **ExecuteAll** button of script editor
- drag your code with MMB to a shelf and press the button that will appear

#### Running code from a file
If you need to run python code from a file: 
- save your code as **`*.py`** file in certain place
- let Maya know this place by running:
```python
import os
os.environ['PYTHONPATH'] = <pathToFile>
```
- import code
```python

```