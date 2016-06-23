![](https://lh3.googleusercontent.com/-FVFx_K75buc/Vx-RusyFrVI/AAAAAAAAFcg/Tr9GQ-hGFX87JOZ8SvJH_04yA0uIkK3oACCo/s700/bannerDNA_glossary_01.jpg)

A. [Glossary of terms](#terms)  
B. [Glossary of codes](#codes)

## Terms
**Asset** – a set of digital data (files of different formats), required for the creation, management and visualization of real-world objects in the environment of a computer program Maya. Any visible object in the scene while rendering 3D scenes is asset. 

**Editing** — is the art, technique and practice of assembling shots into a coherent sequence.

**Grading** — is a process of changing color of a motion picture (film) for enhancing and adopting to a cinema scree

**Look development** –  is a process which define physical behavior of surfaces and volumetric in conjunction with lighting. The result of look development process is materials and lights.

**Material** — Surface property which define light reacting characteristics. Common materials are: wood, metal, carpaint, wax, skin etc.

**Pipeline** — is project organisation and execution system

**Progressive workflow** — is a method of step by step project execution when your get the rough form of the end step as soon as it possible and than refine stages which are most valuable in overall result according to resources your have. 

**Rendering** — is a conversion of vector data to a raster images.  

**Rendering layer** — rendered part of the shot (character, background, FX etc)

**Publishing** — is a process of recording necessary data to FTrack database with a help of [Animation DNA tools](03-Tools) using [FTrack Python API](http://ftrack.rtd.ftrack.com/en/3.3.1/developing/index.html)

**Shader** — Mathematical realization of surface material in particular rendering engine. 

**Shot** — is a part of a film between two cuts.

**Story reel** — is a rough movie version in form of storyboard pictures with sound. 

**Structuring** — dividing big amount of data into smaller pieces according to a particular model.

**Variation** — slight modification of the same asset. 

**Version** — digital number of file.

## Codes
**`<###>`** — 3 digits version  
**`<codePart>`** — name of film overall division (REEL_01, TEASER, MASTER-whole movie, etc)  
**`<codeSequence>`** — 3 digits number of episode in film (010)  
**`<codeShot>`** — number of shot in each sequence (010). Used with `SHOT_` or `S` prefixes  
**`<codeRSS>`** — sub path `/<codePart>/<codeSequence>/SHOT_<codeShot>/`   
**`<codeFX>`** — 3 capital letter short name of FX (dragon fire - DRF)  
**`<codePass>`** — 3 capital letter short name of compositing pass (depth = DPT)  
**`<codeLayer>`** — 3 capital letter short name of rendering layer (background, character etc)  
**`<assetName>`** — name of asset  
**`<assetCode>`** — short name of asset.  
**`<partName>`** — name of asset part (trunk, leaves etc)  
**`<letterNumber>`** — number of object in letter format (A, B, C etc)  
**`<assetCategory>`** — class of object according to classification system (FLORA, UTENSILS etc)  
**`<assetNestedCategorys>`** — structure of folders according to classification system  
**`<assetForm>`** — GEO or RIG for animated assets, GEOMETRY or STANDIN for static  
**`<property>`** — object characteristic: color (CLR), displacement (DSP) etc  
**`<rootProject>`**— project root folder  
**`<rootScenes>`** — root folder for Maya scenes in Maya project.  