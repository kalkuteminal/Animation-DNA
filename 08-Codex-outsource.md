# Outsourcing general notes
Any data of each project physically exists on studio network drive.  
Each member of the studio team works with this drive only, no project data could be stored locally.  
To outsource any part of work we create FTP server with project copy on it with the same folder structure. Outsource company should replicate studio folder structure on their own network drive and copy all necessary data from FTP to a corresponding location.  
Software also should be matched to studio software list exactly.  
#### Data exchange
Each department produce some data which need to be translated to other departments.  
In studio data transfer between departments occurs automatically with [Animation DNA tools](03-Tools).  
If for any reason outsource company do not integrated into studio pipeline it should output data manually according to a strict rules, which basically covers location and names of files for different data types. See details in "**Data exchange**" section for each department in [Projects specifications](#projects-specifications) part.

# Prepare data for outsource
#### Animation phase
See how to [create animation scene](02-Codex-DNA#creation-of-animation-scenes)
#### FX phase
See how to [create FX scene](02-Codex-DNA#creation-of-common-fx-scenes)

# Projects specifications
In this section located information specific for particular projects.
## The dragon spell
### Folder structure
Create network drive `**P**` and locate `**TANNER**` folder there so `<rootProject> = P:/TANNER/`  
`<root3D> = P:/TANNER/PROD/3D/`  

Recommended to use empty folder structure in conjunction with [wrapper](02-codex-dna#running-maya-and-nuke-with-wrappers) to integrate into our pipeline more deep and speed up production.

Blank folder structure: `P:\TANNER\PREP\MANAGE\TOOLS\FOLDERS_BLANK\TANNER.rar`  
Wrapper for Maya: `P:\TANNER\PREP\MANAGE\TOOLS\WRAPPER\wrapperMaya.rar`

### Required software and plugins
3D [branch](02-Codex-DNA#structure-of-film-and-production):
- Maya 2015 Extension 1 Service Pack 5

Animation [phase](02-Codex-DNA#structure-of-film-and-production):  
- Animation Manager script  
Script location `P:\TANNER\PREP\MANAGE\TOOLS\ANM\animManagerOut.py` 
- Studio library plugin for Maya  
Script location `P:\TANNER\PREP\MANAGE\TOOLS\ANM\Picker_2015_64\`
- Picker  
Script location `P:\TANNER\PREP\MANAGE\TOOLS\ANM\studiolibrary\`

### Data exchange for FX branch
In addition to main [Maya FX scene](02-Codex-DNA#creation-of-common-fx-scenes) for each FX in each shot there could be more data types to transfer (open VDB and alembic caches, renders etc). You can find instructions for each data type in [Common FX workflow](02-Codex-DNA#common-fx-workflow) section.

