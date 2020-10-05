# Modularity

## [13.1] Cluster

## [13.1.1] Concept cluster

cluster is part of the program entity 

```cpp
// program entity
ngl:cluster main

ngl:concept:movie // use movie from the ngl:cluster:concept named ncc
// all concepts from ncc are available in ngl:concept
```

## [13.1.2] Entity cluster



## [13.1.3] Xeno cluster

A ngl:cluster<xeno> is a cluster that contains only foreign descriptions.

examples

// sfml.ngl (xeno cluster)
ngl:cluster<xeno> sfml
{
    ngl:xeno:function<"init", some, params> init
    ngl:xeno:function<"cleanup", some, thing, to, give, as, params> cleanup
    ngl:xeno:function<"wait"> wait

    ngl:xeno:function<"custom", a, b, c> init
}

// program.ngl
ngl:cluster main

ngl:edge<ngl, main, ngl:cluster:sfml, nge:import>    // import in main cluster
ngl:edge<ngl, ngl, ngl:cluster:sfml, nge:import>     // import globally

ngl:cluster:sfml:init
ngl:arc<ngl, ngl:cluster:sfml, sfml>
sfml:init<params>