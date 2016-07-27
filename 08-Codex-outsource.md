![](https://lh3.googleusercontent.com/-ftAiFMX-a5k/V5dnNjoFaqI/AAAAAAAAFxM/9uSnFpG22xUfbZcgGxX1cjPEE-Nat02WACCo/s2048/bannerDNA_outsource_02.jpg)
# Outsourcing general notes
Any data of each project physically exists on studio network drive.  
Each member of the studio team works with this drive only, no project data could be stored locally.  
To outsource any part of work we create FTP server with project copy on it with the same folder structure.  
**Outsource company should replicate studio folder structure on their own network drive exactly** and copy all necessary data from FTP to a corresponding location.  
**DO NOT CHANGE THE NAME of any file your work with**, the only part you can vary is [version](02-Codex-DNA#naming)!  
Software also should be matched to studio software list exactly.  
#### Data exchange
Each department produce some data which need to be translated to other departments.  
In studio data transfer between departments occurs automatically with [Animation DNA tools](03-Tools).  
If for any reason outsource company do not integrated into studio pipeline it should output data manually according to a strict rules, which basically covers location and names of files for different data types. See details in "**Data exchange**" section for each department in [Projects specifications](#projects-specifications) part.
#### Integration to studio pipeline
It is recommended for outsource studios to integrate to [Animation DNA](https://github.com/kiryha/AnimationDNA/wiki) pipeline more in depth, than just replicate folder structure. It can dramatically speed up production and simplify problem solving.

The minimum requirements for pipeline integration are:
- Access to [FTrack database](02-Codex-DNA#management-with-ftrack) of the project for outsource studio
- Using [DNA.rar](02-codex-dna#dna-archive) to create project folder with required data 

# Prepare data for outsource
#### Animation phase
See how to [create animation scene](02-Codex-DNA#creation-of-animation-scenes)
#### FX phase
See how to [create FX scene](02-Codex-DNA#creation-of-common-fx-scenes)

# Projects specifications
In this section located information specific for particular projects.
## The dragon spell
![](https://lh3.googleusercontent.com/-wuigHU_vv84/V5d10Ai3BXI/AAAAAAAAFxw/pkJLPV7px6oPsBfSt-AQ104a2EMr12tkQCCo/s2048/bannerDNA_KZM_01.jpg)
### Folder structure
Create network drive **`P`** and locate **`TANNER`** folder there so `<rootProject> = P:/TANNER/`  
Set Maya project to `<root3D> = P:/TANNER/PROD/3D/`  

![](https://lh3.googleusercontent.com/-wP8I4iwB3ig/V5d5X6sC0tI/AAAAAAAAFx8/-VPrt-eidc8T14V2pZJ9XoHiwAgd5Ei4QCCo/s2048/projectSetup_02.gif)

### Integration to studio pipeline
Blank folder structure: `P:\TANNER\PREP\MANAGE\TOOLS\FOLDERS_BLANK\TANNER.rar`  
Extract archive content (TANNER folder) to drive P:/

[Wrapper](02-codex-dna#running-maya-and-nuke-with-wrappers) for Maya: `P:\TANNER\PREP\MANAGE\TOOLS\WRAPPER\wrapperMaya.rar`  
Extract archive content to `P:\TANNER\PROD\3D\scripts` and run **runMaya.bat**

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

The full list of FX in "The Dragon spell" project: `P:\TANNER\PREP\MANAGE\LISTS\ListVFX.xls `

Breaf with artwork for each FX located in **FX task** of corresponding shot in [FTrack](02-Codex-DNA#management-with-ftrack)
