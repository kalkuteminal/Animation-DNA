# Houdini to Animation DNA integration

### Fluid smoke
Create fluid: `Fluid container > Smoke Container`  
Add emitter: `create geo node > in > create Fluid Source > Container settings > initialize`  
DOP network: `create Source Volume > connect to LAST in of smokesolver > initialize `

