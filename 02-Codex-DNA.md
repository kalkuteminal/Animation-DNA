![](https://lh3.googleusercontent.com/-wGO0rrbAXi0/Vx-DTNUE5TI/AAAAAAAAFb0/2gGhdnyoxz4pqy1KVgAQXV-XkDAE6wEegCCo/s700/bannerDNA_home_02.jpg)

## Animation DNA Introduction and general notes.
To optimize and speed up shots production process, proper system should be developed and implemented. This system calls **PRODUCTION PIPELINE**. Production pipeline consist from a set of rules and tools for every branch, phase, procedure and action. Rules define relations between branches and phases, tools allow to execute actions automatically. The main goals of pipeline are: distribution of work between team members, automatisation of actions and procedures, make workflow flexible to changes.  
**Codex DNA** is set of instructions for computer graphic which establish workflow for creation an animation movie.

**A)** [General notes](#general-notes):  
  [Structuring](#structuring) | [Naming](#naming) | [Quality control](#quality-control)  
**B)** [Pipeline overview](#pipeline-overview):  
 [DNA.rar](#dna-archive) | [Wrapper](#running-maya-and-nuke-with-wrappers) | [Pipeline brief](#pipeline-brief) | [FTrack](#management-with-ftrack) | [Outsource](#workflow-with-outsource-studios) | [Shot creation](#shot-creation-workflow)    
**C)** [3D branch](#3d-branch):  
 [3D overview](#3d-branch-general-notes)  | [3D pipeline](#pipeline-development-and-data-transfer) | [Asset creation](#asset-creation) | [Layout and animation](#layout-and-animation) | [Lookdev](#look-development-and-rendering) | [FX](#fx)    
**D)** [2D branch](#2d-branch):  
 [2D overview](#2d-branch-general-notes) | [Procedure](#compositing-procedure) | [Output](#output-from-2d-branch)    
**E)** [Art](#art)  
**F)** [Editing and grading](#edit-and-grading)

## General notes
[Structuring](#structuring) | [Naming](#naming) | [Quality control](#quality-control)
### Structuring
To solve complex task (or operate with a big amount of data) it must be splited into smaller pieces. This process of dividing big amount of data into smaller parts according to a particular model is called structuring and structuring is a basement of organisation.
![](https://lh3.googleusercontent.com/-6bIw2UeK9hk/VyNSHg04YqI/AAAAAAAAFgI/KLYb-OBJkWw2H4bZc7HsDxg13MzwP-ZLACCo/s640/plantsClassification_01.jpg)

#### Structure of film and production
Structure of film: **FILM >PART> SEQUENCE > SHOT**  
Structure of production process: **SEGMENT > BRANCH > PHASE > PROCEDURE > ACTION**   
Structure of employee in VFX segment: **VFX Supervisor > TD > artist**

#### VFX segment structure
* **2D (compositing)** branch  
Phases of 2D:
  * Compositing
  * Mattepainting
* **3D** branch  
Phases of 3D:
   * Pipeline development and data transfer
   * Asset creation  
Procedures of asset creation:
           * modeling
           * texturing
           * sculpting
           * setup
   * Layout and Animation
   * FX
   * Rendering and look development
* **Editing and grading** branch 


#### Folder structure
Physically VFX branch is set of files on a hard drive. To manage huge amount files of different formats in a logical and predictive way proper folder structure has to be created.
Folder structure relies on:
* Used software
* Requirements to folder structure for particular software
* Pithiness, logic and usability for data exchange.
Each file should have proper name, version and be in a proper folder. 

Animation DNA folder structure designed for a full CG projects and already has 	
directories elaborated for all imaginary data required for a production. At least at the first 3 levels of nesting you don`t need to create new folders.

Project root directory — **`<rootProject>`**:  **`<drive>:/<path>/<projectName>`**  
This is main directory of project, stored on hard drive in the studio, no project files can be stored outside this folder.
Project root directory contain: 
* **EDIT** — Editing and grading area. Contain:
  - **GRAD** — Working files and final result of grading process, contain **DCP** folder for final DCP and **FORMATS** for video files for TV, internet or other carriers.
  - **OUT** — Preview renderings from editing software sorted according to a [film structure](#structure-of-film-and-production)
  - **PRO** — Editing software project files
  - **SRC** — Source files for editing process other than 3D or 2D renders, e.g. sound for film.
* **PREP** — Pre-production area: 
  - **ART** — Artwork
  - **DOCS** — Project documentation
  - **MANAGE** — Project management team data
  - **PIPELINE** — Pipeline development and final scripts
  - **REFERENCES** — All types of reference materials, for artist, animators, lighters etc.
  - **SCRIPT** — Script of the film.
* **PROD** — Production area, root for the VFX segment:
  - **2D** — Root for compositing branch
    - **COMP** — Compositing software project files with `<codeRSS>` structure 
  - **3D** — Root for 3D branch, [Maya project root folder](#3d-folder-structure).
  - **RENDER_2D** — Renderings from compositing department:
    - **DPX** — Final renderings from compositing department with `<codeRSS>` structure 
    - **JPG** — Service files for art department with `<codeRSS>` structure 
    - **MOV** — Previer renderings for editing software with `<codeRSS>` structure 
  - **RENDER_3D** — Renderings from 3D software:
    - **BLAST** — Playblast from Maya  with `<codeRSS>` structure
    - **LOOKDEV** — Renderings of assets
    - **RENDER** — Final renderings from 3D rendering software(Arnold) with `<codeRSS>` structure 

Full folder division can be learned from [DNA.rar](#dna-archive) which contain folder structure.

### Naming
If structuring is a basement of organisation than naming is a basement of structuring. Naming is an art and it highly important aspect of production.

All files on HDD and objects in software should be named correctly according to strict rules, described for all phases and procedures in this document.  
**ONLY ENGLISH** characters and words allowed for using in ANY names.  
**NO SPACES** allowed in naming.  
Naming order: **FROM GENERAL TO SPECIFIC**.  
**Name should be short, readable and descriptive!**

Any name should start from lowercase letter. If there is more than one word in name for better readability it should be divided — each next word should start from upper case.

Division of logical parts in names of files and objects occurs with underscore sign.  
Name of files: **prefix_name_version.extension** or **name_version.extension**  
Name of objects: **name** or **name_variation** or **name_variation_property**  
Examples file names: **ANM_E010_S010_001.mb, RIG_BENDER_001.mb, trsMelony_001.mb**  
Example asset names: **trsMelony,  trsMelony_D, trsMelony_D_trunk**

### Quality control
At the end of each procedure, phase or branch, before resulting data is transferred to the next procedure, phase or branch, the control stage should go, in which the data is being checked for FLAWS and ERRORS.

## Pipeline overview
Animation pipeline is a system of organisation and execution of a project.

[DNA.rar](#dna-archive) | [Wrapper](#running-maya-and-nuke-with-wrappers) | [Pipeline brief](#pipeline-brief) | [FTrack](#management-with-ftrack) | [Outsource](#workflow-with-outsource-studios) | [Shot creation](#shot-creation-workflow) 
### DNA archive
Materially **on HDD Animation DNA** represented as a winrar archive **DNA.rar** which includes:
- [Maya and Nuke python tools](03-tools)
- [Folder structure](#folder-structure)
- [Project database](https://github.com/kiryha/AnimationDNA/blob/master/DNA/DIC/dataProject.json) in JSON format (for non FTrack version)
- Demo data (Maya scenes with models, rigs, animation, materials and render, textures, Nuke scripts and other data necessary for production of example shot)

Animation DNA documentation located online:
- [Quick start tutorial](01-quick-start) 
- [Pipeline rules](02-codex-dna)
- [Tools description](03-tools)
- [Glossary](#04-glossary)

[Download DNA.rar](https://drive.google.com/file/d/0B08-uC9HedKCTjI5SFBDanBHQXc/view?usp=sharing). This version contain only folder structure and [tools](03-Tools), no demo materials included. If you need them — drop me a message.

### Running Maya and Nuke with wrappers
Go to **`<rootProject>/PREP/PIPELINE/`** and run:
* **runMaya.bat** to load Maya, 
* **runNuke.bat** to load Nuke.  

Optional you can create shortcuts on runMaya.bat or runNuke.bat on desktop for each project, rename them to a project name and build a representative icons or use [DNA icons](https://github.com/kiryha/AnimationDNA/tree/master/DNA/3D/icons) in `.ico` format.

![](https://lh3.googleusercontent.com/-79aa8Jer7xI/V0Qho_VLZVI/AAAAAAAAFoM/9hZH36ZvEzoyTRGSzJc-ViZ5ZKJmclgxwCCo/s436/DNA_icons_01.jpg)

**runMaya.bat** executes runMaya.py – python script which run Maya with settings you need to setup for particular project (environment variables, project settings etc.) and it called **wrapper**.  
Once Maya opened you should get following messages in the script editor without any error:  
`<<  userSetup.mel: RUNNING setupMaya.py  >>`  
`<<  setupProject [ rootProject ]: P:/DNA/ >>`  
`<<  setupMaya [ projectName ]: DNA  >>`

**runNuke.bat** executes runNuke.py to load Nuke with DNA menu and necessary settings.

If Maya or Nuke does not run — check paths to Maya and Nuke installation folders in runMaya.bat, runMaya.py, runNuke.bat, runNuke.py

### Pipeline brief
The final output of VFX department is set of shots for editing and grading.  
In a very general overview, VFX department pass from [**story reel**](04-glossary) through **asset creation** to **shot production**.  
**Asset creation** stage consists from: modeling, texturing, sculpting, look development and rigging.  
**Shot production** stages: animation, lighting- rendering setup, renders 3D process; compose and render 2D process (final VFX images).

Schemes below illustrate shot production in general and VFX pipeline more in details.
![](https://lh3.googleusercontent.com/-btZQhX5xAD8/VyNTQ-GbN8I/AAAAAAAAFgc/ps9U9BQyCy8XgONyev1ZzIJMJ97eX3DbwCCo/s1024/ProductionPipeline_03.jpg)

#### Asset forms
Each animated asset exists in **two forms** — RIG and GEO — polygonal geometry with setup and polygonal geometry only. We use RIG assets in animation scenes and GEO assets in rendering scenes.  
Each polygonal object shape contains all **shading data** in Arnold custom attributes (textures and materials).  
Finalized animated asset (or environment)  should be published to FTrack with [Data Publisher](03-tools#data-publisher).

Each static asset also exists in two forms — **GEOMETRY** and **STANDIN**. We model static assets as regular Maya polygon geometry and at the last stage of asset creation convert them to Arnold Standins.

#### Production with Animation DNA
For each shot layout artist creates **animation scene** with [Shot Assembler](03-tools#shot-assembler).  
On the animation stage artists bring characters and props to life, setup and animate camera.

After animation has been finished and approved, animation scene goes to a pipeline department, where pipeline artist should check scene: if there are all assets in scene; if there are no redundant assets in scene; if assets has proper versions. Then FX artist creates cloth and fur simulation scenes with [FX Manager](03-tools#fx-manager) and export animation data to alembic with [Animation Exporter](03-tools#animation-exporter).

Once pipeline and FX department had export all caches, rendering artist can take shot in production.  
During the lighting- rendering stage artist creates **rendering scene** with [Shot Assembler](03-tools#shot-assembler), import animation and FX to the scene with [Data Importer](03-tools#data-importer) and [Render Manager](03-tools#render-manager), creates lights, make individual tweaks in each shot and send scenes to 3D rendering process.

Rendered shots goes to compositing department as exr sequences, where artist assemble Nuke script with [Shot Assembler](03-tools#shot-assembler-nk), achieve final look by gathering 3D renders and artworks, adding different elements and FX, tweak colors and materials.

After finishing compositing stage shots are passes rendering 2D process and delivers to editing.  

### Management with FTrack
#### Management with FTrack general notes
FTrack is primary studio information database. Every action in production starts and recorded in FTrack. Through FTrack all studio departments and employee communicate one to each other by reading and writing particular data (either manually or automatically when using [Animation DNA tools](03-tools)).  

At the base level of project organization we have to deal with two substances: 
* **ASSETS**
* **SHOTS**

This core division permeates through a project workflow and reflected in FTrack database and folder structure. Shots organization based on [film structure](#structure-of-film-and-production). Asset organization in FTrack based on [assets classification](#assets-classification).

**SHOTS**. Whole film divided into smallest logical pieces — shots (a part of a film between two cuts). Shots grouped into the sequences — logical part of film actions, usually sequence starts and finishes in one environment, so sequence linked to one particular environment. Sequences grouped into the parts (which are called REELS for feature films) — around 25 min part of the movie. In smallest project there could be only one part and it may have any readable descriptive short name (e.g. TRAILER)

Reels and sequences are numbered sequentially, e.g. there is no reels or episodes in the film with the same number. In each sequence shot number starts from the beginning. 

Representation of film structure on HDD and in FTrack:  
**`<codePart>/<codeSequence>/SHOT_<codeShot>`** ( REEL_01/010/SHOT_010 )  
This peace of folder structure exists in FTrack database and repeated many times in different project folders, which deals with **SHOTS**, for example in **`scenes/ANIMATION/`**, **`PREP/ART/SHOTS/`** etc.

**ASSETS**. All assets divided into 2 main parts: what is animated, and what is not. Animated assets its characters, dynamic props and EDA, not animated assets is static props end environments. Read [assets classification](#assets-classification) for more details.

#### Asset types in FTrack
Respectively you need to create such **asset types** (FTrack system settings > schemas > Asset build > Types  ):
- eda
- props
- environment
- static
- characters

Exactly as written, because this types are used by python tools so no mistakes allowed. Case sensitive also.

Representation of [assets classification](#assets-classification) on HDD and in FTrack:
**ASSETS**:
* **CHARACTERS** (contain folders named as characters. On HDD there RIG and GEO folder inside each character folder)
* **ENVIRONMENTS** ( contain folders with locations, in each folder with location there is folder with EDA )
* **PROPS** (dynamic props, [structured](02-codex-dna#structuring) into a collection)
* **STATIC** (static props, [structured](02-codex-dna#structuring) into a collection)

#### Creating FTrack database
First we analyze story reel. During this process we create two lists: list of all objects(assets) and list of all shots in film. Than this lists should be entered to FTrack. 

Finally we **link** animated assets end environments to a shots. DO NOT link EDA and static props to a shots.

Refer to [database setup tutorial](01-Quick-start#preproduction) for more information.

#### Publishing data to FTrack
One way of entering information to FTrack is publishing.  
Publishing is a process of recording necessary data to FTrack database with a help of [Animation DNA tools](03-Tools) using [FTrack Python API](http://ftrack.rtd.ftrack.com/en/3.3.1/developing/index.html):
- [Data Publisher](03-Tools#data-publisher) allow to write:
  * working name and version of GEO and RIG [asset forms](#asset-forms),
  * name and version of character fur file
  * name and version of asset material library
  * list of [EDA](#asset-creation-general-notes), linked to environment
- [Animation Manager](03-Tools#animation-manager) writes name and version of approved animation file for each shot
- [FX Manager](03-Tools#fx-manager) writes name and version of final FX scene
- [Render Manager](03-Tools#render-manager) writes name and version of exr render for each shot

### Workflow with outsource studios
Major part of the project will be done locally in the studio. All project data (3D scenes, comp files, script, artwork, sound, editing etc etc) stores at the studio server at network drive. To outsource any part of work (for example, animation of some sequences) we create FTP server with project copy on it with the **same folder structure**. Outsource company should replicate **studio folder structure on their own network drive** and copy all necessary data. Such setup will ensure, that everything will work properly.

Particular information about each project stores in **codex Outsource**. It include: mirror FTP login and password; project drive letter, name, path; instructions for cooperation.

To upload animation scenes and linked references on mirror FTP use [FX Manager](03-tools#fx-manager). Enter shot number and press **UPLOAD SCENE**. Note that script does not copy environment, user have to upload it manually

### Shot creation workflow
To start work on shot it should be created in FTrack, all necessary assets should be published and linked to each shot.
Then in CG area for each shot should be created animation scene. Animation scene goes to layout artist and then to animator.
Finished animation goes to FX and rendering. Rendered shots should be finalized at compositing stage.

For each shot:  
Project management department:
- creates shot in FTrack
- link assets
- setup shot length

Layout department:
- creates animation scene with [Shot Assembler](03-tools#shot-assembler)
- produce layout, makes playblasts with [Animation Manager](03-tools#animation-manager) and approves them. 
- after layout has been approved, artist publish animation to FTrack with [Data Publisher](03-tools#data-publisher)(**PUBLISH CURRENT ANIMATION**). Scene goes to pipeline department.

Animation department:
- produce animation and approves playblasts.
- after animation has been approved, artist publish animation. Scene goes to pipeline department.

Pipeline department:
- open approved animation shot, save it to a next version (**SNV**).
- check and clean scene, update asset versions.
- publish animation file to FTrack
- export animation cashes

FX department:
- creates CLOTH simulation, export cloth cashes.
- create FUR simulation, export fur cashes.

Lighting and rendering department:
- create render scene with [Shot Assembler](03-tools#shot-assembler)
- import animation cashes with [Animation Importer](03-tools#animation-importer) and fur with [Render Manager](03-tools#render-manager)
- setup and render shot with PREVIEW quality
- publish render to FTrack
- improve shot according to painted reference from art department and compositing report
- render FINAL quality of the shot
- publish render to FTrack

Compositing department:
- create Nuke script with [Shot Assembler](03-tools#shot-assembler-nk)
- compose preview quality render and publish render
- render JPG to review in art department
- create report on 3D render errors and issues and submit this report to LR department

Art department:
- paint over preview render
- review goes to compositing and lighting rendering departments.

Lighting-rendering department:
- tweak shot according to review
- render shot in PREVIEW quality

Compositing department:
- tweak shot according to review
- approve shot in Art department

Lighting-rendering department:
- render shot in FINAL quality

Compositing department:
- render final shot
- publish render

## 3D branch
3D branch include Maya and other 3D applications.

[3D overview](#3d-branch-general-notes)  | [3D pipeline](#pipeline-development-and-data-transfer) | [Asset creation](#asset-creation) | [Layout and animation](#layout-and-animation) | [Lookdev](#look-development-and-rendering) | [FX](#fx)

### 3D branch general notes
3D branch phases are: 
* [pipeline development and data transfer](#pipeline-development-and-data-transfer)
* [asset creation](#asset-creation)
* [layout and animation](#layout-and-animation)
* [look development and rendering](#look-development-and-rendering)


### Pipeline development and data transfer
Once pipeline for the project has been developed, the main role of pipeline department is:
* transfer data between departments 
* maintain pipeline function 
* create new tools for production by request of TDs

Main tools of pipeline department are: [Shot Assembler](03-tools#shot-assembler), [Data Publisher](03-tools#data-publisher), [Animation Exporter](03-tools#animation-exporter)

#### 3D folder structure
Root folder for 3D branch is `<rootProject>/PROD/3D`. This root folder of Maya predefined project system contain:
* data 
* cache
* scenes
* sourceimages 

### Asset creation
#### Asset creation general notes
**Asset** – a set of digital data (files of different formats), required for the creation, management and visualization of real-world objects in the environment of a computer program Maya. Any visible object in the scene while rendering 3D scenes is asset. 

Ordinarily, the asset consists of the following elements: a polygonal model, setup (if asset must be animated), materials and textures. There are different procedures for creating the assets: 
* [modeling and sculpting](#asset-modelling)
* [texturing](#asset-texturing) 
* [rigging](#asset-rigging)
* [look development](#asset-look-development)

#### Assets classification
In order to optimize the process of creating and managing a quantity of objects, the objects must be classified, which means that the objects must be separated into groups according to the procedures used for assets creation and to the type of usage the assets in the virtual environment.

As a result, it is possible to create a set of unambiguous instructions for each group (category). The strict compliance with these instructions will let the significant part of the process be automated. 

Assets are divided into 5 categories: 
* [Static assets](#static-assets)
* [Dynamic assets](#dynamic-assets)
* [Character assets](#character-assets)
* [Environment assets](#environment-assets)
* [Environment dynamic assets](#environment-dynamic-assets)

**Static Asset** – is a non-deformable fixed object.  
Static asset consists of a polygonal model, an object’s proxy, materials and textures. This is the simplest, basic asset type, which involves the minimal quantity of operations to create it. Each static asset is designed for multiple copying in one or more scenes of the environment.

Almost all static assets have **variations** – the objects similar in the functionality but different in the details. 

Example of the static asset is an apple. The examples of the variations of apple tree: young, mature, old and dry.

**Dynamic Asset** – is the object designed for animation.  
In addition to the polygonal model, textures and materials the objects that must be animated require the control system to create animation – **asset setup**. Dynamic assets are usually unique or may be copied a very few times.

**Character asset** — is animated model of the hero of the film, which is able to perform the set of actions defined in scenario.  
Character asset is particular case of dynamic asset. It is separated into a special category because of high complicity of modeling, setup and rendering.

**Environment asset** — is complex asset which consists of the variety of simple objects and static assets.
Environmental asset represents separated part of the world (peace of landscape) where is happening the certain episode of the film. 

**Environment dynamic asset** — dynamic assets, linked to environments (exist in each shot with particular env, like door or window). Publish list of EDA with EDA button of Data Publisher script to link asset to environment  in FTrack.

**Asset creation quality control**  
Asset quality control is a process of checking if asset meat pipeline requirements. Checking quality of asset mean finding technical errors in asset scene which may cause errors in rendered shots or in pipeline.

There is **CHECK SCENE** procedure in [Asset Manger](03-tools#asset-manager) which allow to reveal some errors in asset setup.

#### Asset modelling 
Static assets models should match such conditions:
- Combine objects by materials (all objects with the same material has to be combined to one piece)
- One asset – one texture (may be different if one texture used by several assets)
- Freeze transformations and deleted history.
- Non overlapped and non flipped Uvs 
- Proper naming and hierarchy.
- Shading info and subdivision in attributes.
- Cleaned scene. No extra nodes but geometry should be in scene, especially shading nodes.

See how to [prepare assets for rendering](#prepare-assets-for-rendering) for more info.

##### Static assets
###### Name and location of static asset
Name and category of each asset defined in FTrack and it should be exactly the same in Maya scenes.  
Place static asset files in:  
**`<rootScenes>/ASSETS/STATIC/<assetNestedCategorys>/`**  
Name assets  files:  **`<assetName>_<###>.mb`**  
Place textures for static asset files in:  
**`sourceimages/ASSETS/STATIC/<assetNestedCategorys>/`**
Name assets  file textures:  
**`<assetName>_<partName>_<property>_<##>.tx`**  
Source files for textures in TX format are: **`*.jpg`** for all properties and **`*.exr`** for displacement.

###### Static asset structure
Each asset file contains models of all **asset variations** inside (A-Z).  
Each asset consist from **2 parts** gathered in particular hierarchy — render geometry (group of objects for render) and proxy object (polygonal shape to represent render geometry with a very few polygons). Artist switches between render or proxy mode with **PROXY** button of [Asset Manger](03-tools#asset-manager).

**Names of objects** in static asset file:
The root of scene contains polygonal proxy object  of each asset version.  
Name of proxy **transform**: **`<assetName>_<letterNumber>_<###>`**   
Name of **shape**: **`<assetName>_<letterNumber>_Prx`**  
The polygonal proxy object contains group with render geometry.  
Name of **render geometry** group: **`<assetName>_<letterNumber>_Geo`**  
The render geometry group contains  all parts of asset. Name of parts:  
**`<assetName>_<letterNumber>_<partName>`**  
Artist create asset and proxy model, gives them correct names, create asset hierarchy with **SETUP STATIC** button of [Asset Manger](03-tools#asset-manager).

There could be complex assets, like trees with heavy crown, which may require **manually setup of hierarchy**. Crown builds from instanced brunches assets, then all leaves exports as one ASS file, brunches as another and imports into the scene as a standin to solve combining objects by materials with instanced standins. See [setup of complex assets](01-quick-start#complex-static-asset-setup)

After finishing asset modeling, each asset variation has to be converted to Arnold standin asset with **CONVERT TO STANDIN** button of [Asset Manger](03-tools#asset-manager) and this would be **FINILIZED ASSET** for using in ENVIRONMENT scenes. Standin version of asset model has the same structure but group with render geometry replaced with group with Arnold standins and named:  
**`<assetName>_<letterNumber>_Ass`**  

Location and name of **Arnold ass geometry**:  
**`<rootScenes>/ASSETS/STATIC/<assetNestedCategorys>/ASS/`**  
**`<assetName>_<letterNumber>_<partName>_001N.ass`**  
Location and name of [standin forms](#asset-forms) of static assets:  
**`<rootScenes>/ASSETS/STATIC/<assetNestedCategorys>/SI/`**  
**`<assetName>_<letterNumber>_SI_<###>.mb`**

###### Converting GEOMETRY form to STANDIN form  
**CONVERT TO STANDIN** button export each asset part of geometry to ass file, import into the scene as standin, rename standin and copy attributes from geometry, place standins in render group and rename it to:  
**`<assetName>_<letterNumber>_Ass,`**  
export all asset into:  
**`SI/<assetName>_<letterNumber>_SI_<###>.mb`**

**DO NOT SAVE SCENE AFTER CONVERT TO STANDIN BUTTON!!!.**

###### Organizing assets to a SETS
From the number of standin assets in each category we create a **sub set** of static assets:  
**`<rootScenes>/ASSETS/STATIC/<assetCategory>/SET_<assetCategory>_001.mb`**

All finished standin forms of static assets could be gathered in one **set** of static assets in:
**`<rootScenes>/ASSETS/STATIC/SET_STATIC_<###>.mb`**  

Default asset condition in SET: hidden render geometry and visible proxy object.

During creation of environment assets this sets are used as source of objects for filling environments. Hierarchy in SET files should match hierarchy in Ftrack database.

###### Example of sunflower asset workflow
Asset Maya file located: **`<rootScenes>/ASSETS/STATIC/FLORA/ASSETS/sunflower_001.mb`**  
Texture files: **`sourceimages/ASSETS/STATIC/FLORA/`**  
Textures for render: **sunflower_A_seeds_CLR_01.tx, sunflower_A_stern_CLR_01.tx, sunflower_A_seeds_DSP_01.tx, sunflower_A_stern_DSP_01.tx**  
Source textures(output from texture artists): **sunflower_A_seeds_CLR_01.jpg, sunflower_A_stern_CLR_01.jpg, sunflower_A_seeds_DSP_01.exr, sunflower_A_stern_DSP_01.exr**

sunflower setup:
- Variation of sunflowers in Maya scene,
- Geometry form structure of static asset,
- Standin form structure of static asset

![](https://lh3.googleusercontent.com/-a9Sm34iqsE4/Vyn4lC3p3TI/AAAAAAAAFiY/RPwOBo1ODvIDLXQ-kOeTK2IVdnYgfAK6gCCo/s859/assetStatic_setup_01.jpg)

##### Dynamic assets
###### Name and location of dynamic asset
Name and category of each asset defined in FTrack and it should be exactly the same in Maya scenes.
Place dynamic asset files in:  
**`<rootScenes>/ASSETS/PROPS/<assetCategory>/<assetForm>/`**  
Name dynamic asset files:  
**`<assetForm>_<assetName>_###.mb`**
Place textures for dynamic asset files in:  
**`sourceimages/ASSETS/PROPS/<assetCategory>/`**  
Name assets file textures:  
**`<assetName>_<partName>_<property>_<##>.tx`**

###### Dynamic asset structure
Each dynamic asset exists in two [forms](#asset-forms) — RIG and GEO. Maya scene with rigged asset form contain root group named exactly as in FTrack database (**`<assetName>`**).

Inside root group there two groups:
* **`<assetName>_GEO`**
* **`<assetName>_RIG`**

Group **`<assetName>_GEO`** contain all render geometry, group **`<assetName>_RIG`** contain all setup nodes.

Name of objects in render geometry group:  
**`<assetName>_<partName> `**

Display layers:
* GEOMT — layer with render geometry
* CTRLS — layer with controls

![](https://lh3.googleusercontent.com/-NWzPYnqUUFQ/VysdMeVnXiI/AAAAAAAAFi0/ahrvIdHRMcQ8F0cAoHnK9OviIx5IeII0wCCo/s823/assetDynamic_setup_01.jpg)

Modelling artist:
* creates render geometry with necessary shading attributes, 
* give names to all parts of render geometry,
* creates asset hierarchy with **SETUP DYNAMIC** button of [Asset Manger](03-tools#asset-manager),
* publish GEO form of asset with [Data Publisher](03-tools#data-publisher).
* deliver file to rigging department (by changing statuses of asset in FTRack)

Rigging artist:
* create asset rig and place all nodes under **`<assetName>_RIG`**
* publish RIG form of asset with [Data Publisher](03-tools#data-publisher).
* mark asset as ready for animation in FTrack

##### Character assets
###### Name and location of character asset
Place character asset files in:  
**`<rootScenes>/ASSETS/CHARACTERS/<characterName>/<assetForm>/`**  
Name character asset files:  
**`<assetForm>_<characterName>_###.mb`**  
Place textures for characters in:
**`sourceimages/ASSETS/CHARACTERS/<characterName>/`**  
Name character file textures:  
**`<characterName>_<partName>_<property>_<##>.tx`**

Place FUR of character asset files in:  
**`<rootScenes>/ASSETS/CHARACTERS/<characterName>/FUR/FUR_< characterName >_###.mb`**  

###### Character asset structure
Root group: **`<characterName>`**  
Inside root group there two groups:
* **`<characterName>_GEO`**
* **`<characterName>_RIG`**

Group **`<assetName>_GEO`** contain all render geometry, group **`<assetName>_RIG`** contain all setup nodes.

Name of character body object for FUR GROW:  
**`<characterName>_body`**

Display layers:
* CHARC — layer with render geometry
* CTRLS — layer with controls

###### Setup FUR.
Name of  yeti node: **`FUR_<characterName>`**  
Geometry with fur node: **`FUR_<characterName>_body`**  
Groom nodes: **`GRM_<partName>`**

![](https://lh3.googleusercontent.com/-m7K1mKgq8QQ/Vys48YiTS-I/AAAAAAAAFjE/ESI5AN_xB9QkT0bSiKzlEga7N2pMJgzFQCCo/s1045/assetCharacter_setup_01.jpg)

##### Environment assets
###### Name and location of environment asset
Place working environment asset files in:  
**`<rootScenes>/ASSETS/ENVIRONMENTS/<environmentName>/EDIT/`**  
Name working environment asset files:  
**`EDT_<environmentName>_###.mb`**  
Place finalized environment asset files in:  
**`<rootScenes>/ASSETS/ENVIRONMENTS/<environmentName>/`**  
Name finalized environment asset files:  
**`ENV_<environmentName>_###.mb`**  
Arnold ass files for environments:  
**`<rootScenes>/ASSETS/ENVIRONMENTS/<environmentName>/EDIT/ASS/`**  
Sub-assets files for environments:  
**`<rootScenes>/ASSETS/ENVIRONMENTS/<environmentName>/EDIT/ASSETS`**
Mary, Z-brush and OBJ files for environments:
**`<rootScenes>/ASSETS/ENVIRONMENTS/<environmentName>/EDIT/(M, Z, OBJ)`**  
Place textures for environments in:  
**`sourceimages/ASSETS/ENVIRONMENTS/<environmentName>/`**  
Name environment asset file textures:  
**`<environmentName>_<partName>_<property>_<##>.tx`**  
Source files for textures in TX format are: **`*.jpg`** for all properties and **`*.exr`** for displacement. 

###### Environment asset structure
The root of environment scene contains group **`<locationName>_GMT`** with all environments objects inside. Small assets, which are part of environment assets, but NOT static or dynamic assets can be modeled in separate scenes and then imported into environment scene. In this case place parts of environment assets in [sub-asset folder](#name-and-location-of-environment-asset)  

Display layers:
* GEOMT — layer with render geometry
* HIRES — layer with heavy for viewport display render geometry

###### XGen for environment asset plants population
Large area of environments covered with assets procedural with XGen module.  
XGen files for environments are developed in look development scenes of environments:  
**`<rootScenes>/LOOKDEV/ASSETS/ENVIRONMENTS/<environmentName>/`**  
Name of Maya scene with XGen:  
**`LDV_<locationName>_###.mb`**  
Name XGen collection: **`SCT_<environmentName>`**
Name XGen description: **`SCT_<environmentName>_<assetName>`**
Name XGen geometry: **`SCT_GEO_<property>`**

After finalizing Xgen developing artist export all XGen data with **EXPORT XGEN** button of [Render Manager](03-tools#render-manager). In every render shot scene render artist imports XGen data with **IMPORT XGEN** button. 

##### Environment dynamic assets
EDA usually modeled in environment scenes and than necessary geometry exported as separate asset into corresponding location. After exporting EDA geometry it should be deleted from environment scene.

###### Name and location of environment dynamic asset
Place EDA files in:  
**`<rootScenes>/ASSETS/ENVIRONMENTS/<environmentName>/EDA/<assetForm>/`**  
Name EDA files:  
**`<assetForm>_<assetName>_###.mb`**

#### Asset modelling quality control
Finalized model should fit such requirements:
* Freeze transformations and deleted history.
* Non overlapped and non-flipped UVs 
* Proper naming and hierarchy.
* Shading info and subdivision in attributes.
* Cleaned scene. No extra nodes but geometry (and rigging nodes for RIG forms) should exist in scene, especially shading nodes.

Use **CHECK SCENE** button of [Asset Manger](03-tools#asset-manager) to check scene for the quality requirements consistency.

#### Asset texturing 
Each color texture should be presented in **`*.jpg`** and **`*.tx`** formats.

**UDIM** workflow.
Texture: **`<textureName.1001.jpg>`**  
In **mColor**: **`<textureName>`**  
In shader token: **`<attr:mColor>.<udim>.jpg`**

#### Asset rigging
**Rigging** (or setup) — is a process of creating a system which allow to animate assets and characters.
The main requirement to the rigging task: correct behavior with ABC caches (parent constrains not supported).

#### Asset look development  
Refer to [look development and rendering](#lLook-development-and-rendering) phase description. 

### Layout and animation
#### Layout and animation general notes 
**Layout** — is synergistic cycle between modeling and animation. It is the first step of animation process, where we define and test environment space, cameras, characters basic actions for each shot.

To start layout it`s necessary to have rough models of environments (basic objects in their positions: land, buildings and other objects, which interact with characters) and rigged characters.

As **result** of layout stage we get rough model of environment **tested in particular shots**, positions and basic characters motion, cameras. Also we got first 3D renders (playblasts) at this phase.

Creation of layout and animation file:  
Layout artist creates animation scenes for each shot with [Shot Assembler](03-tools#shot-assembler).  
Each animation file consists from referenced environment, characters and props, camera.  
Layout artist set camera lenses with [Animation Manager](03-tools#animation-manager), place characters assets and cameras in necessary positions, add very rough motion with stepped keys.

After finishing and approving layout, layout scene should be delivered to animators.  
Animation and layout scenes has the same name and location, animation scene is next version of layout scene.

**Animation** — is a process of adding motion to characters and props by setting keys on control elements.  
Animation produces on shot basis, for each shot there is animation file on hard drive. Each animator handle whole shot with all characters and props inside. Each animation file can be handled only by one animator at the same time.

#### Location and name of animation files: 
Animation files located in:  
**`<rootScenes>/ANIMATION/<codePart>/<codeSequence>/SHOT_<codeShot>/`**  
Name of animation files:  
**`ANM_E<codeSequence>_S<codeShot>_<###>.mb`**  
References for animation department:  
**`<rootProject>/PREP/REFERENCES/ANIMATION`**  
Sound location:  
**`<rootProject>/PROD/3D/sound/<codePart>/<codeSequence>/SHOT_<codeShot>/`**  
Sound name:  
**`E<codeSequence>_S<codeShot>_<###>.wav`**  
Playblasts location:  
**`<rootProject>/PROD/RENDER_3D/BLAST/<codePart>/<sequenceCode>/SHOT_<codeShot>/`**  
Playblast name:  
**`E<codeSequence>_S<codeShot>_<###>_<###>.mov`**
#### Animation process:
- animation starts at frame 101
- camera should has lens defined with [Animation Manager](03-tools#animation-manager) (12-180 buttons)	
- animators receive scene after layout approve, setup camera and lens, set keys, makes playblasts with [Animation Manager](03-tools#animation-manager).
- during the work animators may save other version of file with **SNV** button in [DNA shelf](03-tools#toolset-for-3D-branch) or in Animation Manager. **No file name changes allowed!**
- animation can be done **ONLY ON CONTROL ELEMENTS** in scene, no geometry should be animated or moved.
- animators should not add objects, characters or props by themselves manually. Use only **CHECK SCENE**, **ADD CHAR**, **ADD ASSETS**, **ADD ENV** and **FIX ALL** procedures of Animation Manager to check and fix animation scene.
- animators could create constrains for space switching, also using only control control objects. 
- if render camera required special rig, than Pipeline TD creates rig for the camera and add it to animation scene.
- no hierarchy changes allowed, parenting can be done only with constrains.
- add [service keys](#service-keys) for each character.  
- create playblasts only with **PLAYBLAST** button of Animation Manager

After animation has been approved:
- [check quality](#animation-quality-control) of animation file
- publish animation file with **PUBLISH** button of Animation Manager
- select frame which describe shot, press **JPG** button of Animation Manager

#### Service keys
For the dynamic cloth and fur simulation two additional keyframes for each character are required:  
* in **90 frame** set character in **T-pose**, 
* in 1 frame move it to default position (Main control translate and rotate set to 0) 



#### Animation quality control
Before exporting animation data scene should be checked:
- for consistency of asset and scene with FTrack  
(**CHECK SCENE** button of [Animation Manager](03-tools#animation-manager))
- intersections of assets and asset parts

### Look development and rendering
#### Look development and rendering general notes
**Rendering**, by general definition, is a conversion of vector data to a raster images.  
In terms of pipeline organization, rendering shots its last phase 3D branch, where data from all 3D departments assembles in one scene for each shot and outputted as a sequence of EXR files to be transferred to the compositing department.

**Look development** — is a process which define physical behavior of surfaces and volumetric in conjunction with lighting. The result of look development process is materials and lights.

For each **character** and **environment** asset should be created material library which include materials for all objects in the asset scene. To create library for each environment we use base material library (which include number of common materials like wood, metal, grass etc and called SET GENERAL) as a starting point and during look development of environment tweak materials to achieve necessary appearance.

**SET GENERAL** located in **`<rootScenes>/LOOKDEV/LIBRARY/MATERIALS/SETS/SET_GENERAL_###.mb`**  
Final set of materials for each environment exported as environment material library to:  **`<rootScenes>/LIBRARY/MATERIALS/ASSETS/ENVIRONMENTS/<envName>/`**

All materials for SET GENERAL are created in certain lighting conditions, in common for all assets scene with a lighting template — **LIGHTROOM** located in:  
**`<rootScenes>/LOOKDEV/LIBRARY/LIGHTS/`**  
This ensure that all materials will work fine together after assembling a render scene.

Look development scene is a fabric for materials production. These scenes located in:  
**`<rootScenes>/LOOKDEV/ASSETS`**  
When you [setup Melony tree](#static-assets) you enter **GEN_BARK_A** and **GEN_PLANT_A** material names in **mMat** attributes. This mean, that there should be such materials in a library. 

#### Rendering pipeline
For each shot of the film should be creating individual render scene with CREATE RENDER SCENE button of [Shot Assembler](03-tools#shot-assembler).

Shot Assembler:
* creates Maya scene located in:  
**`<rootScenes>/RENDER/REEL_01/010/SHOT_010/RND_E010_S010_001.mb`**
* reference [GEO forms](02-codex-dna#asset-forms) of all assets , linked to a shot in project database
* import published materials for each character and environment 
* setup scene playback range

Render scene contains all data from 3D branch which should be rendered in 3D: 
- assets
- props and environments 
- animation 
- camera 
- fur 
- FX 
- materials and lights 
- AOVs 

Each finalized scene should be export to **ASS sequence** with **RENDER SHOT** button of [Render Manager](03-tools#render-manager) to be rendered on render farm. 

Output data of 3D rendering process — sequences of exr files which contain beauty image of shot spitted into passes (direct diffuse, indirect diffuse, direct specular etc) and extra data for compose, such as AO, IDs, normal, depth etc. 

Rendering pipeline scheme.
![](https://lh3.googleusercontent.com/-FYS6r3dyExY/VyNSSf2jFQI/AAAAAAAAFgM/k-xzdumIkWMU85VIW2JntRxihLxWrYvFwCCo/s1192/DNA_RenderingPipeline_02.jpg)

#### Prepare assets for rendering.
Rendering starts from modeling.  
Obvious setup assume custom material for each asset in scene. Sometimes different objects can share same shader but never the less, the more object exists in scene, the more shaders should be used which increase difficulty of scene setup and tweaking. Main idea of optimization Lighting rendering process is reducing general amount of shaders in project to a very low number.

One way to perform this is to organizine materials by physical types (metals, woods, glass, stones etc) so amount of shaders become limited and not connected to amount of objects. Varying of individual characteristics for each asset can be achieved through custom MtoA attributes with individual parameters (such as material or texture name) on each asset. 

Having one common material library we can use it in any rendering scene.  
Character assets is an exception  — **each character has its own material library**.

To provide this workflow all assets should be prepared in certain way to fit rendering pipeline requirements.  
In general this mean:
- each asset should contain basic shading information (names with paths and required material) stored in custom MtoA attributes on the objects shapes.
- Maya scenes with assets are clean from all nodes but geometry.  
- all assets uses the same material library. But each character has its own material library.
- all materials should be assigned to assets in render scene.

There are 3 main tools for lighting-rendering phase:
* [Shot Assembler](03-tools#shot-assembler)
* [Animation Importer](03-tools#animation-importer) 
* [Render Manager](03-tools#render-manager) 

#### location and names of look development and rendering files
Rendering output for main BEAUTY image:  
**`<rootProject>/PROD/RENDER_3D/RENDER/<codeRSS>/MASTER/v###/`**  
Name for main BEAUTY image:  
**`E<codeSequence>_S<codeShot>_v###.####.exr`**  
FX rendering output:  
**`<rootProject>/PROD/RENDER_3D/RENDER/<codeRSS>/<codeFX>/v###/`**  
Name for FX rendering output:  
**`<codeFX>_E<codeSequence>_S<codeShot>_v###.####.exr`**  
Location of rendering output for other layers of shot:  
**`<rootProject>/PROD/RENDER_3D/RENDER/<codeRSS>/<coleLayer>/v###/`**  
Name of rendering output for other layers of shot:  
**`E<codeSequence>_S<codeShot>_v###.####.exr`**

#### Look development and rendering process
##### Look development of assets
Overall workflow for look development phase:  
In **`<rootScenes>/LOOKDEV/ASSETS/`** with a lighting templates from  
**`<rootScenes>/LOOKDEV/LIBRARY/LIGHTS`**  
you create material library for assets and environments for the whole project and save it to  
**`<rootScenes>/LOOKDEV/LIBRARY/MATERIALS/SETS/SET_ GENERALL_###.mb`**.  

Depending on project there could be several set types (for example set for materials with UDIM textures etc). Each character has individual material library developed in  
**`<rootScenes>/LOOKDEV/ASSETS/CHARACTERS`**  
and finally resaved in  
**`<rootScenes>/LOOKDEV/LIBRARY/MATERIALS/ASSETS/CHARACTERS`**

##### Lighting and rendering of shots
Lighting and rendering artist:
* create shot scene
* create lights
* submit and publish preview render
* execute 
* submit and publish final render

#### Look development and rendering quality control
Render frame with low quality settings half size, submit to comp department.


### FX
#### FX general notes
**FX** — is special type of assets, which could not be created with regular polygonal modeling techniques, or special type of animation, which could not be created with rigged asset. 

Fluids, hairs, rigid body simulation are common examples of FX. There are two types of FX existing in each shot — CLOTH and FUR, so they has their own categories, tools and procedures, separated from the others FX.

Formulating FX brief and FTrack setup.
FX TD with VFX supervisor analyze story reel and create list of FX for each shot. There could be several different FX for each shot. Each FX task receives unique for particular shot name (**`<codeFX>`**). For each FX in particular shot in FTrack project manager using list of FX creates a task (task type = FX) with a name equal to FX code (Note that all names are case sensitive!) In each task should be brief of FX from a director and art of FX.

[FX Manager](03-tools#fx-manager) is a main tool of FX phase.
To create scenes for fur simulation: enter reel, sequence and shot number, press **CREATE FUR SCENE**. For each character in noticed shot Maya scene with all data and connections will be created.

Procedure: name and save fur scene for each character for particular shot, Import fur file and ABC cache, connect ABC animation to fur geometry, setup output cache file name. 

To export cache: open scene for each character, setup dynamic behavior, press WRITE CACHE FOR CURRENT SCENE. You don’t need to set Reel, sequence and shot values to export caches.

ART for FX:  
**`<rootProject>/PREP/ART/SHOTS/<codeRSS>/<codeFX>/ART_<codeFX>_##.jpg`**

#### Cloth workflow
Location of cloth scenes:  
**`<rootProject>/PROD/3D/scenes/FX/CLOTH/<codeRSS>/`**  
Name of cloth scenes:  
**`CLT_ E<codeSequence>_S<codeShot>_###.mb`**
Location of cloth caches:  
**`<rootProject>/PROD/3D/cache/alembic/<codeRSS>/CLT/`**  
Name of cloth caches:  
**`CHR_<codeChar>_###.abc`**

#### Fur workflow
Making with Yeti. 
Location of scenes with fur models:  
**`<rootScenes>/ASSETS/CHARACTERS/<nameChar>/FUR/`**  
Name of scenes with fur models:  
**`FUR_<nameChar>_###.mb`**  

Location of scenes for fur simulation for shots:  
**`<rootScenes>/FX/FUR/<codeRSS>/`**  
Name of scenes with fur simulations:  
**`<codeChar>_ E<codeSequence>_S<codeShot>_###.mb `**

Location of fur simulation caches:  
**`<rootProject>/PROD/3D/cache/FUR/<codeRSS>/<codeChar>/`**  
Name of fur simulation caches:  
**`<codeChar>_FUR_###_####.fur`**

#### Common FX workflow
Whatever technique and software used for FX creation the final data for transferring in render scene located in:  
**`<rootScenes>/FX/SHOTS/<codeRSS>/`**  
Name for Maya scenes with FX:  
**`<codeFX>_E<codeSequence>_S<codeShot>_###.mb`**

Version of FX file, cleaned up from unnecessary for the rendering process data, has to be published with [FX Manager](03-tools#fx-manager).  

Paths for cashing simulation data.  
Location of ABC output:  
**`<rootProject>/PROD/3D/cache/alembic/FX/SHOTS/<codeRSS>/<codeFX>/`**  
ABC Name:  
**`<codeFX>_ E<codeSequence>_S<codeShot>_001.abc`**  
Location of VDB output:  
**`<rootProject>/PROD/3D/cache/VDB/< codeRSS >/<codeFX>/v###/`**

If for any reasons FX need to be rendered separately from the master layer, place renders:  
**`<rootProject>/PROD/RENDER_3D/RENDER/<codeRSS>/<codeFX>/v###/`**  
Name FX renders:  
**`<codeFX>_E<codeSequence>_S<codeShot>_v###.####.exr`**

**Playblast** of particular FX in each shot could be done with **PLAYBLAST** button of [Animation Manager](03-tools#animation-manager).  
Location of FX playblasts:  
**`<rootProject>/PROD/RENDER_3D/BLAST/<codeRSS>/<codeFX>/`**  
Name of FX playblasts:  
**`<codeFX>_ E<codeSequence>_S<codeShot>_###_###.mov`**

Importing camera to scene with FX could be done with **IMPORT CAMERA** button of [Animation Importer](03-tools#animation-importer)



## 2D branch 
[2D overview](#2d-branch-general-notes) | [Procedure](#compositing-procedure) | [Output](#output-from-2d-branch)
### 2D branch general notes
2D (compositing) branch is last stage of VFX segment where all shots gets their final look before being graded.

Compositing — is the combining of visual elements from separate sources into single image.

#### Folder structure for compositing branch
The root folder for compositing branch is: **`<rootProject>/PROD/2D`**

All compositing data (Nuke files and compositing python scripts) exists in this folder. Inside compositing root we have folder COMP — folder with Nuke scripts for whole project, organized according to film structure:  
**`<codePart>/<codeSequence>/SHOT_<codeShot>`**

For each shot Nuke script file has name: **`E<codeSequence>_S<codeShot>_v###.nk`**

Folder with python scripts, gizmoz, plugins and templates:
**`<rootProject>/PREP/PIPELINE/DNA/2D`**

#### Compositing tools
[compositing tools](03-tools#toolset-for-2d-branch)

### Compositing procedure.
After 3D preview render of key frames is done (FTrack Lookdev task switched to pending review, Compositing task — to Ready to start ) compositing artist assemble shot: creates Nuke script with loader and write nodes with a help of Shot Assembler. Compositing artist has to check rendered frames for errors (visible defects, masks and passes ), make rough compositing, render JPGs and publish shot. If mistakes in render found — create Error report in Ftrack (note to Compositing task) addressed to Lighting and Rendering TD.

After 3D render of sequence is done (FTrack Rendering task switched to complete) compositing artist finalize shot using artistic review as a reference, render sequence of MOV, JPG, DPX, publish shot in Ftrack, switch compositng task from ready to start to pending review.

### Output from 2D branch
Rendered shots from Nuke for color grading process:  
**`<rootProject>/PROD/RENDER_2D/DPX/<codeSequence>/SHOT_<codeShot>/v<###>/`**  
**`E<codeSequence>_S<codeShot>_v<###>.####.dpx`**  
Rendered shots from RENDER_2D for editing process:  
**`<rootProject>/PROD/RENDER_2D /MOV/<codeSequence>/SHOT_<codeShot>/`**  
**`E<codeSequence>_S<codeShot> _v<###>.mov`**  
Rendered shots from RENDER_2D for ART department:  
**`<rootProject>/PROD/RENDER_2D/JPG/<codeSequence>/SHOT_<codeShot>/v<###>/`**  
**`E<codeSequence>_S<codeShot>_v<###>.####.jpg`**

## Art 
### Art general notes
ART root folder is: **`<rootProject>/PREP/ART/`**  
Concept art for assets: **`<rootProject>/PREP/ART/ASSETS/`**  
Color KEY for shots: **`<rootProject>/PREP/ART/SHOTS/<codeRSS>/CLR_E040_S005_001.jpg`**

## Editing and grading
### Editing and grading general notes
Editing and grading process combined into one brunch. Editing and grading root folder:  
**`<rootProject>/EDIT`**

### Editing
Editing is the art, technique and practice of assembling shots into a coherent sequence.

Folder with Adobe Premiere project files: **`<rootProject>/PRO`**  
Folder with SRC sound: **`<rootProject>/EDIT/SRC/SOUND`**  
Render sound for 3D department: **`<rootProject>/PROD/3D/sound/REEL_01/050/E050_S010_001.wav`**  
Folder with editing preview: **`<rootProject>/EDIT/OUT`**  
Editing preview by episode : **`<rootProject>/EDIT/OUT/REEL_01/150/R01_E150_v003.mp4`**  
Editing preview by REEL: <**`rootProject>/EDIT/OUT/REEL_01/REEL_01_v001.mp4`**

### Grading
Grading is a process of changing color of a motion picture (film) for enhancing and adopting to a cinema screen. The source materials for grading process:
- [Compositing branch](#2d-branch) output renderings of each shot as `*.dpx` sequences 
- Movie editing information as `.edl` or `.xml` files

#### Input data for grading 
Final rendered shots from COMP department in **10 bit DPX cineon** color space:  
**`<rootProject>/PROD/RENDER_2D/DPX`**  
XML of movie edit:  
**`<rootProject>/EDIT/PRO/EDL/MASTER/MASTER_v001.xml`**  
Reference MOV with corresponding to XML version:  
**`<rootProject>/EDIT/OUT/MASTER/MASTER_v001.mp4`**  
Brief for colorist (color key etc.):  
**`<rootProject>/PREP/ART/SHOTS/REEL_01/CLR_REEL_01_01.jpg`**  
Sound: **`<rootProject>\EDIT\SRC\SOUND`**

#### Output data from grading
DCP: **`<rootProject>/EDIT/GRAD/DCP`**  
Video files for TV and Internet : **`<rootProject>/EDIT/GRAD/FORMATS`**

#### Project with shooting materials
SRC from shooting: **`<rootProject>/EDIT/SRC/MATERIALS/<codeRSS>`**  
Convert SRC for production needs: **`<rootProject>/EDIT/OUT/PROD/JPG/<codeRSS>`**