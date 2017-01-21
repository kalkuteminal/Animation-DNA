# Houdini to Animation DNA integration

### Fluid smoke
Add fluid: Fluid container > Smoke Container  
Add emitter: add geo node > in > add Fluid Source > Container settings > initialize  
DOP network:
- create Source Volume > connect to LAST in of smokesolver > initialize
- set Division Size (resolution of fluid continer) in Smoke node

