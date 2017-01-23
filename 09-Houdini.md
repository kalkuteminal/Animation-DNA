# Houdini to Animation DNA integration
Houdini root folder `<rootProject>/PROD/3D`, same as Maya project root.  
`Add = create`

[Dynamic](#dynamic) | [Rendering](#rendering)

# Houdini drafts
## Environment setup
`$JOB` - root for Houdini project.  
`$HIP` - root for Houdini scenes.

## Dynamic
### DOP Fluids
[Add source](#add-source) > [add DOP sim](#add-fluid-simulation) > [add output](#add-output)

#### Add source 
In OBJ root create source emitter for the fluid simulation — **Geometry** node with any data (geo or fluid). Add **Fluid Source** and **Null** (OUT_EMMITER) nodes at the end of the flow.  
Modify **Fluid Source**: Scalar Volume > SDF From Geo > Out Feather Length (decrease for less blur)

#### Add fluid simulation
  
Create fluid container with shelf: Fluid container > Smoke Container  
Modify nodes parameters in **DOP Network** node:
- **Source volume**:
  - initialize > switch Source Fluid and back to Source Smoke
  - Volume Path > set path to source (OUT_EMMITER)
- **Smoke Object**: > set Division size (fluid resolution, decrease for higher resolution)  

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
### OUT context
In OUT Context create Mantra Node
In Mantra:
- Candidate objects: del `*` to render nothing
- Objects > Force Objects: set name of Node to render

### SHOP context
