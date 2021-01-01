# Build system

## [10.1] Phase

The phase represent the program state when an entity is processing something related to the program concept

ngl:phase:build, program is in build state when the build system is processing the project concept
ngl:phase:compile:execution, program is in compilation state when the compiler is executing a program concept code
ngl:phase:alive:execution, program is alive when the jit is executing a program concept code

```
ngl:phase build
{
    ngl:phase begin
    ngl:phase processing
    ngl:phase end
}
```

## [10.2] Project

```
ngl:ecosystem project
{
    ngc:string <name>
    ngc:location<filesystem> = [./]
    ngc:string version
    
    ngc:compiler
    {
        ngc:string <<name>> // may be set by an external entity, nc here
        .option [-w1 -w2] 
        .standard [cpp17]
    }
    
    ngc concrete // resources
    ngc concept // source code
    ngc cluster // external source
    ngc doc
    ngc example
    ngc tests
    
    ngl:phase:configuration<project>
    ngl:phase:concretization // compilation
    ngl:phase:deployment
    ngl:phase:installation

    ngc::configuration config
    
}
```

### Example

### Raz

`nc project config -link_type:static` // optional, default tpo static

`nc [test install] raz`
`nc [install run] raz:example:[demo1 demo2]`

```

ngl:ecosystem:project raz
{
    .name [RaZ]

    .config: [release] //
    
    .option
    {
        link_type [static]
    }

    .compiler // require parameterization, later
    {
        .standard [cpp17]
        (.option ++ [ -DNOMINMAX])
    }
    
    .concept // use a specific shape
    {
        include/RaZ/*
        source/RaZ/*
    }
    
    .concrete // use a specific shape
    {
        assets
        shaders
    }
    
    .cluster // clusters (projects, concept clusters) required by this project
    {
        npc:catch<config: release> // ngl project cluster
        npc:imgui
    }
       
    ngc:cluster_entity raz_cluster
    {
        .name [razlib]
        .link_type option:link_type
    }
    
    ngc:project examples // subproject
    {
        .cluster raz_cluster // all examples require raz_cluster
        ngc:program fulldemo
    }

    ngc:install
    {
        .location "c:/raz"
    }
}

// parameterization
raz<compiler.name: [gcc]>
{
    (compiler.option ++ [ -DRAZ_COMPILER_GCC=ON]) // add sugar
    (compiler.option ++ [ -pedantic])
    ngl:branch<compiler.version>
    {
        (>= 6) (compiler.option ++ [-Wnull-dereference])
        (>= 7) (compiler.option ++ [-Waligned-new])
    }
}


raz<option: option.libpng>
{
    .cluster npc:libpng
}

// debug_info identifier is described as a concrete data using the markdown shape with $ as a delimiter
ngs<markdown> debug_info
{
    ############ raz debug
    *host system* : $ ngl:environment:host_name $
}
// nc raz print debug_info

```