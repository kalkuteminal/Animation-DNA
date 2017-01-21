# Houdini to Animation DNA integration
Houdini root folder `<rootProject>/PROD/4D`

# Houdini drafts
## DOPs
### Fluid smoke
**Add fluid**: Fluid container > Smoke Container  
**Add emitter**:
- add geo node > in > add Fluid Source
- Container settings > initialize
- Settings > lower Division size (fluid resolution) 
- SDF From Geometry > lower Out Feather Length  

**DOP network**:
- add Source Volume > connect to LAST in of smokesolver > initialize
- Source Volume > Scale Source Volume (density)
- set Division Size (resolution of fluid container) in Smoke node
- Resize Container > Padding > decrease to be faster

