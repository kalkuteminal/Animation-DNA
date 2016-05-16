![](https://lh3.googleusercontent.com/-90kNXCym1kQ/VznLmU-hxOI/AAAAAAAAFno/0pT_n7X5Q90a7Fv0BCA-ky-NfB67H20jQCCo/s700/bannerDNA_tut_01.jpg)
# Tutorials

## Getting started with PyMel
### Beginning of developing
#### Step one
All you need to write first block of code is open Python tab of Maya Script Editor and enter:  
`import pymel.core as pm`
This is what all your code will start from. After that line you will place procedures which will to solve particular tasks.

#### Running code from a file

```python
a = pm.listConnections('METALSG')
listTrs = []
for i in a:
    if pm.nodeType(i) == 'transform':
        listTrs.append(i)
print listTrs
```