# Houdini to Animation DNA integration
Houdini root folder `<rootProject>/PROD/3D`, same as Maya project root.
`Add = create`

[DOP](#dop) | [Rendering](#rendering)

# Houdini drafts
## Environment setup
`$JOB` - root for Houdini project.  
`$HIP` - root for Houdini scenes.

## DOP
### DOP workflow
[Add source](#add-source) > [add DOP sim](#add-dop-sim) > [add output](#add-output)

#### Add source 
Source — Geometry nodet with any data (geo or fluid)

#### Add DOP sim
DOP Network node
Fluid smoke sim
**Add fluid**: Fluid container > Smoke Container  
**Add emitter**:
- add geo node > in > add Fluid Source
- Container settings > initialize
- Settings > lower Division size (fluid resolution) 
- SDF From Geometry > lower Out Feather Length  

**DOP network**:
- add Source Volume > connect smokesolver-[5] > initialize
- Source Volume > Scale Source Volume (density)
- set Division Size (resolution of fluid container) in Smoke node
- Resize Container > Padding > decrease to be faster
- add Gas Turbulence + Gas Dissipate + Merge > connect to smokesolver-[3]

### Add output
Output – geometry node

- Add Geo node
- Add DOP I/O node, set:
  - Set Geometry File
  - DOP Network — DOP sim node
  - DOP Node — Smoke node
  - Fields – eg. density, vel, etc

## Rendering
In OUT Context create Mantra Node
In Mantra:
- Candidate objects: del `*` to render nothing
- Objects > Force Objects: set name of Node to render
