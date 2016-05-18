![](https://lh3.googleusercontent.com/-FVFx_K75buc/Vx-RusyFrVI/AAAAAAAAFcg/Tr9GQ-hGFX87JOZ8SvJH_04yA0uIkK3oACCo/s700/bannerDNA_glossary_01.jpg)

A. [Glossary of terms](#terms)  
B. [Glossary of codes](#codes)

## Terms
**Asset** – a set of digital data (files of different formats), required for the creation, management and visualization of real-world objects in the environment of a computer program Maya. Any visible object in the scene while rendering 3D scenes is asset. 

**Look development** – this is a separate technological process of creating material objects, carried out under the visualization step.

**shot** — is a part of a film between two cuts.

**story reel** — is a rough movie version in form of storyboard pictures with sound. 

**structuring** — dividing big amount of data into smaller pieces according to a particular model.

## Codes
**`<codePart>`** — name of film overall division (REEL_01, TEASER etc)  
**`<codeSequence>`** — 3 digits number of episode in film (010)  
**`<codeShot>`** — number of shot in each sequence (010). Used with `SHOT_` or `S` prefixes  
**`<codeRSS>`** — sub path `/<codePart>/<codeSequence>/SHOT_<codeShot>/`   
**`<codeFX>`** — 3 capital letters code of FX (dragon fire - DRF)  
**`<assetName>`** — name of asset  
**`<assetCode>`** — short name of asset.  
**`<partName>`** — name of asset part (trunk, leaves etc)  
**`<letterNumber>`** — number of object in letter format (A, B, C etc)  
**`<assetCategory>`** — FLORA, UTENSILS  
**`<assetNestedCategorys>`** — structure of folders according to static assets structuring scheme  
**`<assetForm>`** — GEO or RIG for animated assets, GEOMETRY or STANDIN for static  
**`<property>`** — object characteristic: color (CLR), displacement (DSP) etc  
**`<rootProject>`**— project root folder  
**`<rootScenes>`** — root folder for Maya scenes in Maya project.  