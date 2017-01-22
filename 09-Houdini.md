# Houdini to Animation DNA integration
Houdini root folder `<rootProject>/PROD/4D`

# Houdini drafts
## Environment setup
`$JOB` - root for Houdini project.  
`$HIP` - root for Houdini scenes.

## DOPs
### Fluid smoke
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

