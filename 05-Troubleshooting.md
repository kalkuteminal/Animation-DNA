![](https://lh3.googleusercontent.com/-xE3m9LwLVoA/VzMoTTUqEOI/AAAAAAAAFlQ/qFlXw_x4ydkAZBW6_yJX_yLiKJXdfVdDACCo/s700/bannerDNA_trouble_01.jpg)

## Troubleshooting general notes
If [Animation DNA Tools](03-tools) usage cause error message you has to find reason of error and fix it.  
This section contain common error description and ways to solve them.

**Script editors** history window is your best friend when you work with Animation DNA toolset. Each main block of executed code supported with readable print massages, and you can learn what is going on in this moment and if something went wrong — which procedure cause an error.

Always keep an eye on script editor, pressing each button should bring success message after finishing procedures. 

## Errors by tools 
### Shot assembler
#### Create render scene
**`Error: KeyError: file <rootProject>/PREP/PIPELINE/dnaCore.py line 130: MAT`**  
Reason: You did not [publish material](01-quick-start#look-development) for an assets, linked to a shot.

### FX manager
#### CREATE FUR SIM SCENE
**`# Error: ValueError: file <maya console> line 70: invalid literal for int() with base 10: '<anyTextHere>' # `**  
Reason: There are files with wrong names in [folder with fur for shot](02-Codex-DNA#fur-workflow)