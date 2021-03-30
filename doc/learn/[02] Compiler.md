# Compiler

# [2.1] Commands

**Documentation meanings**

- **data** : a command
- `<data>` : a required parameter, can be defined by position or by name, the order matter
- `-data` : an optional named parameter

**ngl linear syntax**

`nc path to command positional_paramvalue1 positional_paramvalue2 -named_param -named_param:value -parameterized_param<-type:cpp<17>> `

Nested parameterization is limited to one level.

## [2.1.1] Basics

- `nc entity add` : add a new entity
- `nc entity set` : set the current entity controlling nc
- `nc edge john:projects:cpp /home/template/cpp` : create link between a path from the john entity graph to a local filesystem path
- `nc project update ngc::movie`
- nc set ncc ngl.neuroshok.com/cluster/ncc

## [2.1.2] Project

- `nc project `
    - **add** : add a new project
        - `<name>` `string` : project name
        - `-nvs` `bool = true` : enable nvs
    - `nc project cluster `
        - **update** : resolve dependancies

## [2.1.3] Cluster

- `nc cluster `
    - **add** : add a concept or cluster to the default ngl cluster(ncc)
    - **search** : 
    - **meta** : fiability quality 
    - **version**
    

## [3.1.1] Concretization process

**Initial state**
- Entity : **nc** (the ngl compiler)
- Concrete data : the source code

**Concretization**
- read ngl.ngl (the self description of ngl)
- process the ngl.ngl description
    -  read the ngl:shape description
    - ...
- read the user source code
- create the ngl program graph (source code internal representation)
- process the meta code
- concretize the program graph using the specified concretizer