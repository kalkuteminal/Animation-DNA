# Outsourcing general notes
Each project data physically exists on studio network drive.  
To outsource any part of work we create FTP server with project copy on it with the same folder structure. Outsource company should replicate studio folder structure on their own network drive and copy all necessary data from FTP to a corresponding location.  
Software also should be matched to studio software list exactly.  

# Project specifications
## The dragon spell
### Folder structure
`<rootProject> = P:/TANNER/`  
`<root3D> = P:/TANNER/PROD/3D/`  

Recommended to use empty folder structure in conjunction with [wrapper](02-codex-dna#running-maya-and-nuke-with-wrappers) to integrate into our pipeline more deep and speed up production.

Blank folder structure: `P:\TANNER\PREP\MANAGE\TOOLS\FOLDERS_BLANK\TANNER.rar`  
Wrapper for Maya: `P:\TANNER\PREP\MANAGE\TOOLS\WRAPPER\wrapperMaya.rar`

### Required software and plugins
Any user:
- Maya 2015 Extension 1 Service Pack 5

Animation branch:  
- Animation Manager script  
Script location `P:\TANNER\PREP\MANAGE\TOOLS\ANM\animManagerOut.py` 
- Studio library plugin for Maya  
Script location `P:\TANNER\PREP\MANAGE\TOOLS\ANM\Picker_2015_64\`
- Picker  
Script location `P:\TANNER\PREP\MANAGE\TOOLS\ANM\studiolibrary\`