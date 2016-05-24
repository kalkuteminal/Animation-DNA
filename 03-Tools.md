![](https://lh3.googleusercontent.com/-FjTtyFyai18/VyCMyf2DaSI/AAAAAAAAFdQ/2qMu8N2pJU8YzGfHvCT4qju44lCpnDLxQCCo/s700/bannerDNA_tools_01.jpg)

Animation DNA contains set of python tools for 3D and compositing [branches](02-codex-dna#structure-of-film-and-production). Tools may has small differences between JSON and FTrack versions.

Variety of pipeline actions (like save scene, export cache, assign material etc) formulated as python procedures. This procedures groped into sets related to pipeline phases and each set is a DNA tool. Below is a full list of Animation DNA tools with general tool description and explanation of each of procedure.

### Toolset for 3D branch
![](https://lh3.googleusercontent.com/-nLLQUcdwfN4/VyNdA4VLMCI/AAAAAAAAFhU/kREzq205CisDnIxyqk7pT_qhrNSdKP6pACCo/s388/DNA_shel_01.jpg)
[ATM](#attribute-manager) | [ASM](#asset-manager) | [SHA](#shot-assembler)

In Maya all DNA tools located in DNA shelf, which should appear if you [run Maya through wrapper](02-codex-dna#running-maya-and-nuke-with-wrappers).

#### Attribute Manager
**ATM** button on DNA shelf. Attribute Manager allow to create, set and edit custom MtoA attributes on geometry shapes. Refer to a [token tutorial](06-Tutorials#setup-per-object-attributes) for explanation.

![](https://lh3.googleusercontent.com/-_Lm1C3ipF-U/VyNZ01v-GZI/AAAAAAAAFgs/J2eV2PqQaYYo-Eo4V6IHNrmLUiVdmavPQCCo/s300/DNA_attrManager_01.jpg)

#### Shot Assembler
**SHA** button on DNA shelf. Creates animation and render scenes for each shot based on information about shots and assets in FTrack, check rendering and animation scenes: if they contains all necessary assets and does this asset has proper versions, update asset versions and add missing assets, add assets, props or environment to opened scene by asset code. Creating animation scene include: save scene to proper place with proper name, setup frame range, reference RIGs of all necessary assets, create and setup camera. Creating render scene include: save scene to proper place with proper name, setup frame range, reference GEO of all necessary assets, create FUR nodes and importing all necessary material library’s(individual library for each character and proper SET for environment and assets.) 
#### Asset Manager
**ASM** button on DNA shelf. Modelling tool which allow to setup each asset according to pipeline requirements.  
Create and set custom MtoA attributes. Add and modify render data — textures and material names. Check if asset is prepared correctly. Organize geometry to proper hierarchy. Convert geometry asset to standin asset.

![](https://lh3.googleusercontent.com/-kholsPnoGxU/Vx-W5hpSfdI/AAAAAAAAFc0/h6rS_KxrioYv7EQY2rpvXDHG-ukTMqCewCCo/s430/DNA_assetManager_06.jpg)

* **ADD ATTR** — create MtoA custom attributes (mColor, mMat, mDisp) on selected object shapes to store shading information in every asset for Arnold. Refer to a [token tutorial](06-Tutorials#setup-per-object-attributes) for explanation.
* **COPY ATTR** — copy MtoA attribute values onto selected objects from last selected object.
* **LINE** — line up selected assets from center of scene in a row.
* **CRV** — open curve editor window to modify properties of NURBs curves for Yeti.
* **SI** — select instances of selected object.
* **BBOX** — display selected shapes as bounding boxes.
* **DEL Z** — delete GoZ attributes on selected objects.
* **MAYA SMOOTH OFF [0][1][2][3][4]** — Turns off Maya smooth shape during render (when pressing 3 key), set Arnold subdivision on selected shapes from 0 to 4. Setting Arnold subdivision with [0-4] buttons also turns off Maya smooth.
* **GET COLOR** —for each of selected object: copy file texture name into mColor attribute (replacing JPG extension with TX) from image file texture node of shader, assigned to each object.
* **GET DISPL** — for each of selected object: copy file texture name into mDisp attribute from displacement image file texture node of shader, assigned to each object.
* **GET MATERIAL** — copy name of assigned material to mMat attribute.
* **SHOW TX**— read texture name from mColor attribute, create and assign lambert shader(preview shader) with this texture on of each selected object.
* CLEAN TX — delete all preview shaders.
*  **SET MATERIAL** — set mMat attribute with text rom field (GEN_BASE_A)
* **SETUP STATI**C — creates STATIC asset hierarchy structure for selected objects according to static asset organization rules. Select asset geo, select proxy geo, press SETUP STATIC. 
* **SETUP DYNAMIC** — creates DYNAMIC asset hierarchy structure for selected objects according to dynamic asset organization rules.
* **PROXY** — trigger asset display between PROXY and RENDE mode. Selective sensitive. Works for all assets in scene if nothing selected, or trigger selected asset. 
* **STANDIN** — trigger Arnold standIn display mode between bounding box and shaded polywire. Selective sensitive. Works for all assets in scene if nothing selected, or trigger selected asset.
* **CHECK SCENE** — Help to control quality of asset — analyze current scene for mistakes for and creates selection sets with problematic objects: ATTR_TRANS — consist objects with MtoA attributes on transform nodes, EMPTY_mColor — objects without data in mColor attribute, EMPTY_mMat — objects without data in mMat attribute, NO_CUSTOM_ATTR — objects without custom attributes, NO_SUBDIV — objects without Arnold subdivision values. If set _SG_ appears — in scene exists extra shading groups, which should be deleted.
* **DEL** — unlock and delete selected nodes to cleanup scenes from unnecessary data. 
* **CONVERT TO STANDIN** — convert static asset with geometry to static asset with standin.

![](https://lh3.googleusercontent.com/-KVVWeDn4PxU/VyDPQUJv64I/AAAAAAAAFeM/WfJ0uB1fnAo-krbXsaYj7PqinC5xpIcEACCo/s380/DNA_shotAssembler_06.jpg)
* **PART SEQ SHOT** — Fields to enter part, sequence and shot to create render or animation scene.
* **CREATE RND/ANM SCENE** — Creates render (animation) scene for shot noticed in PART, SEQ, SHOT fields.
* **CHECK SCENE** — Check, if scene contain all necessary data: assets, props, environment. Check version of each asset. Create report in script editor.
* **FIX ALL** — Add all missing assets and reload proper asset versions.
* **SNV** — Save next version of current scene.
* **ADD CHARS, ADD ASSETS, ADD ENV** — Add missing assets by category.
* **UPDATE SCENE REFERENCES** — Reload proper asset versions.
* **ADD ASSETS** — Enter names of assets you wish to reference to the current scene divided by space.
* **FOR ANM/RND** — Choose RIG or GEO asset version you need to add.

#### Animation Manager
**ANM** button on DNA shelf. Animation Manager is animators tool, creates playblasts, setup camera lenses, preview object textures, analize scene content (availability and versions of characters and assets), update scenes content. 

![](https://lh3.googleusercontent.com/-firZiFKlIhc/VyNa2p3mCoI/AAAAAAAAFhM/5UsmjT2FnWYoXLqM4ZF5tR0Umsr7a6ApACCo/s323/DNA_animManager_04.jpg)
* **PLAYBLAST** — creates playblast of current animation scene.  
If any playblast of this shot already exists — warning window appears, asking to choose either to overwrite existing file or save next version.
* **JPG** — creates screenshot from current frame and set JPG image as thumbnail of corresponding shot in FTrack.
* **TX** — show in viewport texture for selected assets.
* **[12][18][27]…[180]** — set the focal length of scene camera(as well as aperture).
* **LCM** — lock / unlock transform for current viewport (camera).
* **CHECK SCENE** — check if scene has all assets and characters according to properties files and if versions of assets and characters are correct.
* **FIX ALL** — add missing data to scene and update scene references according to shot properties files.
* **SNV** — save next version of current animation scene.
* **UPDATE SCENE REFERENCE**S — replace assets and characters references with the versions noticed in assets properties files. 
* **ADD CARS, ASSETS, ENV** — add missing assets, characters or environment.
* **PUBLISH** — publish version of animation scene to FTrack.

#### Animation Exporter
**EXP** button on DNA shelf. Export animation data from animation scenes through alembic cashes. Allow to work with all animation data at once, by asset types or each asset individually.

![](https://lh3.googleusercontent.com/-a30-ijLsVqw/VyNa5nTf-BI/AAAAAAAAFhM/vzfJvwfV-xk_Y0zaaiUzAmrZs5q8AQSyACCo/s483/DNA_EXP_01.jpg)
* **EXPORT ALL ANIMATION** — export all animated assets and camera from current animated scene to alembic files.
* **EXPORT CAMERA** — export only camera.
* `<characterNames>` — export characters individually
* **EXPORT ALL CHARACTERS** — export all characters.
* `<assetNames>` — export assets individually.
* **EXPORT ALL ASSETS** — export all assets.
* `<EDAName>` — export environment dynamic assets individually.
* **EXPORT ALL EDA**— export all environment dynamic assets.
* **UPDATE REFERENCES** — replace assets and characters references with the versions noticed in assets properties files.


#### Animation Importer
**IMP** button on DNA shelf. Import animation data into render scenes through alembic cashes. Allow to work with all animation data at once, by asset types or each asset individually.

![](https://lh3.googleusercontent.com/-CE71LXxQhYc/VyNa5t5INcI/AAAAAAAAFhM/Vcqx32nyFeAUYB6wxAjzJny6wm8ZtvluwCCo/s517/DNA_IMP_01.jpg)
* **IMPORT ALL ANIMATION** — import all animated assets and camera from to the opened render scene.
* **IMPORT CAMERA** — import only camera.
* `<characterNames>` — import characters individually
* **IMPORT ALL CHARACTERS** — import all characters.
* `<assetNames>` — import assets individually.
* **IMPORT ALL ASSETS** — import all assets.
* `<EDACode>` — import environment dynamic assets individually.
* **IMPORT ALL EDA**— import all environment dynamic assets.
* **IMPORT ALL FUR** — import fur cashes for all characters.
* `<characterNames>` — import fur for characters individually

#### FX Manager
**FXM** button on DNA shelf. Create, manage and publish FX scenes and data.

![](https://lh3.googleusercontent.com/-cIzYkWS1t5k/VyNbFCS0LuI/AAAAAAAAFhM/9zviGTs-tPYw6HNbuxcy5CRPYVPNY9QQgCCo/s298/DNA_FXM_03.jpg)
* **[REEL_01] [SEQUENCE] [SHOT] [ ]** — set reel, sequence and shot to generate fur dynamic files. If enter character name or names separated with comma (C04:CALF,C05:KIRILLA) fur scenes will be created only for this characters.
* **CREATE FUR SIMULATION SCENE** — Run procedure of FUR scenes creation.
* **[REEL_01] [SEQUENCE] [SHOT] FX CODE [ ]** — set reel, sequence, shot and **`<codeFX>`** to generate FX file.
* **CREATE FX SCENE** — Run procedure of FX scene creation.
* **ANALYZE CURRENT FX** — Get FX data from file name to publish in FTrack.
* **PUBLISH FX** — Publish FX data from field below to FTrack.
* **[  ]** — Field with FX data to publish.

#### Data Publisher
**PUB** button on DNA shelf. Deliver information about asset to FTrack database. Depending on asset type, data publisher add([publish](02-Codex-DNA#publishing-data-to-ftrack)) information about asset paths: geometry or setup file, fur, materials, environment assets linked to environment(EDA). 

![](https://lh3.googleusercontent.com/-B5FxvT5OEyQ/VyNa3u59FII/AAAAAAAAFhM/JX0lOS32dIYyn-83NEqtGpt93B30koJxQCCo/s298/DNA_dataPublisher_03.jpg)

#### FTP Manager
**FTP** button on DNA shelf. Upload animation scenes and linked references on mirror FTP. Do not load environment assets automatically.

![](https://lh3.googleusercontent.com/-DzyPLHHnB74/VyNa65RCVXI/AAAAAAAAFhM/kYFZpYqkNPcr4ZgsKoZwymgImIK2f1vsACCo/s299/DNA_ftpManager_02.jpg)

#### Render Manager
**RND** button on DNA shelf. Rendering and look development tool. Setup shots for rendering: assign materials, create passes, object and shader IDs, setup render settings (image size, render path and name etc ) and export ass for renderfarm rendering.

![](https://lh3.googleusercontent.com/-upfRXIYEWZI/VyCwXf8kGlI/AAAAAAAAFds/2wjzCG2mT3EWtMcKPTw0c8fEM5bs4troQCCo/s490/DNA_renderManager_06.jpg)
* **REF LDV DATA** — reference material general library and sun and sky system to current scene.
* **DOF** — add DOF setup to drive depth of field to a selected camera.
* **ADD FUR** — Creates yeti nodes for all character in current scene (based on FTrack info)
* **RENAME MATERIA**L — name all nodes of selected shading group network.
* **EXPORT XGEN** — export Xgen data for render scenes from lookdev scene (where Xgen developing).
* **IMPORT XGEN** — import XGen description in render scene.
* **IMPORT MATERIALS** — import material library of each asset from text field.
* **ASIGN MATERIALS** — assign materials to all polygonal object in scene.
* **FOR SELECTED** — assign materials to selected polygonal objects.
* **SELECT SG ALL GEO** — select shading groups of all(or only selected with button SELECT SG SEL) geometry in scene.
* **ADD SHADER ID** — add AOV IDs for each shading group in scene if nothing selected. If any shading group selected — adds AOV only for selected SG. Using aiWriteColor method for this: create AOV and add aiWriteColor node to shading network. Refer to a [AOV tutorial](06-Tutorials#object-and-material-aovs) for explanation.
* **DEL SHADER ID** — delete AOV and aiWriteColor node from network for each selected aiWriteColor node, or for all shader IDs if nothing selected.
* **OBJECT ID** — add object AOV for each selected object(or group).
* **ADD ASSET ID** — add object IDs for each character, asset and environment in scene. Based on naming selection.
* **ADD PASSES** — add set of predefined and custom AOVs in current scene(e.g. direct diffuse, indirect diffuse, ambient occlusion etc).
* **RENDER SETTINGS** — setup render global for each scene — output name and path, frame format, camera, Arnold settings etc.
* **HIGH** and **LOW** set high and low Arnold sampling settings for final and preview renders.
* **RENDER SHOT** — generating of .ass files for each shot starting from frame [101]
* **PUB** — publish to FTrack path to EXR render of current shot.

### Toolset for 2D branch
In Nuke all DNA tools located in DNA menu.

#### Shot Assembler NK
Creates nuke script for the shot, noticed in REEL, ESQ, SHOT fields after pressing ASSEMBLE button. Save nuke script with proper name to a proper folder. Add read node with exr file for this shot.

![](https://lh3.googleusercontent.com/-B3WAhI2EZ5Q/VyDQY1ayUFI/AAAAAAAAFeU/4iv-EtzC7oIORx9ld3HAbJaRoiY9MIdBACCo/s304/dnaNK_assembler_01.jpg)