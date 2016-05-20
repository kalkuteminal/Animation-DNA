![](https://lh3.googleusercontent.com/-rYMdUijDKrw/Vx9kgbxcs-I/AAAAAAAAFbE/LCNUQEhv7Z0jAqKRcWH-Otb980u5_XZKQCCo/s700/bannerDNA_quickstart_03.jpg)

### Making a template shot step by step.

This document will guide you through the base steps of animation feature film production using **Animation DNA** system.
We will create an example shot from the beginning (storyboard) till the end (edited movie ready for grading). To learn more about any pipeline details read [Codex DNA](https://github.com/kiryha/AnimationDNA/wiki/02-Codex-DNA)

**A)** [Preproduction](#preproduction)  
**B)** [Production:](#production)  
 [Asset creation](#asset-creation)  |  [Look development](#look-development)  |  [Animation](#animation)  |  [Rendering](#rendering)  |  [Compositing](#compositing)  
**C)** [Advanced techniques](#advanced-techniques)

## Preproduction. 
Lets [setup FTrack database](02-codex-dna#management-with-ftrack)

Assume we need to deliver an animated shot with a character holding an apple in a street.
Like in DNA banner at [home page](https://github.com/kiryha/AnimationDNA/wiki).

At the base level of project organization we have to deal with two substances: **ASSETS** and **SHOTS**.
This core division permeates through a project workflow and reflected in database and folder structure.
First we need to create necessary assets and shots in database, link assets to shots, setup shots length, then we can start production.

According to [asset classification system](02-Codex-DNA#asset-creation) we need to create such assets with a proper [type](02-codex-dna#asset-types-in-ftrack):
* character asset — Bender 
* dynamic prop asset — apple 
* environment asset — New-York city street 
* environment dynamic asset (EDA) — traffic light

Also we need to create one **shot** and link animated assets to this shot. Note, that EDA are linked to the environments, not to a shots. This allow to create shot links faster: you link environment to a shot, and all EDA links automatically. 

According to [film structure system](02-Codex-DNA#structure-of-film) it will be: **REEL_01 > 010 > SHOT_010**

### Setup project on HDD
Extract [Animation DNA archive](02-codex-dna#dna-archive) to your projects folder, rename root folder to a project name.  
**`<rootProject>`** – is a full path to the renamed folder (P:/DNA/ in this case)

### Setup project in database
In FTrack database create DNA project. **Project name in FTrack should match project root folder name**.  
Create in FTrack root:
* **ASSETS** folder.  
In ASSETS folder create a structure the same as in **`<rootProject>/PROD/3D/scenes/ASSETS/`**  
In CHARACTERS folder create Asset Build with type characters and name BENDER. Use BENDER_TMB_01.jpg as thumbnail image from: **`<rootProject>/PREP/ART/ASSETS/CHARACTERS/BENDER`**
In ENVIRONMENTS folder create NYC folder and inside create Asset Build with type environment and name NYC. In EDA folder create Asset Build with type eda and name nycLitght.
In PROPS folder create Asset Build with type prop and name fooApple.
* **REEL_01** episode.  
In **REEL_01** create sequence **010** and inside it create shot **SHOT_010**  
Now link BENDER, fooApple and NYC assets to a shot.  

If DNA project already exists in FTrack, just learn how it was build.  
![](https://lh3.googleusercontent.com/-cI5QOWjY1H0/VyHxKJ3bB4I/AAAAAAAAFek/YrUVtebFJ9o084FPLGA5FG6JeDUM_SQ_gCCo/s1440/gettingStarted_FTR_04.gif)

For JSON version use template in **`<rootProject>/PREP/PIPELINE/DNA/DIC`**  
Edit file in [online JSON editor](http://www.jsoneditoronline.org) to setup database as it was described for Ftrack above. 
![](https://lh3.googleusercontent.com/-I_Id6RqtBdM/VyHxNL5rYAI/AAAAAAAAFeo/ZXFQiNB69AcU4sipVbScrUDj05gjeDL8ACCo/s1440/gettingStarted_JSN_03.gif)

For correct workflow you need to have **SHOT** with linked assets in the database.  
Each asset, linked to a shot, should be **published** in database with particular data for each asset type:
* RIG, GEO, MAT, FUR ( if used in project ) – for  the **character** type; 
* GEO and MAT — for the **environments** (with published EDA list); 
* RIG and GEO for the **props** and EDA.

## Production.
[Asset creation](#asset-creation)  |  [Look development](#look-development)  |  [Animation](#animation)  |  [Rendering](#rendering)  |  [Compositing](#compositing)

Now we can start production procedures which generally would go in a way:  
**asset creation > animation > render > compose**  
Go to **`<rootProject>/PREP/PIPELINE`** and [run Maya through wrapper](02-codex-dna#running-maya-and-nuke-with-wrappers) 

## Asset creation
![](https://lh3.googleusercontent.com/-EOh7UMVvEck/Vma3M-o-LBI/AAAAAAAAFJw/orreZbXZcSAaci4bC0NMcLV_M64q6ZvdACCo/s1152/WIP_BROAK_01.gif)

[Static assets](#static-assets)  
[Environment assets](#environment-assets)  
[Dynamic assets](#dynamic-assets)  
[Environment dynamic assets](#environment-dynamic-assets)  
[Character assets](#character-assets)   

### Static assets
 
Open [static asset](02-codex-dna#asset-creation-general-notes): **`<rootScenes>/ASSETS/STATIC/FLORA/TREES/trsMelony_001.mb`**  
This is finished [GEOMETRY form](02-codex-dna#asset-forms) of a tree asset. Objects are combined by the materials, have proper names (**`<assetName>_<letterNumber>_<partName>`**) with assigned preview materials using JPG textures. Proxy object modeled also. It is ready to be converted to STANDIN form according to pipeline requirements. 

Save file as new version (**SNV**). Run [Asset Manger](03-tools#asset-manager), select asset parts, select proxy and press **SETUP STATIC**. Deselect all, press **PROXY** button and see how asset switches between proxy and rendering mode. Notice asset structure in outliner with “show shapes” enabled.  
Select asset parts, press **ADD ATTR** and notice custom attributes mColor, mDisp, mMat in extra attributes section of object shapes. Press **GET COLOR** to write texture path to mColor attribute. Enter material names to mMat attribute: **GEN_PLANT_A** for trsMelony_D_leaves and **GEN_BARK_A** for trsMelony_D_trunk.  

Select asset parts and set Arnold rendering subdivision with **2** button. 
Delete all shading nodes. Try to select asset parts and press **SHOW TX** — preview shader with proper textures would be created and assigned to corresponding objects. Press **CLEAN TX** to delete all preview shading nodes. Save scene.

**Prepare asset for Arnold rendering.**  
Run **ASM**. See important note about re-running scripts in codex DNA.  
Select asset root node ( **trsMelony_D_001** ) and press **CONVERT TO STAND IN**.  
Do not save scene!.  

Open: **`<rootScenes>/ASSETS/STATIC/FLORA/TREES/SI/trsMelony_D_SI_001.mb`**  
This is finalized asset which should be added to an asset library. Fill environments with such assets from different libraries according to you project tasks.  
Press **PROXY** button to switch between preview and rendering modes, press **STANDIN** to switch between wireframe and bounding box mode of Arnold standin (turn OFF viewport 2.0).  
Switch to rendering mode, run **Render Manager** and press **REFLOOKDEV DATA**, **ASIGN MATERIALS**. Render asset to check everything is working properly. Check if you have **TX textures** for asset (they are not included in AnimationDNA archive), if not — convert JPG textures to TX format

To create database of static assets images save render to:  
**`<rootProject>/PROD/RENDER_3D/LOOKDEV/ASSETS/STATIC/TREES/trsMelony_D_01.tif`**  
Use this image in FTrack as asset thumbnail.

Under the hood of  **CONVERT TO STAND IN** button: see **Asset structure** section in codex DNA.  
See how to [convert to standin complex assets](#complex-static-asset-setup). The technique when you replace heavy polygonal geometry with Arnold standin and proxy object can be used for complex objects in environment assets scenes.
![](https://lh3.googleusercontent.com/-E6xa0Z5zTpA/VyH0x7WHc_I/AAAAAAAAFe0/0im-hvjxm2YT5bEfTa1J6GB6AlAwgVxpQCCo/s1152/gettingStarted_ASS_02.gif)

### Environment assets
Open [environment asset](02-codex-dna#asset-creation-general-notes): **`<rootScenes>/ASSETS/ENVIRONMENTS/NYC/ENV_NYC_001.mb`**  
Note that several instances of static asset rsMelony was used to fill environment. We need to register particular information about environment asset in project database, in other words, we need to publish an asset in database.

Run **Data Publisher**, press **ANALYSE CURRENT ASSET**.
Field under analyze button should fill with asset name (NYC). Field in front of GEO button should fill with asset filename (ENV_NYC_001.mb). If its not happening either Maya **file name** is wrong or there is no such asset in database.

Press **GEO** button to write information about file in project database (publish asset). Script editor should print massage:  
**<<  PUBLISHED ASSET [ NYC ]: GEO = ENV_NYC_001.mb  >>**  
This mean that publishing was successful.

With FTrack version of database each publishing operation written into asset or shot note in FTrack with the following information: publishing value, user, time.

![](https://lh3.googleusercontent.com/-j1dtRKoDz5M/VyIM1P3_YUI/AAAAAAAAFfI/hQCtwn4ETIgOKku1zjg6gg79uICdA_65ACCo/s1440/gettingStarted_ENV_04.gif)

### Dynamic assets
Open [dynamic asset](02-codex-dna#asset-creation-general-notes): **`<rootScenes>/ASSETS/PROPS/FOOD/GEO/GEO_fooApple_001.mb`**
This is finalized geometry with necessary custom Arnold attributes and proper names.
Save file as new version (SNV). Run [Asset Manger](03-tools#asset-manager), select asset parts, select proxy and press **SETUP DYNAMIC**. Save scene.

Run [Data Publisher](03-tools#data-publisher) and press **ANALYSE CURRENT ASSET**. Field in front of GEO button should fill with **FOOD/GEO/GEO_fooApple_002.mb**. Press **GEO** button.
Re save Maya scene as **`<rootScenes>/ASSETS/PROPS/FOOD/RIG/RIG_fooApple_001.mb`**
Rig asset and place all controls and rig nodes into **fooApple_RIG** group. Run [Data Publisher](03-tools#data-publisher) and publish rigged asset with **RIG** button.

![](https://lh3.googleusercontent.com/-NNhez_joMvo/VyIQv7rtlYI/AAAAAAAAFfY/Z4S_-T5iHWUlaTQJGkw_Cb5RVseFuxe1ACCo/s1440/gettingStarted_DYN_01.gif)

### Environment dynamic assets
Open and publish [environment dynamic asset](02-codex-dna#asset-creation-general-notes):
* **`<rootScenes>/ASSETS/ENVIRONMENTS/NYC/EDA/GEO/GEO_nycLight_001.mb`**
* **`<rootScenes>/ASSETS/ENVIRONMENTS/NYC/EDA/RIG/RIG_nycLight_001.mb`**

Now **link** nycLight **asset to** NYC **environment**  
Open environment scene: **`<rootScenes>/ASSETS/ENVIRONMENTS/NYC/ENV_NYC_001.mb`** run [Data Publisher](03-tools#data-publisher), press **ANALYSE CURRENT ASSET**, enter **nycLight** in text field in front of EDA button and press **EDA**. 

Message in script editor (<<  PUBLISHED ASSET [ NYC ]: EDA = nycLight  >>) means successful data publishing. Check if EDA key of NYC environment in database now filled with nycLight value.  
If you will need more environment dynamic assets later, you need to publish full list each time, because this list replace old one, but not append.

![](https://lh3.googleusercontent.com/-HfRXL-mf5ko/VyIQv5pH42I/AAAAAAAAFfU/Z7nr7oMtpQUrItjvbHDYWU0DCTXofUN0gCCo/s1440/gettingStarted_EDA_01.gif)

### Character assets
The procedure for [character assets](02-codex-dna#asset-creation-general-notes) similar to dynamic assets. Open and publish [**RIG** and **GEO** forms](02-codex-dna#asset-forms) of BENDER asset:  
**`<rootScenes>/ASSETS/CHARACTERS/BENDER`**

**Rigging notes**.  
Process of characters or props setup specific for each project so there is no detailed explanation of this topic. 
Base statement of Animation DNA pipeline in setup procedure is that **animation transfers to rendering through alembic caches**, so whatever rigging system is used it should works with ABC caches correctly. For example better avoid parenting with constrains and use skinning to one joint instead. 

Long time opening scene with reference and ABC cashes issue can be solved with importing reference to a scene.
See ASSET CREATION — SETUP in codex DNA for more details.

![](https://lh3.googleusercontent.com/-pDlzGALmv2g/VyIRDLmk_VI/AAAAAAAAFfc/Wv8K5atgQjgNgk-0_nlpajHyNeC3jX3ywCCo/s1440/gettingStarted_CHR_01.gif)

## Look development
![](https://lh3.googleusercontent.com/-xJHXAP4iVVU/U8j1ZD2vMnI/AAAAAAAAErg/MYPLu5yIyTg5h9C9bGNIzm3p5JfoywBOQCCo/s800/L01_V001_sm.jpg)

Open **`<rootScenes>/LOOKDEV/LIBRARY/MATERIALS/SETS/SET_GENERAL_001.mb`**  
Check GEN_BARK_A shading network. Shader has name GEN_BARK_A, shading group has name GEN_BARK_ASG. Scripts refer to a shading group name, so it should be correct. 

There is a function (**RENAME MATERIAL**) in [Render Manager](03-tools#render-manager) which allows to give a proper name to all shading nodes of particular material.

Resave scene as:  
**`<rootScenes>/LOOKDEV/LIBRARY/MATERIALS/ASSETS/ENVIRONMENTS/NYC/MAT_NYC_001.mb`**  
Publish scene with **MAT** button of [Data Publisher](03-tools#data-publisher) (press **ANALYZE CURRENT ASSET** first).

Open and publish **BENDER** material library:  
**`<rootScenes>/LOOKDEV/LIBRARY/MATERIALS/ASSETS/CHARACTERS/BENDER/MAT_BENDER_001.mb`**

See [Look development and rendering](02-codex-dna#look-development-and-rendering) for more details.


![](https://lh3.googleusercontent.com/-tEYz4_tDe6M/VyIRIAIF5RI/AAAAAAAAFfg/TotcCl9FDigTJqqz0jHfI0DTYdBWATNcgCCo/s1440/gettingStarted_LDV_01.gif)

## Animation
With an empty scene run [Shot Assembler](03-tools#shot-assembler) (**SHA** button on DNA shelf).  
Enter **REEL_01, 010** and **010** in **PART, SEQ** and **SHOT** fields.  
Press **CREATE ANIMATION SCENE** button. 

Shot Assembler:
* creates Maya scene located in:  
**`<rootScenes>/ANIMATION/REEL_01/010/SHOT_010/ANM_E010_S010_001.mb`**
* reference [RIG forms](02-codex-dna#asset-forms) of all assets , linked to a shot in project database
* create camera with the name of sequence and shot 
* setup scene playback range

If everything went successful script editor should print massage **ASSEMBLING DONE**! 

![](https://lh3.googleusercontent.com/-BMBocZ_qaoc/VyIRiI_Xv4I/AAAAAAAAFf0/dIi9zK7oVy8adR27g4W04VTRkBW9djXWACCo/s1440/gettingStarted_ANM_03.gif)

Make a draft animation, expand camera window, run [Animation Manager](03-tools#animation-manager) and press **PLAYBLAST** button. Movie file:  
**`ANM/ANM_E010_S010_001_001.mov`**
saved in:  
**`<rootProject>/PROD/RENDER_3D/BLAST/REEL_01/010/SHOT_010/ `**


### Exporting animation
After finishing animation you have to export animation data, so you can import animation in render scene later.  
Run [Animation Exporter](03-tools#animation-exporter) and press **EXPORT ALL ANIMATION**. For each animated asset and camera generated alembic cache file in:  
**`<rootProject>/PROD/3D/cache/alembic/REEL_01/010/SHOT_010/`**

### Checking scene
Try to create and publish next version of BENDER RIG asset. Open animation scene, remove fooApple asset in reference editor. Press **CHECK SCENE**. Read report in script editor. 
* **WRONG VERSIONS: BENDER** — mean that version of asset in scene mismatched to a version of asset in database. 
* **MISSING ASSETS: fooApple** — mean that animation scene lack a fooApple asset.

Press **FIX ALL** and check scene again. New version of BENDER loaded to a scene and fooApple also added.  
Do not save this scene.


## Rendering
![](https://lh3.googleusercontent.com/-__zf9cFSUq0/Vyhf9PQvkgI/AAAAAAAAFhs/E8_Y8s-5tV8_nr0SMwxlYgkx2kjcl2vngCCo/s800/WIP_MELONY_SM_02.gif)

With an empty scene run [Shot Assembler](03-tools#shot-assembler). Press **CREATE RENDER SCENE** button.

Run [Animation Importer](03-tools#animation-importer) and press **IMPORT ALL ANIMATION**.

Create lighting or import outdoor light template from:  **`<rootScenes>/LOOKDEV/LIBRARY/LIGHTS/OUTDOOR/LIT_OUTDOOR_001.mb`**
With nothing selected run [Asset Manger](03-tools#asset-manager) and press **PROXY**. Notice how **trsMelony_D** switched from proxy to render mode.

Run [Render Manager](03-tools#render-manager) and press **ASSIGN MATERIALS**. This procedure assign materials to all objects in scene according to **mMat** attribute. 

Press **RENDER SETTINGS** and **HIGH**. This will setup name, extension and path to output image, frame format, frame range and Arnold sampling in render settings window. Render camera.

Notice that the apple is green. This is because there is a green texture in image file node of apple material. 
Open Attribute editor for **IFL_GEN_PLANT_A_CLR**, change ImageName value from:  
**sourceimages/TILES/TIL_PLANT_A_CLR_01.jpg** to:  
**`<rootProject>/PROD/3D/sourceimages/<attr:mColor>`**

You need to enter **absolute full path** before **`<attr:mColor>`** token which is correct for you project location. Now Arnold refer to texture noticed in **mColor** attribute and apple become red.

With nothing selected press **ADD SHADER ID** button in Render Manager and answer **YES**. Check AOVs tab in render settings, there are IDs for all shaders in the scene with **IDS_** perfix.  
Press **ADD ASSET ID** and check AOVs, for each asset there are ID wit **IDA_** prefix.  
Press **ADD PASSES**. This adds list of pre-defined and custom AOVs (ambient occlusion, UVs etc).  
Press **PUB** button to publish render in database (**EXR = v001/E010_S010_001.%04d.exr**) and **RENDER SHOT** to generate ASS sequence to a folder:  
**`<rootProject>/PROD/3D/data/REEL_01/010/SHOT_010/001`**

Render ass sequence with Deadline or other manager or you can just batch render scene.

![](https://lh3.googleusercontent.com/-5N4mYVrkGZM/VyIRILotGNI/AAAAAAAAFfo/RlSfzFSOLPYMkLG5tUVi35YtSYPNuSZDgCCo/s1440/gettingStarted_RND_03.gif)


## Compositing
![](https://lh3.googleusercontent.com/-mnKqLHqaUPY/Vyx2oQJWDrI/AAAAAAAAFkU/We1sfdBosIUAXkEdZ_pbpy9qDB9hpeMGQCCo/s700/E010_S010_v003.jpg)

[Run Nuke through wrapper](02-codex-dna#running-maya-and-nuke-with-wrappers).  
Run **DNA > Shot Assembler** and create nuke script by entering shot number (REEL_01, 010, 010) and pressing **ASSEMBLE**.  
Current version of Shot assembler builds simple NK script with published 3D render and 2 write nodes with correct output formats and paths.

Compose sequence and render MOV and DPX files. Render from compositing department for this shot located in:  
**`<rootProject>/PROD/RENDER_2D/DPX/REEL_01/010/SHOT_010/v001/`**  
**`<rootProject>/PROD/RENDER_2D/MOV/REEL_01/010/SHOT_010/`**

Publish 2D render with **DNA > PUBLISH**

![](https://lh3.googleusercontent.com/-z38m_540cec/VyIRIHXxThI/AAAAAAAAFfk/IarpwItOIwwoRAiKDC95xhDfD6LjeeN7ACCo/s1440/gettingStarted_CMP_01.gif)

## Advanced techniques
![](https://lh3.googleusercontent.com/-nTN8bwIe_p8/VlWxDOSgNZI/AAAAAAAAFGQ/TcT7NsqQSMAL0fjh-TH45ajtdm_Ann_TgCCo/s800/WIP_SET_TREES_SM_01.gif)

### Complex static asset setup.

Open **`<rootScenes>/ASSETS/STATIC/FLORA/TREES/brnOak_001.mb `**  
This is model of the oak branch which has three variations (A, B, C) with common for static assets structure, when all objects with the same material combined to one peace, so each asset consist from the proxy, branch and leaves objects with a proper Arnold custom attributes (to setup texture paths, material names, render subdivision etc). Each variation converted to standin version of asset (in SI folder).
Open **`<rootScenes>/ASSETS/STATIC/FLORA/TREES/trsBroak_001.mb`**  
and switch to the rendering mode (**ASM > PROXY**)  
This is model of a tree which consist from a proxy object, a polygonal trunk and a crown group. Crown was built from the number of instanced standin versions of oak branch asset. Now we need to convert this asset with a group of nested assets to final standin version. 

The procedure remains the same: we need to combine all leaves to one object and all branches to another. In case of instanced assets we actually does not combine objects as we do it with polygonal objects. The way we combine a number of standins assets: export list of objects you need to join to a new standin and import it back as a new combined object.

trsBroak_A_crown group contains leafs:
* ASS_brnOak_A_leaves
* ASS_brnOak_B_leaves
* ASS_brnOak_C_leaves  
and branches:
* ASS_brnOak_A_body
* ASS_brnOak_C_body
* ASS_brnOak_C_body

Select three leave standin objects (e.g. select by name **`*_leaves`** in input box of status line), press **SI** button of [Asset Manger](03-tools#asset-manager) to select all leaves in a crown, press **SHIFT + P** to bring all leaves to the scene root. Go to **Arnold > Standin > Export** and export leaves to:  
**`<rootScenes>/ASSETS/STATIC/FLORA/TREES/ASS/trsBroak_A_leaves_001N.ass`**

Undo un-parent action to leave crown group unbroken.

Do the same actions with branches (**`*_body`**):  
**`<rootScenes>/ASSETS/STATIC/FLORA/TREES/ASS/trsBroak_A_branches_001N.ass`** 

Also, export tree trunk as:  
**`<rootScenes>/ASSETS/STATIC/FLORA/TREES/ASS/trsBroak_A_trunk_001N.ass`** 
 
Now go to **Arnold > Standin > Create** and select trsBroak_A_leaves_001N.ass to create crown leaves combined object, trsBroak_A_branches_001N.ass to create crown branches and trsBroak_A_trunk_001N.ass to create standin of a trunk.

Save Maya scene as **`<rootScenes>/ASSETS/STATIC/FLORA/TREES/SI/trsBroak_A_SI_001.mb`** 

Rename ArnoldStandIn to ASS_trsBroak_A_leaves, ArnoldStandIn1 to ASS_trsBroak_A_branches, ArnoldStandIn2 to ASS_trsBroak_A_trunk

Now we need to copy custom Arnold attributes from source objects to a new standin objects.  
Select ASS_trsBroak_A_leaves, SHIFT select ASS_brnOak_C_leaves and press **COPY ATTR** button of Asset Manager. Notice, now ASS_trsBroak_A_leaves has mColor, mDisp, mMat attributes with the same values as in ASS_brnOak_C_leaves. Copy attributes for ASS_trsBroak_A_branches and ASS_trsBroak_A_trunk from corresponding source parts.

Keep in mind, while model asset parts which would be combined later (like oak branches), that all asset variation (for each part) has to share same texture (all asset variations unwrapped in one UV space) to allow textures on combined objects works properly! 

Rename trsBroak_A_Geo group to trsBroak_A_Ass, delete all parts inside (trsBroak_A_crown group and trsBroak_A_trunk geo) and place ASS_trsBroak_A_leaves, ASS_trsBroak_A_branches and ASS_trsBroak_A_trunk in trsBroak_A_Ass. Save scene.

Switch to the rendering mode (**PROXY** button of **ASM**), run [Render Manager](03-tools#render-manager), press **REF LOOKDEV DATA**, **ASIGN MATERIALS** and render asset to check if everything is working fine.

![](https://lh3.googleusercontent.com/-P2SPA9fex5w/VyIRIQrK-BI/AAAAAAAAFfs/FEEvPWUxH20t2MRYJttM_XvRF-jKvB1HwCCo/s1280/gettingStarted_complexAsset_02.gif)