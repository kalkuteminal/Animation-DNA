# Houdini to Animation DNA integration
Houdini root folder `<rootProject>/PROD/3D`, same as Maya project root.  

Houdini quick tips:  
[Environment](#environment-setup)  | [ATTR](#attributes-and-variables) | [Dynamic](#dynamic) | [Rendering](#rendering) | [VEX](#vex)

# Houdini drafts
## Environment setup
`$JOB` - root for Houdini project.  
`$HIP` - path where Houdini scene is.

## Attributes and variables

## Dynamic
### DOP Fluids
[Add source](#add-source) > [add DOP sim](#add-fluid-simulation) > [add output](#add-output)

#### Add source 
In OBJ root create source — **Geometry** node as an emitter for the fluid simulation:
- Create geometry
- Add **Fluid Source** and **Null** (OUT_EMMITER) nodes at the end of the flow.  
- **Fluid Source**: Scalar Volume > SDF From Geo > Out Feather Length > decrease for less blur

#### Add fluid simulation
  
In OBJ root create **DOP Network** node, dive in.  
Create **Pyro Solver**, **Smoke Object** (fluid container), **Resize Container**, **Source Volume** (import SOP volume data). Connect:  
- **Smoke Object** >> **Pyro Solver** `[1]`
- **Resize Container** >> **Pyro Solver** `[2]`
- **Source Volume** >> **Pyro Solver** `[5]`

Create microsolver (e.g. **Gas Turbulence**), connect to **Pyro Solver** `[3]`  (combine them with **Merge** if more than one)  
Create forces, put them after **Pyro Solver**

Alternative import source: in **Smoke Object** > Initial Data > `*` SOP Path  
Alternative resize: create **Gas Resize Fluid Dynamic** microsolver, connect to **Pyro Solver** `[2]`. Set Bounds > Tracking Object (create **Bound** node after geometry nodes in simulatuion source, set Upper and Lower bounds, e.g.`0.1` ).

**Gas Disturbance** — small size noise, combine 3 solvers with `[0.3] [0.1] [0.03]` values.  
**Gas Turbulence** — big size noise.  
**Gas Dissipate** — fading of fluid
  
Modify nodes parameters in **DOP Network** node:
- **Source volume**:
  - initialize > switch Source Fluid and back to Source Smoke
  - Volume Path > set path to source (OUT_EMMITER)
  - Masks > Velocity Volumes > set to `density`, to limit vel field from source
- **Smoke Object**: Division > decrease for higher resolution  
- **Resize Container**: Padding > decrease to be faster

#### Add output
In OBJ root create output – **Geometry** node to write/read cache and use for rendering or export:
- Create **Geometry** node, dive in.
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

## VEX