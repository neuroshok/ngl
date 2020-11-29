# Modularity

## [13.1] Cluster

A cluster is a part of the program entity 

## [13.1.1] Concept cluster

A ngl:cluster<concept> is an external cluster containing source code that will be part of the ngl entity.

```
// program entity
ngl:cluster main

ngl:concept:movie // use movie from the ngl:cluster:concept named ncc
// all concepts from ncc are available in ngl:concept
```

## [13.1.2] Entity cluster

A ngl:cluster<entity> is a cluster that describe an entity who can only be used by other entities. It cannot exist alone in the ngl:environment.

```ngl
// network.ngl
ngl:cluster main

ngl:cluster<entity> network
{
    ngl:concept connection
    {
        // ...
    }
}

ngl:concept packet
{
}

// export internal concept via the ngl entity to the entity cluster network
ngl:edge<ngl, ngc:packet, ngl:cluster<entity>:network, nge::export>
// sugar: ngc:packet -> ngu:network


// program.ngl
ngl:cluster main

ngl:edge<ngl, main, ngl:entity:cluster:beta, nge:import>    // import in main cluster
ngl:edge<ads, ngl, ngl:entity:cluster:beta, nge:import>     // import globally

```

## [13.1.3] Xeno cluster

A ngl:cluster<xeno> is a cluster that contains only foreign descriptions.

```
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

// using alias
ngl:cluster:sfml:init
ngl:alias<ngl:cluster:sfml, sfml>
sfml:init<params>
```