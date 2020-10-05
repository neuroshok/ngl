# Getting started

## [1.1] Installation

Download **nc** (the ngl compiler) [here](http://ngl.neuroshok.com/concrete/nc.exe)

### [1.1.1] Configuration

**nc** require some configuration for advanced use of ngl, check the [list of nc commands](compiler/commands.md) for more informations

## [1.2] Basics

**nc** can be used in two modes. The linear mode to launch commands using the ngl linear syntax or in interactive mode by running **nc** without parameters.

All ecosystem elements will be handled by **nc** (build system, tests, docs, vcs, etc...)

### [1.2.1] Create a new project

`$ nc project add hello_world`

*output*
```
hello_world/
 - concept/ // project source code
    - program.ngl // the main file containging the entry point of the program

 - ngl.ngl // description of ngl itself
 - project.ngl // description of the project
``` 

Of couse the project templates can be customized.

*content of program.ngl*
```
ngc:program
{
    ngc:print<[Hello world !]>
}
```

### [1.2.2] Build a project

`$ nc project build hello_world`

The output will depend on the project parameterization

*build output*
```
hello_world/
 - concrete/
    - build/
       - hello_world.exe
 - concept/ // project source code
    - program.ngl // the main file containging the entry point of the program

 - ngl.ngl // description of ngl itself
 - project.ngl // description of the project
``` 

### [1.2.3] Run the project

`$ nc project run hello_world`

*output*
`Hello world !`