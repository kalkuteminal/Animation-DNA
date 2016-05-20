![](https://lh3.googleusercontent.com/-yzn5MCjzPaw/Vx9l-bmf1UI/AAAAAAAAFbU/3Lo9EKx7_wMVh3221gDBIKtIlndEgOvbACCo/s700/bannerDNA_home_01.jpg)

## What is Animation DNA?
**Animation DNA** is an example project for **Maya > Arnold > Nuke pipeline** which could be used as template for any full CG task — from a single shot to a whole 3D animation feature film.  
In other words, **Animation DNA is out of the box pipeline** for animation studio (or for a single person).  **Animation DNA** is a starting point which defines main and most important pipeline actions and could be easily refined according to requirements of a particular project.

The **core** of Animation DNA is a **database** — it contains all information you need to create and manage film production. There are two types of database could be used with Animation DNA:
- simple text file in [JSON](http://www.jsoneditoronline.org/) format 
- complex project management system [FTrack](https://www.ftrack.com/). 

Public version of Animation DNA works on JSON database. FTrack is more usable for a bigger projects, can operate more quantity of logical data pieces and store more information about production actions. Documentation is relevant for both types of database.

## How to use Animation DNA?

**The workflow**: 
- Extract [DNA.rar](02-codex-dna#dna-archive) to a folder with projects, rename root to a project name. 
- [Setup database](02-Codex-DNA#management-with-ftrack).
- [Make shots](02-Codex-DNA#shot-creation-workflow)

As an option, you can use some of Animation DNA tools exclusively, without linking to the whole pipeline system. For example, [Asset Manger](03-tools#asset-manager) and [Render Manager](03-tools#render-manager) has many functions, useful if you rendering with Arnold. In this case just put [Animation DNA](https://github.com/kiryha/AnimationDNA) scripts into Maya scripts folder and [run Maya with wrpapper](02-codex-dna#running-maya-and-nuke-with-wrappers)

Click on image below to watch shot creation workflow presentation
[![](https://lh3.googleusercontent.com/-JQbm7zDgwDA/Vz2dDBZ0WKI/AAAAAAAAFoA/oD8VObnJtk07LKekIYh9JGyf0t4VL2LEwCCo/s700/DNA_mov_shotProd_02.jpg](https://www.youtube.com/watch?v=LOm3bAo80KI)]

## Animation DNA documentation
[This wiki](https://github.com/kiryha/AnimationDNA/wiki) is Animation DNA documentation. It consists from three main parts:
* [Quick start tutorial](01-Quick-start) — easy way to get in
* [Codex DNA](02-Codex-DNA) — full description of pipeline
* [Animation DNA tools](03-Tools) — specification of pipeline tools

To understand principles of Animation DNA pipeline you need to reed [Codex DNA](https://github.com/kiryha/AnimationDNA/wiki/02-Codex-DNA) which define terms, describe overall pipeline logic and has particular instructions for each stage of production.

On the right side of wiki you can find full Animation DNA documentation table of contents.